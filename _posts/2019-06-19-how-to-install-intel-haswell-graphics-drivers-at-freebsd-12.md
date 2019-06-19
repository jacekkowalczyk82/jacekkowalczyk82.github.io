---
layout: post
title: How to install Intel Haswell Graphics drivers at FreeBSD 12?
date: 2019-06-19 13:53 +0200
categories: update manuals linux
tags: [freebsd,bsd,intel,hd,haswell,graphics,i915,thinkpad,x240]

---


When I installed FreeBSD 12 at my Thinkpad X240 few months ago, the support for Intel graphics was already in OS. I did not need to install any packages. 
Recently something changed and Xorg started crashing at with my standard configs in `/etc/rc.conf`:

```
kld_list="i915kms"
``` 

I found forum thread related to this issue: [Xorg crash at FreeBSD 12 with Intel Haswell](https://forums.freebsd.org/threads/xorg-crash.70744/)

## The solution is quite easy

* First we need to install `drm-kmod` from package of ports. 

```
sudo pkg install drm-kmod
```

* Secondly, enable loading of his intel graphics kernel module on startup. To to this edit the file `/etc/rc.conf` and set:

```
kld_list="/boot/modules/i915kms.ko"
```

* and reboot the system 

