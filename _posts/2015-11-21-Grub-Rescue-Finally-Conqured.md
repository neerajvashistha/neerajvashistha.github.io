---
layout: post
title: Grub Rescue Finally Conqured
---

Locate the Ubuntu Partition.

grub rescue> ls

This will display the known drives/partitions.
Drives are designated (hd0), (hd1), etc. Partitions are designated (hd0,1), (hd0,2), (hd1,1), etc
The Ubuntu partition will be one of the (hdX,Y) formatted returns.
If all you get is (hd0) you most likely have a partition table or disk error. Seek assistance elsewhere! (fsck, e2fsck, TestDisk, etc.)

Locate the grub folder.

grub rescue> ls (hd0,1)/boot/grub 

Try each partition (hd0,1), etc. until you find your grub folder
If you don't find the /boot/grub folder, start with a wider search and narrow the search once you find the Ubuntu folders:

grub rescue> ls (hdX,Y)/ 

# Look for the Ubuntu folders, such as lost+found, /bin/, /boot, /home,

grub rescue> ls (hdX,Y)/boot 

# Look for the grub folder.
The grub folder will contain dozens of *.mod files, as well as grub.cfg

Booting From grub-rescue>

If you're in the GRUB rescue shell the commands are different, and you have to load the normal.mod andlinux.mod modules:

grub rescue> set prefix=(hd0,1)/boot/grub
grub rescue> set root=(hd0,1)
grub rescue> insmod normal
grub rescue> normal
grub rescue> insmod linux
grub rescue> linux /boot/vmlinuz-3.13.0-29-generic root=/dev/sda1
grub rescue> initrd /boot/initrd.img-3.13.0-29-generic
grub rescue> boot
Tab-completion should start working after you load both modules.

Making Permanent Repairs

When you have successfully booted your system, run these commands to fix GRUB permanently:

cipher@blackfury-HP-eNVy:~$ update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
cipher@blackfury-HP-eNVy:~$ grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
When you run grub-install remember you're installing it to the boot sector of your hard drive and not to a partition, so do not use a partition number like /dev/sda1.
