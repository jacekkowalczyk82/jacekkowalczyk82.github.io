---
layout: post
title: Setup OpenBSD at thinkpad x240
date: 2020-10-21 22:24 +0200
categories: update manuals bsd
tags: [openbsd,bsd,x240,thinkpad,laptop]
---

![OpenBSD with MATE](/assets/images/openbsd_mate_2020-10-15-140558_1366x768_scrot.png)

This post will show how to configure the OpenBSD at laptop, in my case it is Lenovo ThinkPad x240. 
I will not describe the install process of the base OpenBSD as it is basically quite simple process. Users need to jus follow the install wizard ans ask questions. 
Some old notes related to the installation of base OpenBSD can be found in this [old post](/update/manuals/bsd/2019/03/07/how-to-install-openbsd64-with-dwm.html)

Here I will focus on my way to OpenBSD and the configuration of this system at my laptop. 

## My way to OpenBSD

When I started interesting in BSD system few years ago, I started with FreeBSD 10.4 at VirtualBox. It tooka me quite long to try it on bare metal ThinkPad x240.  
Since that time I started to earn more about BSD system, I installed many of them at VMs. 
In mamy places I found information that OpenBSD is one of the best BSD systems if you want it to run on laptop. 

My first attempt was the USB stick with OpenBSD 6.6. The blog post about it is [here](/update/manuals/bsd/2020/01/30/openbsd-install-to-usb-stick.html)

Few weeks ago I bought Lenovo ThinkCenter m92 and as I wanted to try OpenBSD on bare metal I installed it there. 
It was running without any issues, but the purpose of that machine was a backup server and for the FreeBSD was better, so I installed the FreBSD 12.1 on it. 

Few days later I decided that I will install OpenBSD 6.7 and replace FreeBSD 12.1 at my Lenovo ThinkPad x240. 

Yesterday I did an upgrade to OpenBSD 6.8 and I love it. Everything is so easy here. 

## Prepare USB stick (just in case you are looking for how to )

```
sudo dd if=install67.fs of=/dev/sda bs=1m

# for OpenBSD 6.8 it will be 
sudo dd if=install68.img of=/dev/sda bs=1m

```

## Post install steps / configuration of OpenBSD at x240


* Install pase packages 

```
su -
pkg_add sudo git nano mc rsync 

```

* Edit `/etc/sudoers`  and uncomment:

```
%wheel  ALL=(ALL) SETENV: ALL
```

* Add to `.profile` file

```
export ENV=$HOME/.kshrc
```

* Create `~/.kshrc` file:

```
. /etc/ksh.kshrc

HISTFILE="$HOME/.ksh_history"
HISTSIZE=5000
```

* Install Firmware 

```
sudo fw_update -a

```


* Create file `/etc/hostname.iwm0` with WiFi configuration

```
join <MY_SSID>_5G wpakey <MY_SECRET_PIN>
join <MY_SSID> wpakey <MY_SECRET_PIN>
join <MY_SSID>_EXT wpakey <MY_SECRET_PIN>
join <MY_SSID>_5G_EXT wpakey <MY_SECRET_PIN>

dhcp
```

* Connect to wifi 

```
sudo ifconfig iwm0 nwid <SSID> wpakey <SECRET>
sudo dhclient iwm0
```

* Install GUI packages 

```
sudo pkg_add mate-desktop mate-notification-daemon mate-terminal mate-panel mate-session-manager mate-icon-theme mate-control-center mate-calc caja pluma  
sudo pkg_add mate eom 
sudo pkg_add dbus

sudo pkg_add chromium firefox

```

* Edit file `/etc/rc.conf.local`

```
xenodm_flags=
pkg_scripts="dbus_daemon avahi_daemon"
dbus_enable=YES
```

* Edit `/etc/X11/xenodm/Xsetup_0` and comment all and set 

```
xset b off

```

* Create .xinitrc file

```
exec mate-session

```

* Link .xsesion to .xinitrc

```
ln -s .xinitrc .xsession
```

* `sudo reboot`


## Install DWM 

![OpenBSD with DWM](/assets/images/openbsd_dwm_2020-10-09-102845_1366x768_scrot.png)

* Packages 

```
sudo pkg_add dwm st dmenu neofetch nitrogen scrot compton

```

* Configure `.xinitrc` file

```
## DWM 
xset -b 
setxkbmap pl 

#exec xrandr -s 1280x720 & 
exec nitrogen --restore & 
exec compton -b & 

while true ; do xsetroot -name "`date '+%Y-%m-%d %H:%M.%S'` Load15: `uptime |awk -F "load" '{print $2}' |cut -d " " -f 5 `; Up: `uptime |cut -d "," -f 1 |awk -F "up" '{print $2}'`"; sleep 1; done & 

exec dwm 

```

## Applications that I use

```
sudo pkg_add roxterm rxvt-unicode geany kompare

```

