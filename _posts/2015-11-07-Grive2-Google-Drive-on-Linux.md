---
layout: post
title: Grive2 Google Drive on Linux
---

After a long time I have finally decided to write about whatever I do, so that i can have a copy of whatever awesome things that i usually come across. 
So here it is, In Ubuntu 13.04, I had used Google Drive using grive. But since then i have changed my environment to Pantheon which is usually shipped with [elementary os], and i would say it has blown my mind off. But still it has took a heavy toll on me for installing all the packages and everything, the experience was awesome and i enjoyed it.

The last hurdle I faced was using the Google Drive through grive, after lot of searching on internet pages i finally found what i wanted. The problem with the grive was that it was not maintained and there were no updates and Google had started using  Google Drive REST API to talk to Google Drive service. So the solution which i found on one of the Git Issue [solution](https://github.com/Grive/grive/issues/311) was to use [Grive2](http://yourcmc.ru/wiki/Grive2), which is a great command line utility for sync to Gogle Drive.(Don't Dishearten yourself because its command line).

So let's get started its harldy 23MBytes(dependencies), here I am using debian/ubuntu environment.

First make sure you have all the dependencies installed and ready.

{% hightlight bash %}
sudo apt-get install git cmake build-essential libgcrypt11-dev 
sudo apt-get libyajl-dev libboost-all-dev libcurl4-openssl-dev 
sudo apt-get libexpat1-dev libcppunit-dev binutils-dev
{% endhighlight %}

A known problem you may face is for `libboost-all-dev` which can be downloaded separately from [here](http://packages.ubuntu.com/trusty/libboost1.55-all-dev). After downloading and installing libboost-all-dev manualy, make sure you execute the above successfully.
