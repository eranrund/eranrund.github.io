---
layout: post
title:  "DIY Music Machines - Mixer/Traktor contoller and 4-ch Audio Interface"
description: "DIY Music Machines - Mixer/Traktor contoller and 4-ch Audio Interface"
tags: [electronics, phi]
date: 2017-07-13 22:35:00 -0700
excerpt_separator: <!--more-->
---


Lots of progress on two parts of this project has happened in the last few months. I have a working prototype of the Traktor/mixer controller, with 3 fully operational channels and good Traktor integration as well as a USB 4ch (two stereo pairs) audio interface. They are not integrated yet but that will happen sometime after Burning Man.

## Introducing Hyperion - Traktor controller/mixer module

After months of work I finally have a device I can use as a fully-functional DJ controller (still missing the audio interface). Pictured below is the prototype, showing three [Hyperion](https://github.com/pulsar-heavy-industries/phi/tree/master/hyperion) modules and one [Cenx4](https://github.com/pulsar-heavy-industries/phi/tree/master/cenx4) module. The Cenx4 is currently a placeholder until I create a "master" module that integrates with the audio interface shown below.

![Proof of concept of 3xHyperion and 1xCenx4]({{ site.baseurl }}{% link /assets/diy-music-machines-mixer-and-audio-interface/phi-3-hyperions.jpg %})

Each channel strip gives me control of gain, EQ (3 or 4 bands with knobs to spare), simple looping, cueing, filter, fader... and I haven't even mapped all the controls :)
The Cenx4 module allows switching between 3 layers:
1. The default layer where the buttons in each strip are used to control effects/filter/etc.
2. A browse mode that lets the user navigate Traktor's browser, play tracks in the preview player and load tracks into the decks.
3. A cue mode that lets the user select cue points, cue/pause, jump, etc.

More details to follow. Source code and schematics are available in the [Pulsar Heavy Industries repo](https://github.com/pulsar-heavy-industries/phi/).

## Introducing Narvi - 4ch Audio Interface module

What do we currently have?
* 2 channels: Balanced outputs + line level outputs using TI's "Higest Performance" [PCM1792A](http://www.ti.com/product/PCM1792A) DAC. Output stage consists of the high-performance [OPA1632](http://www.ti.com/lit/ds/symlink/opa1632.pdf) op-amp.
* 2 channels: Headphones output using TI's [PCM5102A](http://www.ti.com/product/PCM5102A) DAC.
* Both DACs are receiving 24 bit audio over USB, powered by an [STM32F429](http://www.st.com/en/microcontrollers/stm32f429-439.html) microcontroller.
* USB asynchronous sample rate feedback provided by using a timer to measure MCK.
* MIDI input, MIDI output.
* Many supply rails created from an external +12V supply (+5V for powering modules - would be used in a non-standalone configuration), +/-15V regulated down to +/-12V for the analog output stage, +5V for the DACs, as well as +3.3V
* Modular design: A DAC+Power supply board and a CPU board.

What's missing?
* Hardware: The stand-alone audio interface will have a simple character LCD + two rotatry encoders to control it. Boards have been ordered but not shipped yet.
* Software: Need to fix a bunch of bugs, create bootloader, add LCD support.
* Need to measure performance with an audio analyzer.
* Need to cleanup and release code + schematics (work being done in [this](https://github.com/pulsar-heavy-industries/phi/tree/narvi-v0/narvi) branch at the moment.

![Narvi Enclosure Front]({{ site.baseurl }}{% link /assets/diy-music-machines-mixer-and-audio-interface/phi-4ch-enclosure-front.jpg %})
![Narvi Enclosure Rear]({{ site.baseurl }}{% link /assets/diy-music-machines-mixer-and-audio-interface/phi-4ch-enclosure-rear.jpg %})
![Narvi Enclosure Side]({{ site.baseurl }}{% link /assets/diy-music-machines-mixer-and-audio-interface/phi-4ch-enclosure-side.jpg %})
![Narvi Inside 1]({{ site.baseurl }}{% link /assets/diy-music-machines-mixer-and-audio-interface/phi-4ch-inside-1.jpg %})
![Narvi Inside 2]({{ site.baseurl }}{% link /assets/diy-music-machines-mixer-and-audio-interface/phi-4ch-inside-2.jpg %})
![Narvi Inside 3]({{ site.baseurl }}{% link /assets/diy-music-machines-mixer-and-audio-interface/phi-4ch-inside-3.jpg %})

{% include phi-mailchimp.html %}
