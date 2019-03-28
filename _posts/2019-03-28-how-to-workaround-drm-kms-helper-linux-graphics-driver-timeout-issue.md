---
layout: post
title: How to workaround drm_kms_helper linux graphics driver timeout issue
date: 2019-03-28 13:48 +0100
categories: update manuals linux 
tags: [tips,tricks,linux drm_kms,graphics,grub]

---


Over year ago I was struggling with the annoying issue at linuxes. I experienced it at many distributions and it turned out to be related to Linux - kernel, and the graphics drivers. 

```
[drm:drm_atomic_helper_commit_cleanup_done [drm_kms_helper]] *ERROR* [CRTC:26:pipe A] flip_done timed out 
```

![drm_kms_helper_issue](/assets/images/drm_kms_issue.png)

This issue was causing that the machine was booting endlessly - many minues over the expected seconds. 


The solution is to edit the file `/etc/default/grub` and modify the entry from: 
`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"`	
to: `GRUB_CMDLINE_LINUX_DEFAULT="video=SVIDEO-1:d"`

Removing options: `quiet splash` turns on boot logs instead of the splashscreen, and now I can know what is going on with boot of my linux box. 

Additionally I modified from:
`GRUB_TIMEOUT_STYLE=menu` to `GRUB_TIMEOUT_STYLE=menu` 
The last modification is enabling grub menu to be always visible at boot time. 


Next I needed to run command: 

```
sudo update-grub
```

and reboot the computer. 

