---
layout: post
title: Multithreaded DOS Attack!
---

Has it happened that you are in LAN and some guys are connected to your Network and utilising entire bandwidth?
Its very common problem that you want to work and search web or push to git but due to network issues you are unable to do so. This issue was constantly irratiating me over the last couple of days working 
on a very exciting project but was unable to continue due such a$$-h013s. So, one day i decided to go to their level and kick them out of my network, making them taste their own medicine. Of-course this is no counterstrike that you can kick your combatants out due to their non performance but this was more than that, they will stop using the network and they will switch, or realise their predator has come:-p

I had in my second year of engineering written a small code to send small packets(TCP/UDP/raw) to a reciever IP. This struck me! if I can send a multitude of large packets continulsy to an IP on port 80 that will vitually block them to use the internet!. This was the inspiration.

Find all the IPs on my network using nmap utility and once that are found flood them! using multithreaded apprach. That's it!.

<script src="https://gist.github.com/neerajvashistha/2ecde01011a42e05d804acce83674971.js"></script>


Change `192.168.1.x` where ever its written according to your Network and install `nmap` first!! haven't tried on Windows though it should work.. But be careful it does leaves traces of your IP bomabarding the network you will easily be caught:-). Its upon you how you use it, use this wisely.
