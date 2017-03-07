---
layout: post
title:  "DIY Music Machines - Ableton Live Controller Update"
description: "DIY Music Machines - Ableton Live Controller Update"
tags: [electronics, phi]
date: 2017-03-05 15:45:00 -0700
excerpt_separator: <!--more-->
---

Since I wrote the [previous post]({{ site.baseurl }}{% link _posts/2016-12-08-diy-music-machines-intro.md %}) about this project I have made significant progress on the Ableton Live auto-mapping modular controller I am building:

![Front]({{ site.baseurl }}{% link /assets/diy-music-machines-ableton-live-controller-update/front.jpg %})
![Rear]({{ site.baseurl }}{% link /assets/diy-music-machines-ableton-live-controller-update/rear.jpg %})

<iframe width="560" height="315" src="https://www.youtube.com/embed/m-vPZ5upg-s" frameborder="0" allowfullscreen></iframe>

The video demonstrates the following features:

 * A setup of one master module and one slave module. The slave module is the STM32F0 shown in the [previous post]({{ site.baseurl }}{% link _posts/2016-12-08-diy-music-machines-intro.md %}#ableton-live-midi-controller). The master module is a new revision which uses an STM32F3 CPU. While the F0 is likely powerful enough, the F3 allows me to have more processing power, RAM and flash, all of  which might be useful in the future. [ST](http://www.st.com/en/microcontrollers/stm32-32-bit-arm-cortex-mcus.html) makes it very easy to upgrade between their serieses, as the chips are pin compatible and the peripherals are similar.
 * Automatic parameter mapping: thanks to a custom Remote Script I wrote, no configuration/manual mapping is necessary. Simply selecting a device maps sends it’s parameter names/current values to the controller, and CCs are automatically assigned. This is one of the major highlights of this project.
 * MIDI control of Ableton Live: The encoders send MIDI CC messages to Ableton, changing the value of the mapped parameter.
 * Feedback from Ableton Live: When a parameter on the currently selected device is changed, whether via automation/modulation, by using the mouse, or by using another controller the new value is sent back to the controller.
 * Encoder acceleration: When an encoder is pressed and then rotated the values change faster.

The hardware/mechanical part of this project is almost done, but there is still some work left:
 * The STM32F3 MCU, for whatever reason, does not include a built-in controllable pull-up resistor on the USB D+ line. The STM32F0 and STM32F4 do have this, and I failed to notice the STM32F3 does not. The new (and hopefully last) revision of the board have a controllable one.
 * It occurred to be that both master and slave modules could run the exact same firmware image. For that to work the unit needs to be able to tell on boot time whether it’s a master or a slave unit. While I will likely implement this in software using the options byte, I will add a jumper that controls this in case there are surprises.
 * The laser cut enclosure is slightly too tall, and the cutout for the USB port is too big.

The software still needs work:
 * Get the bootloader working again, and implement master->slave(s) firmware update.
 * Massive cleanups in preparation for open-sourcing all of this.
 * Not hard-coding the number of slaves modules available or their ordering (which module sits left/right to which module).


Shoutouts to [MacroFab](https://macrofab.com/) for once again delivering a professionally made and assembled board for a very reasonable price, and to [Noisebridge](https://noisebridge.net/) for providing people like me with access to their space and tools. Their [laser cutter](https://www.noisebridge.net/wiki/Laser_Cutter) is a thing of beauty!


{% include phi-mailchimp.html %}
