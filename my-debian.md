---
layout: page
title: My Debian - LDD Linux
permalink: /my-debian/
---

### Debian manuals and build scripts

![Debian Buster DWM screenshot](/assets/images/debian-buster-dwm-scrot.png)
* [repo at gitlab.com](https://gitlab.com/jacekkowalczyk82/my-debian)
* [Manuals for building Live ISO with Debian Stretch and Buster](https://gitlab.com/jacekkowalczyk82/my-debian/blob/master/debian-stable-readme.md)
* [Configs for Buster](https://gitlab.com/jacekkowalczyk82/my-debian/tree/master/live-build-buster/config)
* [Configs for Stretch](https://gitlab.com/jacekkowalczyk82/my-debian/tree/master/live-build-stretch/config)
* [Basic help and about](https://gitlab.com/jacekkowalczyk82/my-debian/blob/master/live-build-buster/about.md)

### About LDD Linux 

* LDD Linux - Lightweight Debian Distribution is custom Live build of Debian Linux with DWM, Openbox, i3wm, XFCE 
* The goal of this project is to create custom debian live cd image and lightweight OS that can be used on VM or older hardware. 
* [my-debian - LDD Linux at sourceforge.net](https://sourceforge.net/projects/my-debian/)
* [Download latest ISO](https://sourceforge.net/projects/my-debian/files/latest/download)
* [Download files](https://sourceforge.net/projects/my-debian/files/live-buster-dwm-openbox-i3-xfce/)
* To start X session run `startgui` command after login in terminal 

|Feature           |Description                                                                         |
|------------------|------------------------------------------------------------------------------------|
|Livecd user/pass  |user/live                                                                           |
|GUI sessions      |Custom-DWM, Openbox, i3, XFCE                                                       |
|DWM custom ModKey |Win                                                                                 |
|i3wm ModKey       |Win                                                                                 |
|Openbox ModKey    |Win                                                                                 |
|DWM terminal      |ModKey + Shift + Enter (Win + Shift + Enter)                                        |
|DWM Dmenu         |ModKey + p (Win + p)                                                                |
|DWM exit          |ModKey + Shift + q (exits to terminal)                                              |
|i3 exit           |ModKey + Shift + e (exits to terminal)                                              |
|i3 poweroff       |ModKey + Shift + p (shuts down the system)                                          |
|Openbox terminal  |Win + Enter                                                                         |
|Openbox Dmenu     |Alt + F3                                                                            |
|i3wm terminal     |Win + Enter                                                                         |
|i3wm Dmenu        |Win + d                                                                             |
|Network Manager   |nmtui, nm-applet                                                                    |
|Volume Control    |pavucontrol                                                                         |
|Power Manager     |xfce4-power-manager, upower -i /org/freedesktop/UPower/devices/battery_BAT0         |
|WWW browser       |Firefox, rchromiu, falkon                                                           |


* More information/help about dwm can be found at [http://suckless.org](http://suckless.org).




