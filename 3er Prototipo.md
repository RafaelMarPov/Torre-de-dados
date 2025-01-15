# Proceso de creación del tercer prototipo
- Para el diseño final se necesita de un servo de giro continuo, por lo que sopesamos dos opciones: comprar servos 360, que saldían más caros o tranformar uno de 180 en uno de giro continuo. Finalmente decimimos que la segunda opción era la más adecuada y buscamos tutoriales para ello. El tutorial que segimos fue el sigiente:
  - [Tutorial](https://www.youtube.com/watch?v=BROlS2q4Spw)
  - [Codigo en Arduino](https://www.dropbox.com/scl/fi/75v022f0498o1ly5mlh1v/control_giro_360.ino?rlkey=givfcjaj6mc72fz464msb5vou&e=1&dl=0)
  
![Servo hakeado](https://github.com/user-attachments/assets/d61c8d45-3d48-4191-8b92-471ca02955a1)
- Para el tercer prototip buscabamos algo plenamente funcional pero nos encontramos con varios obstaculos que ponian en rieso la viabilidad del proyecto.
  - El tiemplo inverido era exesivo y a punto de terminat el 1er trimestre habiamos avanzado realmente poco.
  - Las tres propuestas de diseños presentaban muchas dificultades. El sistema de engranajes necesario paro un mavimiento rectilinio era demasiado complejo. La plataforma giratoria era muy poco fiable por la inexactitud de      las simulaciones en tinkercd, que hacian muy dificil pensar en el modelo aplicado a la realidad. El proyecto de aspas giratotias también fracasó, entre otras por que el seervo requerido de 360 era dificil de otener y        poco eficiente ya que se descalibraba.
  - El sitema de recoleccion de dados aun era una incognita que no nos habiamos parado a abordar pero suponiamos que su implemantación no seria sencilla.
- En busca de soluciones decartamos todos las ideas anteriores excepto una, la plataforma giratoria. Una nueva versión de esta prometía mejores resultado y bastante más fiables, empleando un servo 180 mucho mas práctico. Se   retocaron los últimos aspectos y pasamos a imprimirla.
- Como alternativa se pensó en un nuevo diseño, similar al anteriores propuestas, una plataforma en forma de V en posicion vertical que recoje los dados y los deja caer con un mevimiento de servo de 90 grados. Se puede aplicar como un movimiento bidireccional que deje caer dos dados en sentidos opuestos o unidirccional, que deje caer un solo dado. 
- Con la plataforma giratoria imprimiendose y la V también lista para imprimir, pasamos al reconocimiento de voz.
- La plataforma fue un éxio, salvo pr el d4, pero se solucionaria rapidamente con un pequeño cambio en el modelo. El problema actual era el tamaño qur iba a tener la torre.
- Los cabios en la plataforma fueron mejores de lo planeado. Se aplicó, ingeniosamente, un método de intercambio de salidas; permitiendo probar multitud de tamaños distints sin tener que imprimir toda la estructura cada vez. Por fin los d4 estaban bajo conrtol y con un una tasa de éxito bastante elevada. 
