# Lleida.net  Ransomware Challenge
## Level 1

Descargamos el archivo y lo analizamos con un programa para visualizar la imagen en hexadecimal.

![Hex Editor Pro](https://i.imgur.com/81nMzIr.png)

**Flag**
| UNEXPECTED |
## Level 2

Investigamos la imagen y vimos que decía que abriéramos la luz, observamos que en la URL ponía level/2/false y lo cambiamos a true  asi siendo true ON y false OFF (https://hackathon.lleida.net/level/2/true)

![Ruta](https://i.imgur.com/bE4ja4n.png)
   **Flag**
--------------

## Level 3
Visualizamos la imagen hasta que nos dimos cuenta de que había puntos rojos que resaltaban algunas letras. Todas estas letras formaban "lum poirot", buscamos en internet y encontramos una película llamada "POIROT" que tenía el mismo sombrero y bigote que en el acertijo.

**Flag**
| POIROT |

![Imatge Proporcionada](https://hackathon.lleida.net/img/22d86afe01bf3cee2da05c30aaaaeb8e.png)


## Level 4

Visualizamos que había dos posibles valores, negro o blanco, 1 o 0, y estaban agrupados por 8 posiciones, como el binario, pasamos de binario a texto y encontramos:

01000001 01001110 01001111 01001110 01011001 01001101 01001111 01010101 01010011
**Flag**
|ANONYMOUS|

## Level 5
Visualizamos un código que estaba estructurado como un texto normal, pero que las letras no formaban ningún orden lógico, como si hubieran aplicado ROT13, utilizamos un código propio en C# para descifrar palabra por palabra lo que decía, ya que tenía rotaciones diferentes.
![Resolució Text](https://i.imgur.com/nJLJMNo.png)
Decía una adivinanza y la respuesta era la flag.
**Flag**
| TIME |


## Level 6
Visualizamos una imagen de un cuadro, pero nos dimos cuenta de que tenía partes de un código QR, con herramientas de edición de fotografía cortamos los QR de la imagen y pudimos reconstruirlo para leer el resultado siguiente:

34.247.204.45 06eb1263f226abac.com

Utilizamos el archivo etc/hosts para poder acceder al Virtual Hosting.
![website 06eb1263f226abac.com](https://i.imgur.com/cKv6v2D.png)
Nos fijamos en que contenía código JavaScript donde pasamos de Array de caracteres a String y lo traducimos del japonés al español, como encontramos lo siguiente:
![traducció](https://i.imgur.com/s4SrUx9.png)
Notamos que todos los personajes eran robots, entonces recurrimos al archivo `robots.txt`, aunque en ese momento no funcionó ni con `.robots.txt`. Pensamos que las webs a menudo tienen un "SiteMap", accedimos y visualizamos una ruta que era la de "about.html". Desde allí accedimos a la Inspección de elementos donde visualizamos lo siguiente:
![resolve](https://i.imgur.com/A0dsEIB.png)
**Flag**
|SMOOTHIE|



## Level 7
Descargamos el archivo y al ver que decía "Good luck and strength!" y que tenía una obsesión con los números primos, pensamos que teníamos que hacer Fuerza Bruta con una WordList con números primos, en total 100.000 números primos, y después del 100.000 hasta el 200.000.

* Primero intentamos extraer el Hash del archivo GPG, pero no lo identificaba correctamente.

* Luego intentamos extraer el Hash con `gpg2john` y probamos la Fuerza Bruta con **"John The Ripper"** y la WordList de números primos generada.

![arxiu GPG](https://i.imgur.com/k5cSCbM.png)

**Flag**
| 104369 |


## Level 8
A partir del archivo del reto anterior, desencriptamos el archivo .gpg con la clave 104369 y extrajimos la siguiente información: un enlace de una API, 
https://api.lleida.net/dtd/messages/v3/en/index.html
smoothie
I2hgw1)IiS

Utilizando POSTMAN extrajimos la conversación de mensajes de la API. De allí sacamos un enlace a Google Drive como este (https://drive.google.com/drive/folders/1Bb14rnjPHSVNtXurfEl7umW9hC8-tvdA). Visualizamos un archivo document.zip protegido con contraseña y una imagen win.png que contenía lo siguiente:
 
 ![win.png](https://i.imgur.com/qlaaVbh.png)
 
 A partir de aquí, comenzamos a pensar que se trataba de la contraseña del archivo documents.zip y llevamos a cabo las siguientes acciones:

* Pensamos que podría tratarse de un mes del año o un signo del zodiaco, ya que contenía una "M" cuyo significado es Sagitario.
* Realizamos combinaciones de palabras y frases hechas que pudieran estar relacionadas con "La Gota Fría", estaciones del año, algún día específico...
* Intentamos visualizar los metadatos del archivo, pero no pudimos extraer ninguna información.
* Realizamos búsquedas de imágenes inversas de toda la imagen y de fragmentos.
* Realizamos una búsqueda del código UNICODE de los siguientes símbolos.
* Observamos que en el Notepad, Word y otros editores había fuentes llamadas Webdings y Windings que contenían símbolos y a través de escribir el abecedario completo con la fuente Arial y debajo el abecedario completo con la fuente Webding y Windings, pudimos extraer la frase significativa.

*☼︎ ♏︎ 💧︎ ❄︎ 📁︎ ❒︎ ☜︎ 📬︎* --> **ReST0rE.**

**Flag**
| ReST0rE. |

## Level 9
Accedimos a una API que validaba los DNI con los documentos que extrajimos de documents.zip. Pudimos observar que había algunas diferencias, había un carácter que variaba según el documento.
Ordenamos los cambios de izquierda a derecha y de arriba abajo, extrayendo una cadena de caracteres:

```
============================================================================================
IDESPBDS163005748056179W<<<<<<^7709287M2310037ESP<<<<<<<<<<<7^RAMON<VISA<<ROGER<MIGUEL<<<<<<
IDESPBDS163005748056179W<<<<<<^7709287M2310035ESP<<<<<<<<<<<4^RAMON<VISA<<ROGER<MIGUEL<<<<<<
IDESPBDS163005748056179W<<<<<<^7709280M2310037ESP<<<<<<<<<<<4^RAMON<VISA<<ROGER<MIGUEL<<<<<<
IDESPBDS163005748056179W<<<<<<^7709287M2310037ESP<<<<<<<<<<<4^RAMOH<VISA<<ROGER<MIGUEL<<<<<<
IDESPBDS163005648056179W<<<<<<^7709287M2310037ESP<<<<<<<<<<<4^RAMON<VISA<<ROGER<MIGUEL<<<<<<
============================================================================================
1.------------6
2.----------------------------------------------------------------H
3.-----------------------------------0
4.-------------------------------------------5
5.----------------------------------------------------------
============================================================================================
```
**Flag**
| 6H057 |



## Level 10
**Hash:** *3deb17c3738d1abe68c3fa6f3e2b3a5c46519da55fb3503e69756f0e895faccf*
Enviamos un hash a través de un correo electrónico certificado y entregado de manera segura.




