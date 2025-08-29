# Diseño final
## Desarroyo del Código
- Para el código final se buscaba que cumpliese las siguientes cuestiones:
   
   + Recibir el mensaje de App Invetor por Bluetooth.
   + Interpretar que tipo de dado se pide lanzar y cuantos.
   + Realizar dicha acción de lanzamiento.
   + Todo medinante el siguiente tipo de comando: Tira [numero] de [tipo] y [numero] de [tipo]...
   
- La primara parte es sencilla, conectas el módulo HC-05 al Arduino y lo programas. Aunque a nosotros nos costó calibrar el módulo y entender el modo AT.

- La interpretacion es el grueso del código. Conseguir que entendiese las palabras y las relacionase con los dados no fue fácil pero se consiguió de la siguiente manera:
  + El mensaje se graba en App Invenentor, se le añade un asterisco al final y se envía. Llaga al Arduino y es separado por espacios hasta el asterisco, que indica el fin del mensaje.
  + Las palabras se añaden a una lista y el codigo identifica los "de". La palabra de antes es la cantidad y la de después el tipo de dado.
  + Se convierten las palabras a números. "seis" ----> "6"
  + Se asigna el número de repeticiones a un bucle y el tipo al servo que contiene dicho dado.

- La parte final consite simplemente en que el servo adecuado realice el movimiento las veces necesarias.
<details>
<summary>
 
### Código final
</summary>

```
#include <SoftwareSerial.h>
#include <Servo.h>

SoftwareSerial BTSerial(10, 11);
String datosRecibidos = "";
String datosSeparados[20];
int contador = 0;

Servo servos[7];
int pinesServos[7] = {2, 3, 4, 5, 6, 7, 8};

// Mapeo de tipos de dado a índices de servos
struct Dado {
  String nombre;
  int indice;
};

Dado dados[] = {
  {"cuatro", 0}, {"seis", 1}, {"ocho", 2},
  {"diez", 3}, {"doce", 4}, {"veinte", 5}, {"cien", 6}
};

// Función para convertir palabras numéricas en números
int convertirPalabraANumero(String palabra) {
  if (palabra == "uno") return 1;
  else if (palabra == "dos") return 2;
  else if (palabra == "tres") return 3;
  else if (palabra == "cuatro") return 4;
  else if (palabra == "cinco") return 5;
  else if (palabra == "seis") return 6;
  else if (palabra == "siete") return 7;
  return -1; // Retorno -1 si el número no es válido
}

void setup() {
  Serial.begin(9600);
  BTSerial.begin(9600);
  Serial.print("\n");
  Serial.println("Dispositivo listo");

  for (int i = 0; i < 7; i++) {
    servos[i].attach(pinesServos[i]);
  }
}

void loop() {
  while (BTSerial.available()) {
    char caracter = (char)BTSerial.read();
    Serial.print("\n");
    Serial.print(caracter);
    if (caracter != '*') {
      datosRecibidos += caracter;
    } else {
      procesarDatos();
      datosRecibidos = "";
    }
  }
}

void procesarDatos() {
  contador = 0;

  while (datosRecibidos.length() > 0) {
    int indiceEspacio = datosRecibidos.indexOf(' ');
    if (indiceEspacio == -1) {
      datosSeparados[contador] = datosRecibidos;
      datosRecibidos = "";
    } else {
      datosSeparados[contador] = datosRecibidos.substring(0, indiceEspacio);
      datosRecibidos = datosRecibidos.substring(indiceEspacio + 1);
    }
    contador++;
  }

  for (int i = 0; i < contador; i++) {
    if (datosSeparados[i] == "de") {
      int numero = convertirPalabraANumero(datosSeparados[i - 1]);
      String tipoDado = datosSeparados[i + 1];
      int servoIndex = obtenerServoIndex(tipoDado);

      if (servoIndex != -1 && numero > 0 && numero <= 7) {
        moverServo(servoIndex, numero);
      } else {
        Serial.println("Comando no válido o número fuera de rango.");
      }
    }
  }
}

int obtenerServoIndex(String tipoDado) {
  for (int i = 0; i < 7; i++) {
    if (dados[i].nombre == tipoDado) {
      return dados[i].indice;
    }
  }
  return -1;
}

void moverServo(int servoIndex, int numero) {
  String nombreDado = dados[servoIndex].nombre; // Obtener el nombre del dado
  
  Serial.print("Moviendo el dado ");
  Serial.print(nombreDado);
  Serial.print(" ");
  Serial.print(numero);
  Serial.println(" veces.");

  for (int j = 0; j < numero; j++) {
    servos[servoIndex].write(90);
    delay(500);
    servos[servoIndex].write(0);
    delay(500);
  }
}


```
</details>

## Modelado
- Imprimiendose...
