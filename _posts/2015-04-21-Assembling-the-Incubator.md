---
layout: post
title:  Assembling and Modifying the Incubator
---

The first step to develop cell cultures in order to engage in biohacking experiments or feed a bioreactor is to find a way to optimize the colonies' growth and keep them thriving. Since we will be working with different types of microbiological material, it is desirable that parameters such as temperature and medium are adjustable.

A simple way to move forward with such requirements is to build an insulated box furnished with a variable heat source, that is, an <a href="http://en.wikipedia.org/wiki/Incubator_(culture)"target="_blank"> incubator</a>. The medium can be controlled by using different types of <a href="http://en.wikipedia.org/wiki/Petri_dish"target="_blank"> Petri Dishes </a> to store the colonies.

Styrofoam sheets were used to isolate the inner part from the cover and the outside environment. Heat was provided by an infrared lamp, which turns on and off depending on the target temperature and on the readings of a <a href="http://en.wikipedia.org/wiki/Thermistor"target="_blank"> thermistor </a>. 

The <a href="http://biohackacademy.github.io/biofactory/class/1/Incubator-Fritzing.fzz"target="_blank"> original project </a> was modified in the sense that a different LCD pannel was used and the fan's mosfet was replaced by a relay. The <a href="https://drive.google.com/open?id=0BxTWOUpE59OrZGNIN1p3WS0ycWtWeHZWWklrV0hfdGxhaXZJ&authuser=0"target="_blank"> schematics </a> can be better visualized with <a href="http://fritzing.org/download/"target="_blank"> Fritzing </a> and the full Arduino code can be downloaded <a href="https://drive.google.com/file/d/0BxTWOUpE59OrLVlYcmQ0X3VoU2M/view?usp=sharing"target="_blank"> through this link </a>, but here is a quick incomprehensible sketch that was subsequently attacked and destroyed by dead animals from ancient times:

<img src="https://fbcdn-sphotos-c-a.akamaihd.net/hphotos-ak-xtf1/v/t1.0-9/11061982_1423136377994548_1894585970475729822_n.jpg?oh=d3fc5f0d9d42b9d613dd0104a357299d&oe=559862D8&__gda__=1440498032_20d922ecdbd4b3af3dbcdfe68a04fdde"alt="inc" width="800" height="565" border="1" />

<img src="https://scontent-gru.xx.fbcdn.net/hphotos-xpa1/v/t1.0-9/11056068_1423358411305678_3956225601870821440_n.jpg?oh=5d77d7c1b77f0d3a0d4265ebdea8a4d1&oe=55E242ED"alt="inc" width="800" height="565" border="1" />

The MDF encasing structure was laser cut in accordance with <a href="biohackacademy.github.io/biofactory/class/1/Incubator-SVGs.zip"target="_blank"> this file </a> and assembled in a workshop. Holes were drilled to open path for cabling and to clench the PC cooler that serves as a fan to disseminate heat throughout the inner compartment (as shown in the horrible picture below).

<img src="https://fbcdn-sphotos-a-a.akamaihd.net/hphotos-ak-xtp1/v/t1.0-9/p320x320/11167673_1423204627987723_7386591215262085024_n.jpg?oh=141e566bff765a3dcd8d56753fb8f7c8&oe=55D8D21B&__gda__=1435992894_1ae2d4dd5a0f1ead7b1d7ea4d89cd80d" 
alt="inc" width="480" height="720" border="1" />

The breadboard and Arduino were attached to the bottom of the external framework.

<img src="https://fbcdn-sphotos-h-a.akamaihd.net/hphotos-ak-xft1/v/t1.0-9/11141156_1423156954659157_3989832340389439509_n.jpg?oh=95bce3d68cc58efa183c6ce7b12a8985&oe=559C6E82&__gda__=1440787939_c2ea4493c9e7dffcd0345fb99d8647a4" 
alt="inc" width="400" height="235" border="1" />

With everything in place, it was time to turn it on:

<img src="https://scontent-gru.xx.fbcdn.net/hphotos-xap1/v/t1.0-9/11188248_1423179397990246_3816158107642862709_n.jpg?oh=190d64f8e50b00d2e9e411b48a217175&oe=55DEFACE" 
alt="inc" width="281" height="499" border="1" />

Gladly it worked and nobody died. These were some of the Petri Dishes used in our first experiment, in which random bacteria were collected from people's hands and personal objects for testing purposes:

<img src="https://fbcdn-sphotos-d-a.akamaihd.net/hphotos-ak-xpf1/v/t1.0-9/10898297_1423073181334201_8190557592477610890_n.jpg?oh=0d47447df6dcc29c8fd02685348a4929&oe=559BCDE9&__gda__=1441139670_2c2e2218cc17e0ab0020071efa0633ba" 
alt="inc" width="337" height="300" border="1" />

In the absence of better life-wasting activities, you can watch the colonies grow, like I did.

<img src="https://fbcdn-sphotos-g-a.akamaihd.net/hphotos-ak-xaf1/v/t1.0-9/1546273_1423063354668517_6674142658355745583_n.jpg?oh=a9b66f904ff077f6e79bac6aef33ac4a&oe=55991697&__gda__=1436403238_1c215a35c7634a29ed6a686b296f97b5" 
alt="inc" width="281" height="499" border="1" />

(at least now they do it faster)
