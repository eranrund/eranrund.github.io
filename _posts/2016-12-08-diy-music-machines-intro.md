---
layout: post
title:  "DIY Music Machines - Introduction"
tags: [electronics]
date: 2016-12-08 00:40:00 -0700
excerpt_separator: <!--more-->
---

## Intro

Music has always been a significant and influential part of my life. I have been listening to music from as far back as I can remember myself. Like most people my musical taste has changed throughout the year, but my affection towards electronic music, and particularly Techno remained pretty consistent. When I was a teenager I became interested in [DJing](http://keves.org/), and continued doing that for many years. In addition to the musical and party/cultural aspects of DJing, I was attracted to the technical aspect of it - and of music production in general. Producing music, or remixing other people’s music, is done using tools. As it happens in the Electronic music world, those tools happen to be, well, electronic - which was and still is a passion of mine. For whatever reasons (one, notably being spending many hours in front of a computer screen as it is), I wanted to keep my musical hobby separated from my computers hobby. That meant using vinyls to DJ (gave up eventually and switched to digital), and attempting to produce music using anything but a personal computer (I say “personal computer” because, of course, many of the machines I used throughout the years had computers in them). I never took the music production part [seriously](https://soundcloud.com/eranrund), and even today I only toy with the drum machines, sequencers and synthesizers that I own. At some point in life I learnt enough software and electronics to be able to build those things on my own, and I find that very exciting. This intersection between music and technology facinates me. It helps that there are plenty of people around the world doing exactly the same - for example, and these are just the tip of the iceberg: [MIDIbox](http://ucapps.de/), [Axoloti](http://www.axoloti.com/), [Mutable Instruments](http://mutable-instruments.net/shruthi1), [x0xb0x](http://www.ladyada.net/make/x0xb0x/), and the list goes on and on. Throughout the years I started many projects of this nature and never completed most of them, a lot of time due to lack of time and money, or simply not enough sustained interest. After enough iterations on various prototypes that never led to any usable devices, I feel like I have matured enough to start completing some projects, and making my contribution to the DIY music maker community.

In the last few months I have been working on a modular audio/MIDI platform that currently consists of three projects going in parallel, having some shared infrastructure. They are detailed below and the purpose of this post is to introduce them. They currently do not have a catchy name, but that is on the never-ending TODO list.

## Ableton Live MIDI controller

![UI Board]({{ site.baseurl }}/assets/diy-music-machines-intro/rotenc-ctrl-board-small.png)

A higher resolution image is available [here]({{ site.baseurl }}assets/diy-music-machines-intro/rotenc-ctrl-board-large.jpg) as well as a [(crappy) video](https://youtu.be/LIjwVPmGKmk).

The controller I am envisioning is somewhat similar to a modular version of the [Behringer BCR2000](http://www.synthtopia.com/content/2005/01/27/behringer-bcr2000-usb-midi-controller-review/), but with OLED displays instead of LED rings. While LED rings gained popularity a few years ago as a way to provide visual feedback for rotary encoder positioning, they still require the user to either memorize what each pot is mapped to, or to constantly go back and forth between the controller and the computer screen. Since I am trying to avoid looking at the screen while toying with music, and do not like memorizing things (especially given different mappings per project/device/etc), I find the idea of having rotary encoders paired with a display of both value/position and assignment very appealing and elegant. The module pictured above uses an [STM32F0 MCU](http://www.st.com/en/microcontrollers/stm32f0-series.html?querycriteria=productId=SS1574), and offers [CAN-Bus](https://en.wikipedia.org/wiki/CAN_bus) connectivity. The idea is to have a few of these next to each other, and have them dynamically mapped to selected device(s) in Ableton Live using Ableton’s Remote Scripts.

While this is not revolutionary, it will serve as a base for far more advanced controllers. The main objectives for this project are:

 * A functioning ‘main’ controller board, bridging between the CAN-Bus network and Ableton Live (or any MIDI-capable instrument) through either traditional MIDI connectivity or MIDI over USB. This main controller will support firmware upgrades of both itself and the devices on the CAN network, done over MIDI and requiring no specialized host support.
 * Ableton Live Remote Script integration, meaning the controller can be used with Live without any custom configuration.
 * A web application for some configuration not directly possible via Ableton for those who want that (such as display settings, firmware updates, channel editing, etc), or plain old MIDI map editing for use with other MIDI devices. This web application is made possible thanks to [Web MIDI API](https://webaudio.github.io/web-midi-api/), which I feel like not enough people in this space are leveraging.


## Traktor DJ Controller/Mixer Controller

I love [Traktor](https://www.native-instruments.com/en/products/traktor/). It is truly a wonderful DJing software, and it is what sealed the deal on me fully transitioning away from vinyls. I’ve wanted my own custom controller for it for a while, and here is the current design for a channel strip - which exposes enough controls to make it fit for both Traktor usage or any kind of MIDI controllable mixer:

![Board design]({{ site.baseurl }}/assets/diy-music-machines-intro/ch-strip-brd.png)
![3D rendering]({{ site.baseurl }}/assets/diy-music-machines-intro/ch-strip-3d.png)

This project lays on the foundations being built by the simpler controller described above, but most notably adds a 4 channel USB audio interface, to provide a complete integrated solution for DJing. To my knowledge this does not currently exist in the DIY world.


## Digital Synthesizer/Sampler/who knows?

Well, if we have the ability to connect UI modules, deal with MIDI and stream USB audio, why not move the audio generation part away from the computer as well?
I haven’t given this much thought yet, but I do have a working prototype of something that vaguely resembles a TB-303 and I plan on using that as the basis for a simple standalone synthesizer.


## Where am I today?

Software:

 * 4 channel 24-bit/48KHz USB audio into 2 channel DAC (software selects which of the 4 channels gets sent to the DAC).
 * A custom and reliable CAN-Bus packeting protocol (because CAN-Bus messages are limited to 8 bytes of data and that’s not enough).
 * CAN-Bus and USB-MIDI bootloaders.
 * Web application for firmware updates.
 * Preliminary sound synthesis code.


Hardware:

 * The 4 roatary encoder/2 OLEDs UI board for the basic controller interface pictured above works. I will be manufacturing a few more of those in the near future.
 * The first revision of the Traktor controller channel strip is ready to be sent to the fab.
 * The first revision of a custom high-end DAC ([PCM4104](http://www.ti.com/product/PCM4104)) evaluation board is ready to be sent to the fab.


None of this would have been possible without the following (or would have been much more time consuming and annoying):

 * [ChibiOS](http://www.chibios.org/) - this open-source embedded operating system had proved to be rock solid and super friendly to use. I am used to the Embedded Software world being a complete disaster, but this project caught me off guard. Everything just works, is well documented, and has a great support community to the extent that I could Google my way around many issues I have encountered.
 * [uGFX](http://ugfx.io/) - this is the current graphics library I am using. Like ChibiOS, it Just Works, and have wasted very little of my time in trying to do what I wanted to do.
 * [MacroFab](https://macrofab.com/) - Last but most definitely not least, an affordable PCB manufacturing turnkey provider. These people fabricate the PCB for you, source the components, assemble them and mail you the complete thing without requiring a loan and with a very friendly web interface. Gone are the days of dealing with Gerbers (although to be honest OSH Park put an end to that dark era a while ago), Mouser/DigiKey carts, stencils, hand soldering. They even accept quantities as low as 1!


Note that the code is currently a huge mess, and as such I am keeping it in a private repository. Feel free to [contact](mailto:eran@rundste.in) me if you are interested in any of this.
