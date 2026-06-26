# Discoteca Gyal
Documentación de mi proceso para el examen.

**Autora:** Francisca Castro Martinez

**Descripción general:** Este es un sketch interactivo que simula la experiencia de entrar, vivir y salir de una discoteca. La persona que interactué controla la transición entre los tres estados mediante el mouse y el teclado, cada momento tiene su propia estética visual y sonora.

##Links
- P5.js pantalla fija: https://editor.p5js.org/francisca.castro3/full/L8aBG3Fr0
- Editable: https://editor.p5js.org/francisca.castro3/sketches/L8aBG3Fr0

## ¿Qué voy a hacer en este proyecto? Explicación
En mi segunda solemne desarrollé un sistema inspirado en el Op Art y, en parte, en el diseño interactivo: cuatro cuadrantes de líneas verticales que cambiaban de movimiento y grosor según la posición del mouse. Para este proyecto decidí mantener ese código como base y ampliarlo con el contenido visto en esta última unidad.

El proyecto se organiza en tres estados: una pantalla de inicio, una pantalla de experiencia y una pantalla de despedida.

El concepto central es una discoteca: dado que mi segunda solemne ya transmitía esa atmósfera, decidí potenciarla en este nuevo trabajo. La pantalla de inicio corresponde a la entrada de la discoteca; al hacer clic en la puerta, las líneas comienzan a moverse según el mouse y se reproduce una canción. Cuando esta termina, se debe presionar Enter para llegar a la pantalla final, que representa la salida de la discoteca.

A lo largo del proyecto utilicé recursos trabajados en unidades anteriores del curso.

# Documentación del proceso 
A continuación se documenta paso a paso el proceso de construcción del proyecto, incluyendo imágenes y fragmentos de código.

- **Variables globales** Estas variables están declaradas afuera de cualquier función para que cualquier parte de mi código pueda usarlas. 

```let estado = 0;

let cantidadLineas = 300;
let variacion = 5;

let grosorLinea = 2; 

let sonido;
```

Las nuevas variables agregadas son ```let estado``` , ```let grosorLinea``` y ```let sonido```.

**Primera función** Se ejecuta antes que cualquier otra parte del sketch, porque trabajo es esperar a que el archivo de audio termine de cargar antes de seguir. Si no se hiciera así, podría intentar reproducirse el audio sin que esté listo.

```
function preload(){
  sonido = loadSound("fiebre.mp3");
```
**Códigos para los estados** Acá se decide qué estado se debe mostrar en la pantalla según lo que esté pasando.

 ```if (estado === 0) {
    dibujarDiscotecaNoche();
  } else if (estado === 1) {
    // lógica interactiva
  } else if (estado === 2) {
    dibujarDiscotecaDia();
  }
}
```

**Primer estado** Esta parte solo se ejecuta cuando estado === 1, y también es la base de mi solemne 2.
```background(0);
grosorLinea = map(mouseY, 0, height, 0.5, 8);
strokeWeight(grosorLinea); ```

```map()``` toma la posición vertical del mouse (que va entre 0 y 500, el alto del canvas) y la transforma en un número más chico, entre 0.5 y 8. Ese número es el grosor que van a tener las líneas. Es decir, mientras más abajo esté el mouse, más gruesas se ven, y mientras más arriba, más finas.

##

**Bucle** Esto es para que no tenga que estar escribiendo código tras código. Es el mismo que usé en mi solemne 2, pero le cambié el ```cantidadLineas``` por ```width```, esto fue para que las líneas llegaran a cada esquina de mi lienzo.
```for (let i = 0; i <= width; i = i + 10) {
  dibujarLinea(i);
}
```
**Funciones de los dibujos** Para que el código no fuera un desorden, separé el dibujo de cada pantalla en funciones propias. Tenemos ```dibujoDiscotecaNoche``` y ```dibujoDiscotecaDia```

 El dibujo de la discoteca de noche lo realicé primero en Illustrator, para definir con precisión la posición (X, Y) de cada figura antes de pasarlo a p5.js. Como se trataba únicamente de un dibujo estático, decidí construirlo directamente dentro de draw(), sin necesidad de variables globales.
  (aca imagen del dibujo en illustrator y final

 Empecé con la forma del edificio, para empezar a ubicar las otras figuras.

 ```background(19, 31, 51); 

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

```fill(255);
    noStroke();
    textAlign(CENTER);
    textSize(14);
    text("Presiona ENTER para salir de la discoteca", width / 2, height - 30);
```

Ese vendría siendo el **estado 0**.

El **estado 1** son las líneas de mi segunda solemne.

El **estado 2** es la discoteca de día. Modifiqué más que nada la paleta de color para que se viera de día.

 ```fill(213, 218, 23);
  ellipse(700, 60,80, 80)
```

Para construir el sol.

```
 fill(255);
  textAlign(CENTER);
  textSize(20);
  text("¡ESPERO QUE LO HAYAS DISFRUTADO, VUELVE PRONTO!", width / 2, 400);
```
El dibujar fue mi parte favorita, aunque cuando estaba dibujando la versión de día no podía ver como iba quedando, asumí que era porque seriá la pantalla final y aún no lo tenía preparado del todo el código que lo ejecutaba.

**Códigos segunda solemne** Mantuve todo igual, excepto los cambios que mencioné anteriormente.

```function dibujarLinea(i){
  let temblor = random(-variacion, variacion);

  if (mouseX < 150) {
    stroke(255, 0, 255);
  }
  else if (mouseX < 300) {
    stroke(0, 255, 255);
  }
  else if (mouseX < 450) {
    stroke(204, 255, 0);
  }
  else {
    stroke(57, 255, 20);
  }

  line(i + temblor, 0, i + (mouseX - width / 2) / 5, height);
}
```


Como eliminé el ```altoCuadrante``` y ```anchoCuadrante```, los reemplacé por width y height dentro de la función ```line()```


- **Eventos** Elegí dos eventos. El primero hace que pasemos del estado 0 al 1 y se reproduzca la música. El segundo nos pasa al estado 2 para finalizar la experiencia.

```function mousePressed(){
  
  if(estado === 0){
    estado = 1;
  sonido.play();
}
  else if(estado === 2){
    estado = 0;
   }
}

function keyPressed(){
  if (estado === 1 && key === "Enter") {
    estado = 2;
    sonido.stop(); 
  }
```

**Errores que tuve** En estos errores consulté a una inteligencia artificial porque no estaba entendiendo que sucedía.
