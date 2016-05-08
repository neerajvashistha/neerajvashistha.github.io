---
layout: post
title: Battery Notification in Ubuntu
---

It's been days since my last post on Free Code Camp, but now I am back, I had lots of ongoing in last few months, was busy with the project, and few other college stuff, lest along I learnt a lot of new stuff and here I am to share with you a quite intersting stuff on how to prevent overcharging and undercharging of your linux box. Though I have kept it simple it's just a notification system right now but I am thinking of improving it to disable charing after certain percentage level.

The notification system in Ubuntu based distro is quite simple just a command `notify-send`  [man page]:https://wiki.ubuntu.com/NotificationDevelopmentGuidelines its quite playful like you could write any script in shell, python, c or c# and make it working or no need of that too just you can say hello world too and a notification will pop on the desktop, like `notify-send "hello world"`

So here is the script that I wrote, which notifies the user that the charing is above 90% and below 30%, for the script to work correctly you must install `acpi` through

  `sudo apt-get install acpi`
  
<script src="https://gist.github.com/neerajvashistha/28351ddd07c9cc9761a0bacb03bc933d.js"></script>

Now for the system to run this contineously one can write a corn tab or just begin a proceess at the startup, in starup application. But if one doesnot have startup application utility create a new file in `~/.config/autostart/` named as `batterynotify.desktop` and add the below lines

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
StartupNotify=false
GenericName=batterynotify
Categories=
Exec=/usr/local/bin/batterynotify.sh
Icon=
Name=batterynotify
Comment=
X-GNOME-Autostart-enabled=true

```
here <b>Exec</b> field gives the path for batterynotify.sh file. Note the above file batterynotify.desktop after creation should be an <b>executable</b>.
