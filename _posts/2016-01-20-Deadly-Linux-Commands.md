---
layout: post
title: Deadly Linux/Unix Commands
---

These commands are highly likely to disrupt the normal functioning of a working Linux/Unix Distros, It is expected from the READER not to try them as they may cause loss to someone else. Please keep in mind these command must be expermented on, for the sake of curosity on virtual machine or an old Linux Box which has no use. 

	mkfs.ext3 /dev/sda

The above command will clean/format/erase all the data named after the mkfs command.

	mv ~ /dev/null 

The above command will clean everything from the root directory as there is no directory named /dev/null

	:(){:|:&};:

The most dangerous command called as Fork Bomb. Once you run this, it only freezes the computer and you will have to warm reboot (from the power button), avoid writing it in ~/.bashrc.

	rm -fr /

This is the simplest and well known by most people. It recursively deletes all files from the root.

	mv /home/* /dev/null

This moves all the user directories in the home directory to an unknown location /dev/null meaning everything in /home directory is deleted.

	mv /home/myhome/* /dev/null

This is just the same as mv /home/* /dev/null but it is limited to the specified user’s home directory. In this case myhome.

	chmod -R 777 /
	
This won’t show any physical effect when run, but for security sake it internally grants read, write and execute rights on every file to every user on that system.

This is just a few deadly commands. I know there will be more out there. Kindly leave yours in the comment box below with a little description of what the command will do.