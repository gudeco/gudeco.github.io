---
layout: post
title:  Assembling and Modifying the Incubator
---

The first step to develop cell cultures in order to engage in biohacking experiments or feed a bioreactor is to find a way to optimize the colonies' growth and keep them thriving. Since we will be working with different types of microbiological material, it is desirable that parameters such as temperature and medium are adjustable.

A simple way to move forward with such requirements is to build an insulated box furnished with a variable heat source, that is, an <a href="http://en.wikipedia.org/wiki/Incubator_(culture)"> incubator </a>. The medium can be controlled by using different types of <a href="http://en.wikipedia.org/wiki/Petri_dish"> Petri Dishes </a> to store the colonies.

Styrofoam sheets were used to isolate the inner part from the cover and the outside environment. Heat was provided by an infrared lamp, which turns on and off depending on the target temperature and on the readings of a <a href="http://en.wikipedia.org/wiki/Thermistor> thermistor </a>. 

The <a href="http://biohackacademy.github.io/biofactory/class/1/pdf/5%20Incubator%20design.pdf"> original project </a> was modified in the sense that a different LCD pannel was used and the fan's mosfet was replaced by a relay. The <a href="https://drive.google.com/open?id=0BxTWOUpE59OrZGNIN1p3WS0ycWtWeHZWWklrV0hfdGxhaXZJ&authuser=0"> schematics </a> can be better visualized with <a href="http://fritzing.org/download/"> Fritzing </a> and the full Arduino code can be downloaded <a href="https://drive.google.com/file/d/0BxTWOUpE59OrLVlYcmQ0X3VoU2M/view?usp=sharing"> through this link </a>, but here is a quick incomprehensible sketch that was subsequently attacked and destroyed by dead animals from ancient times:

<img src="https://fbcdn-sphotos-e-a.akamaihd.net/hphotos-ak-xfa1/v/t1.0-9/15576_1423136071327912_5648323525979756981_n.jpg?oh=21dd55d2a1c54b099639852dff4f61c2&oe=55D7B0F1&__gda__=1439940164_064f154a5a938a3014d26cc7e064433f"alt="inc" width="800" height="582" border="1" />

The MDF encasing structure was laser cut in accordance with <a href="biohackacademy.github.io/biofactory/class/1/Incubator-SVGs.zip"> this file </a> and assembled in a workshop. Holes were drilled to open path for cabling and to clench the PC cooler that serves as a fan to disseminate heat throughout the inner compartment.

<img src="https://fbcdn-sphotos-h-a.akamaihd.net/hphotos-ak-xpa1/v/t1.0-9/p480x480/10404242_1099899320027100_3108853078127897254_n.jpg?oh=30f4fcb9408b64840d7b67ba259bc364&oe=559FE179&__gda__=1439960252_feb8793586dcf811c2f7faa947721168" 
alt="inc" width="480" height="720" border="1" />

The breadboard and Arduino were attached to the bottom of the external framework.

<img src="https://fbcdn-sphotos-h-a.akamaihd.net/hphotos-ak-xft1/v/t1.0-9/11141156_1423156954659157_3989832340389439509_n.jpg?oh=95bce3d68cc58efa183c6ce7b12a8985&oe=559C6E82&__gda__=1440787939_c2ea4493c9e7dffcd0345fb99d8647a4" 
alt="inc" width="400" height="235" border="1" />

With everything in place, it was time to turn it on:

<img src="https://fbcdn-sphotos-a-a.akamaihd.net/hphotos-ak-xpa1/v/t1.0-9/11048760_1099899450027087_2807690121244586735_n.jpg?oh=9b68762beac92145d30e0e48e0e46f89&oe=55E44C2F&__gda__=1436063045_28e9849dc62b40c170e6e6828d4b4069" 
alt="inc" width="528" height="960" border="1" />

These were some of the Petri Dishes used in our first experiment, in which random bacteria were collected from people's hands and personal objects for testing purposes:

<img src="https://fbcdn-sphotos-d-a.akamaihd.net/hphotos-ak-xpf1/v/t1.0-9/10898297_1423073181334201_8190557592477610890_n.jpg?oh=0d47447df6dcc29c8fd02685348a4929&oe=559BCDE9&__gda__=1441139670_2c2e2218cc17e0ab0020071efa0633ba" 
alt="inc" width="337" height="300" border="1" />

In the absence of better life-wasting activities, you can watch the colonies grow, like I did.

<img src="https://fbcdn-sphotos-g-a.akamaihd.net/hphotos-ak-xaf1/v/t1.0-9/1546273_1423063354668517_6674142658355745583_n.jpg?oh=a9b66f904ff077f6e79bac6aef33ac4a&oe=55991697&__gda__=1436403238_1c215a35c7634a29ed6a686b296f97b5" 
alt="inc" width="281" height="499" border="1" />

(at least now they do it faster)
