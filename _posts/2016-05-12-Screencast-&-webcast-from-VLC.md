---
layout: post
title: Screencast & Webcast from VLC
---

Haa!! finally conqured!. There are thousand of videos on youtube where the presenter is either behind the screen explaining himself or inset within the screen. for example 

![Screencast+Webcast]({{ site.url }}/files/screenshot.png "Screencast+Webcast")

But the question arisis how does one do it with stretching himself to th length of going on installing tons of applications and understanding how do they work, though there are some like Camstudio, Camtasia, but even they require some installation. A key fact  of understanding is current configration of our laptop (if one uses VLC) is built to record screen from web cam and audio all at the same time. Seems pretty intersting isn't it? so how does one go about doing it? Well the answer is simple, write a simple bash script with opens VLC and records the correct thing at correct audio with a correct frame rate. That's it.

<script src="https://gist.github.com/neerajvashistha/2c7c7a7bcc01c5723f511b714ec946e3.js"></script>

And the script will exectute as shown below.

![exection_of_bash]({{ site.url }}/files/out2.gif "In Action")

There would be some cases where it will not record the audio, if that is the case then exec `arecord -l` and replace `input-slave=alsa://hw:x,y` where `x` denotes card number and `y` denotes device number.

```
cipher@blackfury-HP-eNVy:~/exp$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: 92HD91BXX Analog [92HD91BXX Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
##Update

This is update is about recording screen and the audio from built-in speaker like if you want to record a live show from webseminar or a tv-video show.

<script src="https://gist.github.com/neerajvashistha/8aad9ce90897de4ff1e7230f1774ea64.js"></script>

For the above script to work correctly, check your ".pci-.." value in "pulse://alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" from VLC, View > Playlist > Audio capture > Monitor Built-in Audio stereo > Information.
