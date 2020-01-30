---
layout: post
title: OpenBSD install to USB stick
date: 2020-01-30 11:35 +0100
categories: update manuals bsd
tags: [openbsd,bsd,qemu,usb]

---

While writing it I am after the procedure covered by this manual but I am not sure it it will work at real hardware. 
Lets get it started.


* Create a KVM machine and install the openBSD to the virtual disk img file

```
mkdir openbsd
cd openbsd/
wget https://cdn.openbsd.org/pub/OpenBSD/6.6/amd64/install66.iso
# I have a 64GB usb sandisk (the real size is a bit less ~ 57GB)
qemu-img create openBSD.img 56G
sudo qemu-system-x86_64  -smp 2 -m 2048 -enable-kvm -usb -hda openBSD.img -cdrom ./install66.iso
```

* After installing the base system I booted it, configureed and added additional software 

```
sudo qemu-system-x86_64  -smp 2 -m 2048 -enable-kvm -usb -hda openBSD.img
```

* At the end I installed it to USB stick 

```
sudo dd if=openBSD.img of=/dev/sdb bs=256k status=progress
```


