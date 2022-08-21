---
layout: post
title: Reverse Engineering Serial over USB
date: '2022-08-21T17:26:00.000+05:30'
author: Abhijit
categories: EE
tags: hacking foss
modified_time: '2022-08-21T17:26:00.000+05:30'
---

I recently discovered that the GWInstek power supply (GPD-3303D) had a USB-B  connector on the back - which meant it could have some remote monitoring and control features. Sure enough, the [user manual](http://web.archive.org/web/20220821120322/https://www.gwinstek.com/en-global/products/detail/GPD-Series) lists all the serial commands and also has a dedicated windows executable with a GUI for sending the commands.
Unfortunately, when I tried to replicate the commands through minicom, it did not work, leading me down a rabbit-hole of USB/serial debugging.

<!--more-->
<img src="/images/GPD-3303D.jpg" width="30%">

First I wanted to check if the serial settings (Port number, baud rate, number of bits etc.) were all correct.
First off, with the power supply connected over USB, it showed up in ``lsusb`` as a native FT232 device with the expected ``/dev/ttyUSB0`` serial port - meaning that a standard serial interface should work. Also, with Minicom configured as per the manual, powering up the 3303D printed out some standard text about a firmware update - confirming that the settings were also correct. (9600 baud with 1 stop bit, no parity, no flow control). The 3303D has no echo mode - so there is no feedback about whether the device is actually getting any bytes sent to it.

I decided to check with the manufacturer's software, fortunately I had a Windows machine, and that worked. That meant that the problem could be either with the byte sequences, or end-of-line sequence (CR/LF/CRLF), or something else entirely. To figure out what byte sequences were working, I installed USBpcap and Wireshark; and got a dump of the USB transactions as [shown here](https://www.youtube.com/watch?v=0MC-D_oNzbk). Since the data is being sent to the USB, it has more data than just the bytes to be sent on serial.

All USB Data (contains data for all devices - incuding a USB keyboard, mouse etc)

<img src="/images/01-WiresharkAllPackets.PNG" width="100%">

Filtered packets showing only FTDI Data

<img src="/images/01-WiresharkFTDI-Packets.PNG" width="100%">

Filtered packets showing only FTDI Transmit Data (TX)

<img src="/images/01-WiresharkFTDI-TXPacket.PNG" width="100%">

And that clearly shows us:
1. The commands are: ``REMOTE`` (to start the remote session); ``OUT0`` and ``OUT1`` to control the output; etc.
2. Moreover, the end-of-line character is a linefeed (```0x0a```).
3. The software periodically 'talks' on the USB interface to keep the connection 'alive'. If you don't do this you need to start each new set of commands with ``REMOTE``.

##### NOTES:
1. Docklite (Windows only) is a great tool for debugging serial - although the free version has some annoying limitations
2. There is a [python library](https://github.com/akira-okumura/PyGPD3303S/blob/master/gpd3303s.py) as well but I was not able to get it to work and did not have time to debug.
