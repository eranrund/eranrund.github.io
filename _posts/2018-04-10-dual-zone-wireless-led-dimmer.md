---
layout: post
title:  "Dual zone wireless LED dimmer"
description: "Dual zone wireless LED dimmer"
tags: [electronics, vanlife]
date: 2018-04-10 23:42:00 -0700
excerpt_separator: <!--more-->
---


While I haven't mentioned it on this blog, last year I bought a Dodge Sprinter 2005 van with the intent of converting it into a livable space/festival van. There's a lot I have to say about that project, but that will wait for another post. In this post I want to show an LED dimmer that I built for the van. The requirements were:
* 12V powered.
* Dual-zone, meaning I can dim two separate circuits independently.
* Wireless - I didn't want to run anything but 12V power to the dimmer units.
* Multiple transmitter support - I wanted to have a transmitter near the door as well as one near the bed. Who wants to get out of bed to turn off the lights?
* Capable of supplying at least 2A per channel.
* Use this [fancy](https://www.mouser.com/ProductDetail/652-PTL45-15R0-103B2) sliders that have a red LED light, to make it easier to find in the dark.
* Have one PCB that can either act at the transmitter or the receiver depending on which components get installed on in.

It's a relatively simple project, and it works well. So far I have had zero issues with it. It's built around the [ATMEGA328](https://www.microchip.com/wwwproducts/en/ATmega328) MCU and the [nRF24L01+](http://www.nordicsemi.com/eng/Products/2.4GHz-RF/nRF24L01P) 2.4GHz transceiver. It uses the [RF24](https://github.com/nRF24/RF24) library which made interfacing the nRF24L01+ a breeze.

![Boards]({{ site.baseurl }}{% link /assets/dual-zone-wireless-led-dimmer/boards.png %})

[View schematics](https://github.com/eranrund/eagle/blob/master/dual-led-wireless-dimmer/dual-led-wireless-dimmer-sch.pdf) or [browse the repository](https://github.com/eranrund/eagle/tree/master/dual-led-wireless-dimmer)
