# Juego del Ahorcado con HTML y Javascript

En este juego vamos a tener un tablero de tipo "querty".  Al igual que el juego de la vida real, seleccionaremos una letra de una palabra oculta.  Si la letra coincide se dibuja en los recuadros blancos, de lo contrario se dibuja una parte del ahorcado hasta que este es completamente dibujado, con todo y la soga de la horca, y el juego termina.

Si el usuario adivina la palabra, el juego termina felicitando al usuario.  Las letras son eliminadas del teclado una vez pulsadas para evitar que el usuario las pulse dos veces.

Las partes del ahorcado y el patíbulo son dibujos .png, por lo que usted podrá cambiarlos por algo mas elaborado cuando guste.

## Las variables del juego [juego_ahorcado_01.html]
- Las variables del juego se declaran dentro de la etiqueta *script*, fuera de la función *onload*.
- Algunas variables se van a utilizar para realizar los dibujos de las teclas y otras para almacenar la información en arreglos.
- Con la variable *letras* tenemos el formato de teclado.
- Se tienen arreglos para almacenar las teclas [*teclas_array*], las letras [*letras_array*] y las palabras [*palabras_array*].
- Se tienen variables para calcular los aciertos y errores del jugador [*aciertos*, *errores*]
- Se crean los objetos que permiten almacenar la información: *Tecla*, *Letra*
- Se llena el arreglo donce se almacenan las palabras a adivinar en el juego: *palabras_array.push("PEGASO")*

## Dibujar el teclado [juego_ahorcado_02.html]
- Para dibujar el teclado se necesitan las funciones correspondientes para dibujar las cajas de las teclas y de las letras.
- La función *dibujaTecla* dibuja la letra de la tecla, y la función *dibujaCajaLetra* solo la casilla en blanco vacía.
- La función *teclado* llama a las funciones *dibujaTecla* y *dibujaCajaLetra*.
- La función *teclado* es invocada desde la función *onload*, pero definida fuera de ésta.
- Dentro de la función *teclado* se observan las variables de trabajo y un ciclo for, que permite recorrer la cadena de letras. En Javascript las cadenas pueden ser tratadas como arreglos.  El ciclo dibuja el teclado.
- Dentro del ciclo, se separa cada una de las letras de la cadena con el método *substr()*
- Se crea una instancia del objeto *tecla*, se llama el método *dibuja* y se almacena la referencia en el arreglo *teclas_array*.
- Se incrementan los contadores x e y.
- Aqui se tendría el teclado base, pero no luce como el teclado de la computadora por lo que se modifica con un poco de código.
- El teclado de la computadora tiene tres hileras: dos de 10 teclas y una de 7, con un pequeño desfasamiento.
![teclasdo juego](/imagenes/teclado_juego.png "Teclado juego")

## Pintar la palabra secreta [juego_ahorcado_03.html]
- Se procede a seleccionar y dibujar la palabra secreta en el lienzo.
- Se crea una función llamada *pintaPalabra()*, y su estructura se ubica encima de la función *onload*
- En la linea de código *var p = Math.floor(Math.random()\*palabras_array.length);* se selecciona un número aleatorio entre 0 y la longitud menos 1 del arreglo de palabras.
- En la cadena *palabra* se almacena el valor de la misma.
- En la variable *x* se calcula el espacio para centrar la palabra.
- Dentro de un ciclo se pinta la letra.  Se separa cada una de las letras de la palabra seleccionada al azar, creando una instancia del objeto *Letra* y dibujando el cuadrito con el metodo correspondiente.
- Se mete la referencia del objeto *Letra* en un arreglo, y se incrementa el valor de la *x*.  Con ello se tiene pintado en el Canvas un cuadro por cada una de las letras de la palabra seleccionada al azar.
- Al recargar la página, un número diferente de cuadros debe pintarse.
![teclasdo juego](/imagenes/teclado_palabra.png "Teclado juego")

## Dibujar la horca del ahorcado [juego_ahorcado_04.html]
- La horca o patíbulo se tiene dibujado previamente en archivos .png. Las imágenes se van cargando conforme se vayan necesitando.
- Se incluye el llamado a la función *cadalso()* en la rutina principal y se escribe la estructura de esa función.
- A la función *cadalso()* se le pasa la variable *errores* como parámetro.
- Se recibe el valor y se llama la imagen correspondiente.
![teclasdo juego](/imagenes/horca.png "Teclado juego")

## Seleccionar una tecla [juego_ahorcado_05.html]
- Hasta acá se tienen los elementos gráficos del juego y se procede ahora a escribir la lógica del mismo.
- Se crea un detector de eventos para cuando el usuario pulse sobre el canvas [*canvas.addEventListener("click", selecciona, false);*] y se crea la funcióno *selecciona()*
- La lógica implementada detecta dónde pulsa el usuario.
- Se usa una función para ajustar las coordenadas: *ajusta()*
- Al momento de pulsar sobre unos de los recuadros de las teclas dibujadas en el canvas por medio del ratón, deberá aparecer el número de tecla dentro del arreglo, aún no la letra.
![teclasdo juego](/imagenes/seleccion_tecla.png "Teclado juego")

## Empatar la letra seleccionada vs. las letras de la palabra [juego_ahorcado_06.html]
- Aquí ya se sabe cuál fue la letra seleccionada por el jugador y se conoce la palabra.  El siguiente paso es empatar o comparar ambos y determinar si es acierto o error.
- Para empatar los valores se trabaja dentro de la función *selecciona()*, quitanto la función *alert()* y procediendo a comparar la tecla seleccionada  con cada una de las letras de la palabra secreta.
- En el ciclo *for* se compara cada una de las letras de la palabra con la letra seleccionada por el usuario.
- Si coinciden, se procede a pintarla en la casilla correspondiente al objeto, incrementando en 1 a los aciertos y se pone una *bandera* con valor verdadero.
- Una palabra puede tener muchas coincidencias de una letra.
- La función *dibujaLetra()*
- Al seleccionar una tecla, si acierta, se pinta la letra en el recuadro, y si es un error aparecerá una parte del ahorcado.
- Falta eliminar la tecla pulsada y determinar si es fin de juego, ya sea que el usuario haya ganado o perdido.

## Game Over [juego_ahorcado_07.html]
- Finalmente, se toman las decisiones cuando el juego haya terminado y se borra la tecla cuando esta haya sido seleccionada.
- Se agrega nuevo código dentro de la función *selecciona()*
- Con ese código se determina si el usuario pulsó una tecla que está contenida en la palabra, entonces se manda un error cargando una imagen diferente.


### Fuente
Arce, Francisco.  Programe juegos con HTML5.  Editorial Alfaomega.