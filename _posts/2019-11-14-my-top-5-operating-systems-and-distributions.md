---
layout: post
title: My Top 5 Operating Systems and Distributions
date: 2019-11-14 14:39 +0100
categories: update bsd linux
tags: [freebsd,bsd,linux,tools,debian,fedora,ubuntu,mint,mx, mxlinux, arch]

---
 
Many times I was watching youtube films and reading web articles titled: Top 5 /10 Linux Distributions, or what is the best Linux Distribution. 
After spending many hours on installing them to VirtualBox machines (some to real hardware), testing, using, customizing, building my own custom ISO images, Now I can say and write what I think about it and and what are my Top Operating Systems. 
I use term Operating System as I will not touch only Linux Distributions but also BSD systems. I will write here a bit also about Desktop Environments and Window Managers. 

**What is important for me?** 

* Stability
* Stability
* Stability
* How easy to maintain


## This is my **Top 5** list that I can recommend

but I will not order it because some one them are god for beginners and some only for experts. 

### FreeBSD, GhostBSD, FuryBSD 

FreeBSD is stable OS but not easy for beginers. Recenly I updated my Lenovo ThinkPad x240 to FreeBSD 12.1 Release and I must say it was very very easy. GhosteBSD is a bit easier as it provides Live ISO installer for beginner users. 

### Ubuntu and Linux Mint Family (XFCE, Mate)

It is very stable OS. It is probably the most popular linux distribution in the world as desktop but also as server. My Lenovo ThinkPad R61 is running Linux Mint XFCE edition as it provides configured stable and light system out of the box. 
There are some tools to create a custom ISO. I added some manual at [my-buntu github repo](https://github.com/jacekkowalczyk82/my-buntu)

### Debian (XFCE, KDE, Mate, DWM, Openbox, i3), Kali Linux (XFCE, DWM, Openbox, i3)

It is very stable OS. With Lightweight desktops I can run it from USB stick as Live image almost any hardware. It requires a bit more experience than distributions from Ubuntu family. Right now, I am using it mostly on Virtualbox machines and as Live ISO, but I was running it also on my ThinkPad R61 in the past. 
Live-build tools allow to create custom ISO images. You can read about it: in this [blog post](/update/manuals/linux/2019/05/29/how-to-create-a-custom-debian-iso-with-dwm.html), at [my-debian page](/my-debian/), at [my-kali-linux page](/my-kali-linux/). 

### MX Linux (XFCE only)

It is very stable OS, debian based but without systemd. It is lightweight (XFCE) and provides similar experiance as Linux Mint XFCE. Right now, I am using it mostly on Virtualbox machines and as Live ISO, but I was running it also on my ThinkPad R61 in the past. 
MX Linux provides its own Snapshot tool that can be used for creating custom ISO installer image or backup ISO image. 

### Fedora (XFCE, MATE, DWM)

It is very stable OS. With lightweight desktops (XFCE, MATE, DWM) I am using it on Virtualbox machines and as Live ISO. I have never tried it on real hardware but I hope I will try. 
Using spin-kickstarts I can build my own custom ISO. In my [fedora-dwm-custom github repo](https://github.com/jacekkowalczyk82/fedora-dwm-custom) you can find build scripts and mu configurations for my Fedora editions (XFCE + DWM, KDE + DWM, DWM ultra light). 


## My Favourite Desktop Environments and Window Managers

* XFCE
* KDE
* DWM
* Openbox
* i3wm

I do not recommend Gnome as it consumes too much resources and causes system not responsive. I know, latest versions of Gnome are much more responsive than it was few months ago but still are not as fast and light as XFCE. 

## You do not need rolling distribution 

**Why I do not recommend rolling distributions like Arch or OpenSUSE Tumbleweed?**

* unstable
* unstable 
* unstable 

I was using Manjaro i3 edition for over one year and it was good time but I spent too much time on fixing my system instead of just doing my "work". I created a custom ISO image of Manjaro and Arch but I did it as experiment and for learning. 
[Some notes about custom Arch ISO](/my-arch/). 

I was also playing with Kali Linux which in my opinion is the only stable Rolling linux distribution. More about it [here](/my-kali-linux/). 

**Why you do not need rolling distribution?** 

* Most of the systems I listed here provides easier or more difficult way of upgrading to the new release.
* You can easily ans fast do a fresh install of any of these systems. 
* On real hardware I am creating a data partition which I am using for keeping my documents and other files.
* Before fresh install I do backups of files that are not on the data partition (for example user home directory). 

This way I can have up to date any of these systems. 
