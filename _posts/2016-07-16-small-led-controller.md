---
layout: post
title:  "Small addressable LED strip controller"
tags: [burning-man, electronics]
date: 2016-07-16 02:00:00 -0700
excerpt_separator: <!--more-->
---

![LED Controller]({{ site.baseurl }}/assets/img/small-led-controller/controller.jpg)
![LED Controller being used]({{ site.baseurl }}/assets/img/small-led-controller/demo.jpg)

This is a small LED controller I built for Burning Man 2016 as I was tired from hand-soldering Arduinos, and wanted a more durable solution. There's nothing fancy here, but it's simple, cheap and works.
<!--more-->

## Features

- ATMEGA32U CPU (Same as Arduino Leonardo).
- Connectors for up to 2 clockless LED strips (although fitting the wires in the tiny enclosure will be tricky with 2).
- Soft power control for LED strips.
- 4 push buttons.
- Powered via USB (meant to be powered from USB battery packs).
- Cheap, easy to get enclosure.


## Hardware

The Eagle design files and code are available [here](https://github.com/eranrund/eagle/tree/master/led-keychain). It's a mess, but I'll get to cleaning it at some point. Maybe after the burn :)

### Design
[Schematics]({{ site.baseurl }}/assets/img/small-led-controller/sch.png)

[Board]({{ site.baseurl }}/assets/img/small-led-controller/brd.png)

### Shopping list
 * [PCB](https://oshpark.com/shared_projects/zXOWZoeE)
 * [BOM](http://www.mouser.com/ProjectManager/ProjectDetail.aspx?AccessID=8ce4c18cea)
 * [USB Cable](http://www.frontx.com/cpx505.html)
 * [LED Cable](http://www.aliexpress.com/item/50pairs-Lot-2pin-40cm-Wire-Line-led-connector-Cable-female-male-2X-0-5-mm2-for/1772228025.html?ws_ab_test=searchweb201556_0,searchweb201602_3_10057_10056_10037_10055_10049_10017_405_404_407_10058_10032_10040,searchweb201603_4&btsid=9a3ca38e-774f-4e2a-87e5-60a59cc6af78)
 * [Case](http://www.polycase.com/fb-45-series)

A [nibbling tool](https://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=nibbling+tool) made it very easy to make the side cuts in the enclosure.
