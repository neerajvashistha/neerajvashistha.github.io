---
layout: post
title: Ubuntu Wallpaper Changer
---

This question was their in my head for a long time, and now i have finally sorted it out. Oops! I forget to tell you about my question, How does one can change desktop wallpaper without using any third party resource like [variety]. Now that I have finally figured it out that how does it takes place, i have written a beautiful script in shell to do so, which not only changes the wallpaper at certain time but also downloads the wallpaper in a specific directory. 

[variety]:http://peterlevi.com/variety/

The reason I am switching my self from any third party resource is the memory consumption is far too high, also it gives me better control of what is being downloaded and where and how. In the script I have also added notify-send too, that is because I like the <b>fortune</b> being provided as pop-ups every then and now. 

So, here is the script

<script src="https://gist.github.com/neerajvashistha/1df62e912bb437ee06651d188c2a0f56.js"></script>

If you want to try and test it please change, DIR variable and uncomment line 28,32,38,42. You can start the script by creating a .desktop (as described [here]) file to your autostart directory in ~/.config/autostart .

[here]:http://neerajvashistha.github.io/blog/2016/05/08/battery-notification
