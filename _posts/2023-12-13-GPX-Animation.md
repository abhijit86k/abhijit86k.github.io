---
layout: post
title: Animating GPX Tracks
date: '2023-12-13T07:00:00.000+05:30'
author: Abhijit
categories: Cycling
modified_time: '2023-12-13T13:50:00.000+05:30'
---
I had been struggling to animate / plot GPX files from my rides and commutes.
Strava has Flyby (and Strava Premium now has an animation option);
[Relive.cc](https://www.relive.cc/)  has a nice 3D pan and zoom effect with elevation included, but that does not support multiple tracks.
Last week I was pleasantly surprised to find a fully open source tool for animating GPX tracks called [GPX Animator](https://gpx-animator.app/).
<!--more-->

The setup is surprisingly straightforward - just follow the installation intructions. 
Getting the GPX files themselves was not an issue; I just exported from Strava/RideWithGPS. I also had some tracks in Google Fit, for which simple exports don't work (but that's a rant for another time) - but it is possible to export via Google Takeout and then convert the files to usable GPX tracks using [GOTOES](https://gotoes.org/strava/Combine_GPX_TCX_FIT_Files.php).

Once I had the GPX files, all I had to do was load them into the GPX Animator, set the options, and I had the results!
The workflow is [here](https://youtu.be/matyH6Q0c_A?si=atsTOwkCnPyEDDzF) and the results are [here](https://www.youtube.com/watch?v=SDrV2xOdVpQ&list=WL&index=1).

Here are some notes:

1. The setting for zoom level, viewport an canvas size are a little non-intuitive to me. The way I understood it was that the zoom level defines the tiles that get pulled from the tile server. The zoom level can never change during a video because the tiles are always to one zoom level. The canvas size defines the total extent of the all the tiles that get pulled. So basically if a GPS trace is 10km long and is captured completele in a cavas of WxL pixels, then a 20km long trace will need a canvas that is Wx2L or 2WxL. The viewport defines the portion of the canvas that is in the frame at any instant.

2. The viewport will always be centered on the *last* track.

3. When multiple tracks start at different times, an offset can be added to make all the visualisations "start" at the same time.
