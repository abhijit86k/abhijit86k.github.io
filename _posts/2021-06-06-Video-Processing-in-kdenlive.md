#### Draft
Captured a timelapse of some clouds rolling in today. Partly taken as a timelapse (internal intervalometer on A6400) and the remaining using S&Q mode.
All clips have same lens, focal length and exposure settings, *BUT*: the photos are obv. 4:3 and the video is 16:9. Final processing on kdenlive, which is a
fantastic and powerful video editor for Linux.

1. Take the JPGs and roll them into a MP4 using ffmpeg: `ffmpeg -framerate 25 -pattern_type glob -i '*.jpg' -c:v libx264 -r 25 -pix_fmt yuv420p -s 1920x1440 out.mp4`
  1.  Set output resolution size correctly, else it will give you a video with 24mp frame
  2.  Globbing gives painless way to not worry about file numbering
2. Load up all the clips into KDENlive, set project setting to match that of most/largest clips. this way not much encoding effort is needed.
3. Resize the 4:3 clip into the 16:9 format using the "Position and Zoom" effect. I did this mostly by trial and error - need to figure out a proper way to find
the scaling and offset value. *Tip: select the "Distort" checkbox*.
4. Apply a LUT. My original footage was not recorded in slog, as I am now regretfully realizing. So not much scope for adjustment.
Plus conditions were quite difficult too - bright sky with clouds, relatively very dark foreground - no ND/ graded filter. :(
Even with base ISO100 and f/13 I could not get the shutter speed anywhere near the 1s frame intergval, hence the choppy trees :( :(

Result:  https://youtu.be/wabYY_EJJmk
