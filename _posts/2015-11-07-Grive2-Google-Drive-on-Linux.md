---
layout: post
title: Grive2-Google Drive on Linux
---

After a long time I have finally decided to write about whatever I do, so that I can have a copy of whatever awesome things that I usually come across. 
So here it is, In Ubuntu 13.04, I had used Google Drive using grive. But since then I have changed my environment to Pantheon which is usually shipped with [elementary os], and i would say it has blown my mind off. But still it has took a heavy toll on me for installing all the packages and everything, the experience was awesome and i enjoyed it.

The last hurdle I faced was using the Google Drive through grive, after lot of searching on internet pages I finally found what I wanted. The problem with the grive was that it was not maintained and there were no updates and Google had started using  Google Drive REST API to talk to Google Drive service. So the solution which i found on one of the Git Issue [solution](https://github.com/Grive/grive/issues/311) was to use [Grive2](http://yourcmc.ru/wiki/Grive2), which is a great command line utility for sync to Gogle Drive.(Don't Dishearten yourself because its command line).

So let's get started its harldy 23MBytes(dependencies), here I am using debian/ubuntu environment.

First make sure you have all the dependencies installed and ready.

{% highlight bash %}
sudo apt-get install git cmake build-essential libgcrypt11-dev 
sudo apt-get libyajl-dev libboost-all-dev libcurl4-openssl-dev 
sudo apt-get libexpat1-dev libcppunit-dev binutils-dev
{% endhighlight %}

A known problem you may face is for `libboost-all-dev` which can be downloaded separately from [here](http://packages.ubuntu.com/trusty/libboost1.55-all-dev). After downloading and installing libboost-all-dev manualy, make sure you execute the above successfully.

Second, clone the grive2

{% highlight bash %}
git clone https://github.com/vitalif/grive2
{% endhighlight %}

Change the directory to grive2. Now that you are in the source code's “grive2” subdirectory (after 'cd /path/to/yourGriveSourceCodeDir/grive2'), at the prompt type:

{% highlight bash %}
mkdir build
cd build
cmake ..
{% endhighlight %}

1. note the double period (..) as the argument to cmake, to denote the parent directory.
2. You should get a success message like: ”– Build files have been written to: /your/dir”
3. Don't run it with sudo - root access is not needed for building.

Third, At the prompt type:

{% highlight bash %}
make -j4
{% endhighlight %}

You'll get lots of messages & hopefully a success message: ”[100%] Built target grive_executable”. The executable file itself (called “grive”) will be placed in the “grive” subdirectory.
Then install it to the system binary directory (/usr/local/bin by default) by running:

{% highlight bash %}
sudo make install
{% endhighlight %}

### First run
Change to your google drive sync directory, and run `grive -a`:

{% highlight bash %}
cd /home/you/yourGoogleDrive/
grive -a
{% endhighlight %}

-The «-a» option is only needed the very first time you run grive.
Visit the URL that comes up, then post the auth code given (you must have been logged into Google). You should get some messages including «Synchronizing files» … now you are running.
Note: Donot Close the Window of the browser, otherwise the sync will stop.

### Syncs
To sync, you must run the program manually (there is no «real-time watching» yet, but there is a tweak afterall its Linux). At the prompt, type:

{% hightlight bash %}
cd /home/you/yourGoogleDrive/
grive
{% endhighlight %}

### Scheduled Syncs
For Scheduled Syncs/ Automatic Syncs a corn job can be written, which is nothing but an effective way to schedule a routine background job at a specific time and/or day on an on-going basis.
It is written in one these folders: `/etc/cron.daily`, `/etc/cron.hourly`, `/etc/cron.monthly` or `/etc/cron.weekly`. But access of these folder is easily done using the below command.

{% highlight bash %}
crontab -e
{% endhighlight %}

After that only one line is required for creating a schedule for automatic sync after 30 min that is,

{% highlight bash %}
*/30 * * * * cd /home/you/yourGoogleDrive/ && grive # JOB_ID_1
{% endhighlight %}

the format is 

{% highlight bash %}
MIN HOUR DOM MON DOW CMD
{% endhighlight %}

If it is difficult to edit the contab file an alternative is to `gnome-schedule`.  It will provide a powerful GUI to add cron tasks.

{% highlight bash %}
sudo apt-get install gnome-schedule
{% endhighlight %}

thats it, after that your Google Drive will happily Sync with your Linux Box. Now I have started looking for creating an indicator which can be used to provide a visual aid on my panel itself.


