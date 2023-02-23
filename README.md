# Lleida.net  Ransomware Challenge
## Level 1

Vam descarregar l'arxiu i el vam analitzar amb un programa per visualitzar la imatge en Hexadecimal.
![Hex Editor Pro](https://i.imgur.com/81nMzIr.png)
**Flag**
| UNEXPECTED |
## Level 2

Vam investigar la imatge i posava que obríssim la llum, vam veure que a l'URL posava level/2/false i el vam canviar a true. (https://hackathon.lleida.net/level/2/true)
![Ruta](https://i.imgur.com/bE4ja4n.png)
   **Flag**
--------------

## Level 3
Vam visualitzar la imatge fins a donar-nos compte que hi havia punts vermells i que feien relleu a algunes lletres.
Totes aquestes formaven **lum poirot**, vam cercar a internet i vam tovar una pel·lícula anomenada POIROT que tenia el mateix barret i bigoti que al de l'endivinalla.

**Flag**
| POIROT |

![Imatge Proporcionada](https://hackathon.lleida.net/img/22d86afe01bf3cee2da05c30aaaaeb8e.png)


## Level 4

Vam visualitzar que hi havia dos possibles valors, negre o blanc, 1 o 0 i estaven agrupats per 8 posicions, com el binari, vam passar de binari a text i vam tovar:

01000001 01001110 01001111 01001110 01011001 01001101 01001111 01010101 01010011
**Flag**
|ANONYMOUS|
## Level 5
Vam visualitzar  un codi que estava estructurat com un text habitual, però que les lletres no formaven cap ordre lògic, com si haguessin aplicat ROT13, vam utilitzar un codi propi nostre en C# per esbrinar paraula per paraula el que posava, ja que tenia rotacions diferents.
![Resolució Text](https://i.imgur.com/nJLJMNo.png)
Posava una endevinalla i la resposta era la flag.
**Flag**
| TIME |


## Level 6
Vam visualitzar una imatge d'un quadre, però ens vam fixar que tenia parts d'un codi QR, amb eines d'edició de fotografia vam retallar els QR de la imatge i vam poder reconstruir-lo per a llegir el resultat següent:

34.247.204.45 06eb1263f226abac.com

Vam utilitzar el fitxer etc/hosts per a poder accedir al Virtual Hosting.
![website 06eb1263f226abac.com](https://i.imgur.com/cKv6v2D.png)
Vam fixar-nos que contenia codi JavaScript on vam passar de l'Array de caràcters a String i vam traduir-ho de Japonès a Espanyol, com vam trobar el següent:
![traducció](https://i.imgur.com/s4SrUx9.png)
Vam veure que tots els personatges eren Robots, llavors vam caure en l'arxiu robots.txt tot i que en aquell moment no ens va funcionar ni amb .robotx.txt vam pensar que les webs molts cops tenen un “SiteMap”, vam accedir i vam visualitzar una ruta que era la d' “about.html”, d'allà vam accedir a l'Inspeccionar elemento on vam visualitzar el següent:
![resolve](https://i.imgur.com/A0dsEIB.png)
**Flag**
|SMOOTHIE



## Level 7
Vam descarregar l'arxiu i en visualitzar que posava "Good luck and strength!" i que tenia una obsessió amb els nombres primers vam pensar que havíem de fer Força bruta amb una WordList amb nombres primers en total de 100.000 nombres primers i seguidament del 100.000 als 200.000 primers.


* Primerament, vam provar d'extreure el Hash del fitxer GPG, però no admetia bé el HASH, no l'identificava.

* Seguidament, vam provar d'extreure el Hash amb gpg2john i vam provar a fer Força Burta amb “John The Ripper” i la WordList de numeros primers generada.

![arxiu GPG](https://i.imgur.com/k5cSCbM.png)

**Flag**
| 104369 |


## Level 8
A partir de l'arxiu del repte anterior vam desencriptar el fitxer *.gpg* amb la clau *104369* i vam extreure la següent informació (un enllaç d'una api ):
*https://api.lleida.net/dtd/messages/v3/en/index.html*
*smoothie*
*I2hgw1)IiS*

Utilitzant POSTMAN vam extreure la conversa de missatges de l'API , d’alla vam extreure un enllaç a Google Drive com aquest, (*https://drive.google.com/drive/folders/1Bb14rnjPHSVNtXurfEl7umW9hC8-tvdA*).
 Vam visualitzar un arxiu **document.zip** protegit amb contrasenya i una imatge **win.png** que contenia el següent:
 
 ![win.png](https://i.imgur.com/qlaaVbh.png)
 
 A partir d'aquí vam pensar que es tractava de la contrasenya del fitxer *documents.zip* i vam realitzar el següent:

 * Vam pensar que es tractava d'un mes de l'any o d'un signe de l'horòscop, ja que contenia una M que el significat és Sagitari.

 * Vàrem realitzar combinacions de paraules i frases fetes que poguessin estar relacionades, amb “La Gota Fria”, estacions de l'any, algun dia específic ...

* Vam intentar visualitzar les metadades els fitxers i no vam poder extreure res d'informació.

* Vam portar a cap cerques d'imatge inversa de tota la imatge i de fragments.

* Vam dur a terme una cerca del codi UNICODE dels següents símbols.

* Vam estar veient que al Notepad, Word i altres editors tenien unes fonts anomenades Webdings i Windings que contenien símbols i a través d'escriure l'abecedari complet amb la font Arial i a la part inferior l'abecedari complet amb la font Webding i Windings i vam poder extreure la frase significada.

*☼︎ ♏︎ 💧︎ ❄︎ 📁︎ ❒︎ ☜︎ 📬︎* --> **ReST0rE.**

**Flag**
| ReST0rE. |

## Level 9
Vam accedir a una API que validava els DNI amb els documents que vam extraure de *documents.zip*. Vam poder observar que hi havia algunes diferències, hi havia un caràcter que variava segons el document.
Vam ordenar els canvis d'esquerra a dreta i d'adal a baix extraient una cadena de caràcters:

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
Vam enviar un hash a traves d'un correo electronic Certificat entregant.





