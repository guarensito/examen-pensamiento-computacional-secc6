# examen-pensamiento-computacional-secc6
Documentación de mi proceso para el examen.

##Links
- P5.js:
- Github:

##¿Qué voy a hacer en este proyecto? Explicación
En mi solemne 2 hice un sistema inspirado en el Op Art y un poco del Diseño Interactivo, donde habían cuatro cuadrantes de líneas verticales que se movían dependiendo en que dirección se posicionaba el mouse, ahí variaba el movimiento de las líneas y el grosor. 
Quise mantener mi código de la segunda solemne para mejorarlo y agregarle el contenido visto en esta última unidad.

Este proyecto va a tratar de tres estados: pantalla de inicio, pantalla de la experiencia y pantalla de despedida, con un estado que será apretar la tecla "enter" para ver la interactividad. El contenido multimedia que usaré será el sonido.

El concepto es una discoteca, aprovechando que en mi segunda solemne da esa vibra, quise potenciarla. En la pantalla de inicio será la entrada a la discoteca, cuando se haga click en la tecla "enter" las luces se empezarán a mover y con un click se va a reproducir una canción. Cuando esta termine, tendrás que hacer click para llegar a la pantalla final que será la salida de la discoteca.

Usaré recursos vistos en las unidades anteriores.

# Documentación del proceso (imágenes y códigos)

- **Dibujo del fondo** El dibujo lo hice en Illustrator para saber como ubicar cada figura en XY. Para dibujarlo en p5.js decidí hacerlo en function draw, ya que es simplemente un dibujo, no será una variable global.
  (aca imagen del dibujo en illustrator y final

 Empecé con la forma del edificio, para empezar a ubicar las otras figuras.

 ```function setup() {
  createCanvas(800, 500);
}

function draw() {
  background(19, 31, 51); 

  fill(10, 13, 14);
  noStroke();
  rect(110, 100, 580, 300);
```
  (Imagen p1)

  Luego continúo con los detalles interiores del edificio principal.

 ``` fill(200, 50, 255);
  noStroke();
  rect(250, 150, 300, 40);

  textSize(22);
  fill(0);
  text("Discoteca", 320, 177);

  textSize(30);
  fill(255);
  text("GYAL", 430, 178);

  fill(210, 40, 240);
  stroke(255);
  rect(330, 240, 140, 120);

  fill(170, 255, 0);
  noStroke();
  rect(215, 240, 35, 120);

  rect(550, 240, 35, 120);

  fill(80, 230, 200);
  noStroke();
  rect(140, 240, 35, 120);

  rect(625, 240, 35, 120)
```
imagen p2

Ya luego terminé con los detalles exteriores, como las personas que vendrían siendo los rectángulos grises y la vereda junto a la calle.

  ```fill(120);
  noStroke();
  rect(40, 329, 25, 70);
  rect(70, 329, 25, 70);
  rect(100, 329, 25, 70);
  rect(130, 329, 25, 70);
  rect(676, 329, 25, 70);
  rect(705, 329, 25, 70);

  fill(35);
  noStroke();
  rect(0, 390, 800, 10);

  fill(10);
  noStroke();
  rect(0, 400, 800, 100);

  fill(200);
  noStroke();
  rect(10, 450, 90, 12);
  rect(230, 450, 90, 12);
  rect(450, 450, 90, 12);
  rect(670, 450, 90, 12);
}
```

Ya con eso listo, pasamos a los demás códigos. Los voy a separar por partes: códigos para los Estados, códigos para el sonido, y iré explicando cuales fueron los nuevos códigos que agregué.

Antes de empezar, establecí estas variables globales
```let estado = 0;

let cantidadLineas = 300;
let variacion = 5;

let grosorLinea = 2; 

let sonido;
```
Los nuevos que agregué fueron: **let estado**, **let grosorLinea** y **let sonido**. El primero es para crear las pantallas de la experiencia, si mi estado vale 0, el programa va a mostrar la pantalla con el dibujo de la discoteca. Si vale 1 el programa va a cambiar a la pantalla de la experiencia y si vale 2, el programa va a cambiar y mostrar el dibujo de la discoteca pero de día. 

Let grosorLinea sirve para guardar y actualizar dinámicamente el grosor que van a tener las líneas en la pantalla según el movimiento del mouse. 

Y let sonido es una variable vacía que sirve como una especie de contenedor para guardar el audio que elija.

- **Códigos para los Estados** 
