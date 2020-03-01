---
layout: post
title: 'DWM window manager with gaps '
date: 2020-02-28 10:32 +0100
categories: update manuals linux
tags: [linux,debian,bsd,freebsd,dwm,suckless-tools]
---

> dwm is a dynamic window manager for X. It manages windows in tiled, monocle and floating layouts. All of the layouts can be applied dynamically, optimising the environment for the application in use and the task performed. 
> from https://dwm.suckless.org/

Today I visited DWM project page at http://suckless.org and checked their patches for DWM. I downloaded gaps patch but I couldn't apply it directly because of the version mismatch. I made the same changes manually, and I added something from myself. 

![dwm-gaps-debian](/assets/images/dwm-gaps-2020-02-28-083029_1920x899_scrot.png)

You can check my patch for Debian here: [DWM 6.2 with gaps patch for Debian](https://gitlab.com/jacekkowalczyk82/my-debian/-/blob/master/suckless.org/dwm-gaps/0001-DWM-gaps-and-Windows-Mod-Key.patch)

I made also similar patch for FreeBSD: 
[DWM 6.2 with gaps patch for FreeBSD](https://gitlab.com/jacekkowalczyk82/freebsd/-/blob/master/customizations/dwm/0001-FreeBSD-DWM-with-GAPS-and-Win-Mod-Key.patch)

![fDWM-with_gaps-at-freeBSD](/assets/images/dwm-gaps-bsd-2020-02-28-092248_1920x899_scrot.png)

I also built new custom ISO of my LDD Linux with MATE desktop and Ultra edition and tof course his custom DWM with gaps. 

New MATE edition ISO image is published to [LDD linux MATE edition files](https://sourceforge.net/projects/my-debian/files/live-buster-dwm-openbox-i3-mate/)
The file name is: debian-live-10-ldd-mate-2020-02-28_094308-amd64.iso

New Ultra Edition ISO image will be published (I hope today) to  [LDD linux Ultra edition files](https://sourceforge.net/projects/my-debian/files/live-buster-dwm-ultra/)


