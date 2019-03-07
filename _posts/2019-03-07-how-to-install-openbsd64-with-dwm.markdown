---
layout: post
title:  "How to install OpenBSD 6.4 with DWM?"
date:   2019-03-07 10:12:00 +0100
categories: update manuals bsd
tags: [tips,manual,dwm,openbsd,openbsd64]
---


Basic installation of the OpenBSD 6.4 is straightforward. For most installer questions you just press Enter. 

When OpenBSD is booted from instalation image, it will start ask questions:

|Question | Answer |
|---------|--------|
|Welcome to the OpenBSD/amd64 6.4 installation program.   |           |
|(I)nstall, (U)pgrade (A)utoinstall or (S)hell ?          | i         |
|Choose your keyboard layout                              | pl        |
|System hostname                                          | openbsd64 |
|Which network interface do you wish to configure? (or 'done') [em0]| Hit Enter |
|IPv4 address for em0? (or 'dhcp' or 'none') [dhcp]       | Hit Enter |
|IPv4 address for em0? (or 'autoconf' or 'none') [none]   | Hit Enter |
|Which network interface do you wish to configure? (or 'done') [done]| Hit Enter |
|Password for root account? (will not echo)               | type your secret password |
|Password for root account? (again)                       | type your secret password |
|Start sshd(8) by default? [yes]                          | Hit Enter |
|Do you expect to run the X Window System? [yes]          | Hit Enter |
|Do you want the the X Window System to be started by xenodm(1)? [no]       | Hit Enter |
|Setup a user? (enter a lower-case loginname, or 'no') [no]       | kowalczy |
|Full Name for user kowalczy? [kowalczy]                  | Hit Enter |
|Password for user kowalczy? (will not echo)              | type your secret password |
|Password for user kowalczy? (again)                      | type your secret password |
|Allow root ssh login? (yes, no, prohibit-password) [no]  | Hit Enter |
|What timezone are you in? ('?'  for list) [Europe/Warsaw]| Hit Enter |
|Available disk are: wd0.                                 |           |
|Which disk is the root disk?  ('?'  for details) [wd0]   | Hit Enter |
|No valid MBR or GPT.                                     |           |
|Use (W)hole disk MBR, whole disk(G)PT or (E)dit? [whole] | Hit Enter |
|Use (A)uto layout, (E)dit auto layout, or create (C)ustom layout [a]| Hit Enter |
|Let's install the sets!                                  |   |
|Location of sets? (cd0 disk http or 'done') [cd0]        | Hit Enter |
|Pathname to the sets? (or 'done') [6.4/amd64]            | Hit Enter |
|Set name(s)? (or 'abort' or 'done') [done]               | Hit Enter |
|Directory does not contain SHA256.sig. Continue whithout verification ? [no]| yes   |
|Location of sets? (cd0 disk http or 'done') [done]       | Hit Enter |
|Exit to (S)hell, (H)alt or (R)eboot? [reboot]            | Hit Enter |

## Resources 

* https://www.bcsatellite.net/OpenBSD-Desktop-HOWTO/
* https://en.wikibooks.org/wiki/Guide_to_Unix/BSD/OpenBSD/As_a_Desktop
* https://wallpapercave.com/openbsd-wallpaper
* https://www.reddit.com/r/unixporn/comments/9d0a1t/dwm_openbsd_suckless_beauty/
* https://www.c0ffee.net/blog/openbsd-on-a-laptop/#initial-configuration
* http://eradman.com/posts/openbsd-workstation.html

* https://www.openbsd.org/faq/ports/ports.html

## Installing additional applications 

```
pkg_add sudo htop i3 nano vim firefox geany 
#pkg_ddd mate-desktop mat-notification-deamon mate-terminal mate-panel mate-session-manager mate-icon-theme mate-control-center mate-calc caja
pkg_add nitrogen 
pkg_add pkglocatedb
pkg_add wget 
wget https://wallpapercave.com/wp/NIPs9fj.jpg


pkg_add dwm dmenu st 



```


* create file .xinitrc

```
xset -b 
setxkbmap pl
#xrdb ~/.Xresources

#exec xrandr --output VGA-0 --mode 1920x975 --rate 60 &
exec nitrogen --restore &
#exec plank & 

while true ; do xsetroot -name "`date '+%Y-%m-%d %H:%M.%S'` Load15: `uptime |awk -F "load" '{print $2}' |cut -d " " -f 5 `; Up: `uptime |cut -d "," -f 1 |awk -F "up" '{print $2}'`"; sleep 1 ; done &

#if you have compton 
#compton -b --config ~/.config/compton.conf & 

exec dwm

```


