# Diseño final
## Código
 Para el código final se buscaba que cumpliese las siguientes cuestiones:
  - Recibir el mensaje de App Invetor por Bluetooth.
  - Interpretar que tipo de dado se pide lanzar y cuantos.
  - Realizar dicha acción de lanzamiento.

La primara parte es sencilla, conectas el módulo HC-05 al Arduino y lo programas. Aunque a nosotros nos costó calibrar el módulo y entender el modo AT.

La interpretacion es el grueso del código. Conseguir que entendiese las palabras y las relacionase con los dados no fue fácil pero se consiguió de la siguiente manera:
  1. El mensaje se graba en App Invenentor, se le añade un asterisco al final y se envía. Llaga al Arduino y es separado por espacios hasta el asterisco, que indica el fin del mensaje.
  2. Las palabras se añaden a una lista y el codigo identifica los "de". La palabra de antes es la cantidad y la de después el tipo de dado.
  3. se convierten las palabras a números. "seis" ----> "6"
  4. Se asigna el número de repeticiones a un bucle y el tipo al servo que contiene dicho dado.

La parte final consite simplemente en que el servo adecuado realice el movimiento las veces necesarias.
