---
layout: post
title: HPLIP Binary Plugin Installation
date: '2016-02-05T10:48:00.001+05:30'
author: Abhijit Kshirsagar
tags: foss hacking
category: CS
modified_time: '2016-02-05T10:48:35.025+05:30'
---

Recently, I ran into [this exact bug](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=605589#40&nbsp;) with my junk laserjet printer P1108.
```
Package: hplip
Version: 3.13.4-1
Followup-For: Bug #605589
```

Since the update to 3.13.4 I cannot seem to print with my P1005. When sending a job to the printer, a window pops up asking to install theplugin. When following the dialogs, they end saying that the plugin isinstalled, followed by another window saying it failed. Manually launching hp-plugin completes the plugin installation successfully,the printer comes alive, but sending a print job goes back to requesting theplugin.

The solution is [here](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=605589#50)

Briefly:
1. Create the directory /var/lib/hp
2. Update hplip-gui
3. Install/update cups-pk-helper if required
4. Unplug, then re-plug in printer
5. HPLip will ask to download and install the plugin, which is a run file.


If you are behind a firewall or your internet connection is dodgy, this automatic download will fail, and you will need to manually download and install the plugin:
1. In a terminal run hp-plugin
2. Watch the terminal for URL of the plugin file. Download *.run file from hplip website.
