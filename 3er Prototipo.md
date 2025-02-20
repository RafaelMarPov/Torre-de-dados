# Proceso de creación del tercer prototipo

### En busca el diseño final

Para el tercer prototipo se proponen varias ideas que solventen el problema actual con los d4 (Diseñado en tinkercad):

- Un sistema de engranajes que transforma el mavimiento circular del servo en rectilínio. Con este movimiento se desplazarán un conjunto de plataformas que permiten la dispensión de un dado mientras se mantiene el siguiente arriba.
- Una plataforma circular gira bajo el tubo de almacenamiento. Esta plataforma cuenta con un agujero que permite la entada de un solo dado y que evita la de los siguientes.
- Un tubo de almacenamiento que dispensa los dados directamente sobre una plataforma con cuato espacios que gira en el eje y. La rueda con forma de sumando dispensa los dados de uno en uno, impidiendo la salida del resto debido a su diseño. Para el d4 se aplica un modelo especial de rueda con una forma más... peculiar. Esta rueda presenta extensiones en paralelo a la plataforma original que funcionan como ganchos y como tapa con tal de contolar la caida de los dados.

- Para el diseño final se necesita de un servo de giro continuo, por lo que sopesamos dos opciones: comprar servos 360, que saldían más caros o tranformar uno de 180 en uno de giro continuo. Finalmente decimimos que la segunda opción era la más adecuada y buscamos tutoriales para ello. El tutorial que segimos fue el sigiente:
  - [Tutorial](https://www.youtube.com/watch?v=BROlS2q4Spw)
  - [Codigo en Arduino](https://www.dropbox.com/scl/fi/75v022f0498o1ly5mlh1v/control_giro_360.ino?rlkey=givfcjaj6mc72fz464msb5vou&e=1&dl=0)
<details>

![Servo hakeado](https://github.com/user-attachments/assets/d61c8d45-3d48-4191-8b92-471ca02955a1)
<summary>
  
 ### Foto del servo
</summary>
</details>

### Problemas
- Para el tercer prototipo buscábamos algo plenamente funcional pero nos encontramos con varios obstáculos que ponáan en rieso la viabilidad del proyecto.
  - El tiempo inverido era exesivo y a punto de terminat el 1er trimestre habiamos avanzado realmente poco.
  - Las tres propuestas de diseños presentaban muchas dificultades. El sistema de engranajes necesario paro un mavimiento rectilinio era demasiado complejo. La plataforma giratoria era muy poco fiable por la inexactitud de las simulaciones en tinkercd, que hacian muy dificil pensar en el modelo aplicado a la realidad. El proyecto de aspas giratotias también fracasó, entre otras cosas, porque el servo requerido de 360 era dificil de otener y poco eficiente ya que se descalibraba.
  - El sitema de recolección de dados aun era una incognita que no nos habiamos parado a abordar pero suponiamos que su implemantación no seria sencilla.
 
### Final del 3<sup>er</sup> prototipo
- En busca de soluciones decartamos todos las ideas anteriores excepto una, la plataforma giratoria. Una nueva versión de esta prometía mejores resultados y bastante más fiables, empleando un servo 180 mucho más práctico. 
- Aunque el tercer prototipo no llegó a nada pero pero allanó el camio para un prometedor cuanto diseño.
