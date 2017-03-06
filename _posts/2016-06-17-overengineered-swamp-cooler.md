---
layout: post
title:  "Overengineered Swamp Cooler Board"
description: "An overengineered swamp cooler board"
tags: [burning-man, electronics]
date: 2016-07-17 16:00:00 -0700
excerpt_separator: <!--more-->
---

For Burning Man 2014 me and a friend built a [Figjam Swamp Cooler](https://eplaya.burningman.org/viewtopic.php?t=33842). Since swamp coolers requires water to be re-filled when they evaporate, and since no one wants to wake up in the middle of a much needed sleep to do that, we built a mechanism for auto-refilling the bucket. We installed a [float switch](https://www.amazon.com/gp/product/B000NU69XO/ref=oh_aui_search_detailpage?ie=UTF8&psc=1), and together with a 12V relay attached it to an auxiliary pump. When the water level would go below the switch's threshold the relay would switch the power from the main pump to the aux pump and water from a reservoir will get pumped into the bucket. It worked wonderfully and we barely had to touch the system for the entire burn.
<!--more-->

![Assembled Boards]({{ site.baseurl }}/assets/overengineered-swamp-cooler/boards.jpg)

For Burning Man 2016 I decided to over-engineer further this since I wanted to build a second swamp cooler and all the point to point wiring of fuse/relay/fan/pumps is a pain in the ass. And you know, if it's worth doing it's worth overdoing. For that, I have built the board pictures above.

## Features

- Fuse, so if something shorts your power source won't hate you.
- Connectors that are easy to deal with on the field
  - Power input
  - Float switch (connected to relay)
  - Two relay-controlled outputs (one when the relay is not activated - to power main pump, one when relay is activated - to power aux pump)
  - Two always on outputs (one for the fan, one for good measure)

## Hardware


The Eagle design files and code are available [here](https://github.com/eranrund/eagle/tree/master/swamp-cooler).

### Design
[Schematics]({{ site.baseurl }}/assets/overengineered-swamp-cooler/sch.png)

[Board]({{ site.baseurl }}/assets/overengineered-swamp-cooler/brd.png)

### Shopping list
 - [PCB](https://oshpark.com/shared_projects/03cD43VN)
 - 3x 680ohm resistors
 - 3x 5mm LED
 - 1x [Relay](http://www.taydaelectronics.com/mini-relay-spdt-5-pins-12vdc-10a-120v-contact.html)
 - 6x [Connectors](http://www.taydaelectronics.com/connectors-sockets/terminal-blocks/pluggable/2-pin-male-plug-in-type-vertical-terminal-block-5mm-5ehdrc.html) + [Plugs](http://www.taydaelectronics.com/connectors-sockets/terminal-blocks/pluggable/2-pin-female-plug-in-type-vertical-terminal-block-5mm-5esdv.html)
 - 1x [Fuse holder](http://www.taydaelectronics.com/fuse-holder-with-cover-5x20mm-m205-pcb-4a.html)
 - 1x [Fuse](http://www.taydaelectronics.com/fuse-glass-fast-acting-3a-5x20.html)

### TODO
 - Post pictures of swamp cooler using this board
