---
layout: post
title: D Check on the Toshiba
date: '2023-09-23T23:41:00.004+05:30'
author: Abhijit
tags: hardware electronics
categories: Tech
modified_time: '2023-09-23T23:41:00.004+05:30'
---

I now have two laptops that are >10 years old, both in reasonably good working condition. The Toshiba (purchased in 2013) is quite a beast in terms of performance but let down by a poor design (the display hinge and part of the plastic broke three months after purchase) and somewhat inadequate thermal design.
In the last few months the laptop had started to heat up too much and was probably causing CPU throttling, so it was time for a D-check - completely pull it apart, clean it up and re-apply some fresh heat-sink paste. Took about an hour to do that today and thankfully there is a significant improvement.

Here is the "before"; 10 years of gunk in the heat sink and fan, thermal paste all dried up:

<img src="/images/01-Toshiba.jpg" width="70%">

And after, with the board cleaned up and old thermal compound cleaned up, CPU in the top left, GPU (shiny) middle-right.

<img src="/images/03-Toshiba.jpg" width="70%">

Close-up of the GPU:

<img src="/images/02-Toshiba.jpg" width="70%">

Using Freon and lm-sensors I see the max temperaure in the CPU hovering around 50C (it was about 55C before the cleaning).
Under load the temp goes all the way up to 90C, but comes down very quickly when the test is stopped. Earlier, the temp would go to 90C and then the
CPU was probably getting throttled; it used to take a long time for the temp to come back down.

Stress tested with ```s-tui```. Temp sensors are lm-sensors and freon Gnome addon.



Todo:
- Replace the keyboard (replacement ordered)
- Move to SSD?
