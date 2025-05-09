# Proceso de creación del cuarto prototipo

## El Fin se Acerca
- Tras los mecanismos descartados durante el anterior prototipo, para este solo nos quedaba lo mejor. La plataforma giratoria
  daba muy buenos resultados. Para el d4 se implantó ingeniosamente un sistema de intercambio de entrada para que se ajustara
  a este dado y poder probar varios tamaños sin necesidad de imprimir de nuevo cada base.
- Este parecía el pototipo final, el paso que más nos acercaba al final del proyecto, pero aun faltaba por hacer varias cosas.

## El Código 
- El codigo causó algun problema, debido al la complejidad de lo requerido (siete botones conectados a siete servos, contar la cantidad de veces que se ha pulsado cada botón y mover el servo correspodiente dicha cantidad; ademas de el limitado numero de pines) pero con un poco de ayuda externa y paciencia se consuguió un código al menos funcional en una simulación de Tinkercad.
## El Modelado
- La iea del modelo era la sigiente: una torre de cuya puerta asomaba un dragón que dejaría caer los dados por su boca. En la cima de la torre las alcmenas funcionaban como recipiente para los dados que caían hasta el dragón. Desde la parte superior también bajaba una escalera de caracol en caso que que quisieses tirar los dados con normalidad y estos caerían desde una ventana. La aplicación de todo esto en un modelo real ocasionó algunos problemas.
> Complicaciones:
>- El modelado fue un dolor de cabeza, ajustar las medidas para que quedadse estético y que todos los macanismos funcionasen correctamente fue una tarea tediosa y compicada.
>- Además estaba siendo modelado en Blender, que aunque presenteba muchas más opciones que Tinkercad era mucho menos intuitivo.
>- A esto se le suma la falta de conocimientos sobre el programa, por mucho que poco a poco las cosas fueran saliendo más fluidas,los errores inesperado y aparentemente inexplicables seguían apareciendo.
>- Cuando se intentó exportar el modelo a Tinkercad para probar su sistema de físias en la caida de los dados, el modelo se corrompía totalmente y presentaba errores por todas partes, haciendo implosible esta prueba de físicas.
>- La escalera debia ser una espiral y estar modelada de la forma correcta para que los dados bajasen de la mejor forma posible. Mediante la documentación se logró crear una escalera totalmente funcional.

## El Reconocimiento de Voz
  En la recta final empezamos con el reconocimiento de voz. Nuestra primera opción eran los modulos que abarcasen esta función. Tras una larga investigación y con la ayuda de IAs se concluyó que estos modulos no
  eran adecuados para el proyecto. La segunda opcion eran los programas "speech to text" que transformaban la voz en texto que podriamos implementar en el código. Despues de investigar más decidimos usar el programa
  Whisper, ya que, a diferencia de otros, era gratuito e ilimitado; no requería tarjeta y operaba de forma offline. Por distintos motivos se descartaron este y nuestra otra opción de usar Google assistant para usar, de forma definitiva, Appp inventor
<details>
<summary>
  
  ### Instalación de Whisper (no usado)
  
</summary>

- Para instalar Whisper y poder implementerlo con nuestro código de Arduino se necesitaban una serie de requisitos y seguir determinados pasos. Al principio nos centramos solo en istalarlo en el orenador para probar su     funcionamiento.
  - Primero se debía instalar Python en el PC,marcando la opcion "Add Python to PATH".
  - Luego se requería la instalación de Chocolatey mediante PowerShell. Esto se hacía abriendo PawerShell como administrador y ejecutando el siguiente comando:
  > Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object             System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
  - Ahora tocaba intalar FFmpeg, ecribiendo en PowerShell el comando:
  > choco install ffmpeg
  - Seguía la instalación de PyTorch, para lo que se necesitaba ir a [pytorch.org](https://pytorch.org/get-started/locally/) y seguir las instrucciones para instalar PyTorch según tu sistema operativo y tarjeta gráfica.
  - Finalmente puedes instalar Whisper. Abre una terminal (CMD o PowerShell) y ejecuta el siguiente comando:
  > pip install -U openai-whisper
  - Ya puedes usar Whisper para transcribir un archivo de audio, usa el siguiente comando:
  > whisper audio_file_name --model medium
- Si prefieres una guía visual, puedes seguir este [video tutorial](https://www.youtube.com/watch?v=cgDO-JAhoHg) que explica el proceso paso a paso.
### Implementacion de Whisper
- Para omplementar Whisper el proyecto se requiere un intermediario ya que no se admite Arduino por sus limitaciones. Con Raspberry Pi es posible transcribir el mensaje de Whisper a Arduino.
</details>

<details>
<summary>
  
### Google Assistant (no usado)
</summary>

- **Paso 1:** Configurar Google Assistant
  - Instala Google Assistant en tu dispositivo móvil.
  - Configura tu cuenta de Google y asegúrate de que Google Assistant esté activado.

- **Paso 2:** Crear una cuenta en IFTTT
  - Regístrate en IFTTT (https://ifttt.com/) y crea una cuenta gratuita.
  - Conecta Google Assistant a IFTTT siguiendo las instrucciones en la plataforma.

- **Paso 3:** Configurar Arduino Uno
  - Conecta tu Arduino Uno a tu computadora y abre el IDE de Arduino.
  - Instala las librerías necesarias para conectar tu Arduino a internet, como WiFi101 o ESP8266WiFi, dependiendo del módulo -- que estés usando.
  - Escribe el código para controlar el servo y otros componentes. Aquí tienes un ejemplo básico para mover un servo:
  - Sube el código a tu Arduino Uno.

- **Paso 4:** Conectar Arduino a la nube
  - Configura una plataforma en la nube como Arduino IoT Cloud (https://create.arduino.cc/iot/).
  - Crea un nuevo dispositivo y selecciona tu Arduino Uno.
  - Configura las variables y el código necesario para enviar y recibir datos desde la nube.

- **Paso 5:** Crear applets en IFTTT
  - Crea un nuevo applet en IFTTT.
  - Selecciona Google Assistant como el disparador (If This).
  - Configura el comando de voz que deseas usar, por ejemplo, "Mueve el servo".
  - Selecciona Webhooks como la acción (Then That).
  - Configura la URL del webhook para enviar una solicitud HTTP a tu Arduino a través de la nube.

- **Paso 6:** Entrenar y probar
  - Prueba el comando de voz con Google Assistant.
  - Verifica que el Arduino reciba la solicitud y ejecute la acción correspondiente.
  </details> 

### App inentor + Módulo Bluetooth HC-05 (Implementación final)

- Se crea una sencilla aplicación en app inventor que reconozca voz y la pase a texto. Esta aplicación se conecta con bluetooth al módulo HC-05 y este al arduino, que recive las ordenes
  
