# 

## Level 1

Vem descarregar l'arxiu i el vam analitzar amb un programa per visualitzar la imatge en Hexadecimal.
![Hex Editor Pro](https://i.imgur.com/81nMzIr.png)
**Flag**
| UNEXPECTED |
## Level 2

Vem investigar la imatge i posava qu obrisim la llum, vam veure que al url posaba level/2/false i el vem cambiar a true. (https://hackathon.lleida.net/level/2/true)
![Ruta](https://i.imgur.com/bE4ja4n.png)
   **Flag**
--------------

## Level 3
Vam visualitzar la imatge fins donar-nos compte que hi habien punts vermells i que feien relleu a algunes lletres.
Totes aquestes formaven **lum poirot**, vam cercar a internet i vam tobar una pelicula anomenada POIROT que tenia el mateix barret i bigoti que al de la endivinalla.

**Flag**
| POIROT |

![Imatge Proporcionada](https://hackathon.lleida.net/img/22d86afe01bf3cee2da05c30aaaaeb8e.png)


## Level 4

Vam visualitzar que hi habien dos posibles valors negre o blanc, 1 o 0 i estaven agrupats per 8 posicions com el binari, vam pasar de binari a text i vam tovar :

01000001 01001110 01001111 01001110 01011001 01001101 01001111 01010101 01010011
**Flag**
|ANONYMOUS|
## Level 5
Vam visualizar  un codi que estava estructurat com un text habitual pero que les lletres no formaven cap ordre llogic, com si haguesin aplicat ROT13, vam utlitlitzar un codi propi nostre en C# per esbrinar paraula per paraula el que posaba, ja que tenia rotacions diferents.
![Resolucio Text](https://i.imgur.com/nJLJMNo.png)
Posaba una andivinalla con la resposta era la flag.
**Flag**
| TIME |


## Level 6
Vam visualitzar una imatge d'un quadre pero ens vem fixar que tenia parts d'un codi qr, amb eines d'edicio de fotografis vam retallar els QR de la imatge i vam poder reconstruirlo per a llegir el resultat seguent:

34.247.204.45 06eb1263f226abac.com

Vam utilitzar el fitxer etc/hosts per a poguer accedir a el Virtual Hosting.
![website 06eb1263f226abac.com](https://i.imgur.com/cKv6v2D.png)
Vam fixarnos que contenia codi javascript on vam pasar del Array de caracteres a String i vam tradurir-ho de Japones a Español, con vam trobar el seguent:
![traduccio](https://i.imgur.com/s4SrUx9.png)
Vam veure que tots els personatges eren Robots, llavors vem caure en l'arxiu robots.txt tot i que en aquell moment no ens va funcionar ni amb .robotx.txt vem pensar que les webs molts cops tenen un SiteMap, vam accedir i vam visualitzar una ruta que era la de about.html d'alla vem accedir al Inspeccionar elemento on vam visualitzar el seguent:
![resolve](https://i.imgur.com/A0dsEIB.png)
**Flag**
|SMOOTHIE



## Level 7
Vem descarregar l'arxiu i al visualitzar que posaba "Good luck and strength!" i que tenia una obseció amb els numeros primers vem pensar que habiem de fer Força bruta amb una Wordlist amb numeros primers en total de 100000 primers nombres primers i seguidament del 100000 al 200000 primers.


* Primerament vam probar a extreure el hash del fitxer GPG pero no admetia be el HASH, no l'identificaba.

* Seguidament vem probar a extreure el hash amb gpg2john i vam probar a fer Força burta amb John The Ripper i la wordlist de numeros primers generada.

![arxiu GPG](https://i.imgur.com/k5cSCbM.png)

**Flag**
| 104369 |


## Level 8
A partir de l'arxiu del repte anterior vam desencriptar el fitxer *.gpg* amb la clau *104369* i vam extreure la segent informacio (un enllaç d'una api ):
*https://api.lleida.net/dtd/messages/v3/en/index.html*
*smoothie*
*I2hgw1)IiS*

Utilitzant Postman vam extreure la conversa de missatges de la API vam extreure un enllaç a google drive (*https://drive.google.com/drive/folders/1Bb14rnjPHSVNtXurfEl7umW9hC8-tvdA*).
 Vam visualitzar un arxiu **document.zip** protegit amb contrasenya i una imatge **win.png** quecontenia els seguent:
 ![win.png](https://i.imgur.com/qlaaVbh.png)
 A partir d'aqui vem pensar que es tractava de la contrasenya del fitxer *documents.zip* i vam realitzar el seguent:

 * Vem pensar que es tractaba d'un mes de l'any o d'un signe de l'horoscop ja que contenia una M que el significat es Sagitario.

 * Vem realizar combinacions de paraules i frases fetes que poguesin estat relacionades ("La Gota Fria", estacions de l'any , algun dia especific ...).

* Vem intentar visualitzar les metadades els fitxers i no vem poguer extreure res d'informació.

* Vem realitzar cerques d'imatge inversa de tota la imatge i de fragments.

* Vem realitzar una cerca del codi UNICODE dels seguents simbols.

* Vem estar veient que al Notepad, Word i altres editors tenien unes fonts anomenades Webdings i Windings que contenien simbols i a traves d'escriure l'abecedari coplert amb la font arial i a la part inferior l'abecedari complert amb la font Webding i Windings i vam poguer extreure la frase significat.

*☼︎ ♏︎ 💧︎ ❄︎ 📁︎ ❒︎ ☜︎ 📬︎* --> **ReST0rE.**

**Flag**
| ReST0rE. |

## Level 9
Vam accedir a una API que validaba els DNI amb els documents que vam extraure de *documents.zip*. Vem poguer observar que hi habien algunes diferencies, hi habia un caracter que variaba segons el document.
Vam ordenar els cambis de esquerra a dreta i de adal abaix extreient una cadene de caracters:

**Flag**
|  |


## Level 10
**Hash:** *3deb17c3738d1abe68c3fa6f3e2b3a5c46519da55fb3503e69756f0e895faccf*
Vem enviar un hash a traves d'un correo electronic Certificat entregant.




