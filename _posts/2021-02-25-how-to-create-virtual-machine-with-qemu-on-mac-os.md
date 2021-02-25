---
layout: post
title: How to create Virtual Machine with Qemu on Mac OS
date: 2021-02-25 16:32 +0100
categories: update manuals macos
tags: [macos,qemu,linux,sparkylinux]
---

In this short tutorial I will present how to create a virtual machine using qemu on Mac OS system. 
I will use [Sparky Linux](https://sparkylinux.org/), Polish Linux distribution based on Debian Testing. 

First lets install required software: 

```
brew install qemu

qemu-system-x86_64 --version

```

Next we need to create a virtual disk for a VM. 

```
mkdir -p ~/vm_sparky/
qemu-img create -f qcow2 ~/vm_sparky/sparky.qcow2 40G

```

We also need to download the installer ISO file and place it to the same directory. 
Once ISO file is downloaded we can start VM:

```
qemu-system-x86_64 \
  -m 4G \
  -vga virtio \
  -display default,show-cursor=on \
  -usb \
  -device usb-tablet \
  -machine type=q35,accel=hvf \
  -smp 2 \
  -cdrom sparkylinux-2020.12-x86_64-xfce.iso \
  -drive file=sparky.qcow2,if=virtio \
  -cpu Nehalem

```

**NOTE**
I am using macbook pro with CPU Intel i7. Most recent i7 Intel processors have a codename Nehalem. 

When the operating systrem is installed inside Qemu VM, you can shutdown it. 

Normal startup without install CD can be done with command:

```
qemu-system-x86_64 \
  -m 4G \
  -vga virtio \
  -display default,show-cursor=on \
  -usb \
  -device usb-tablet \
  -machine type=q35,accel=hvf \
  -smp 2 \
  -drive file=sparky.qcow2,if=virtio \
  -device e1000,netdev=net0 \
  -netdev user,id=net0,hostfwd=tcp::2222-:22  \
  -cpu Nehalem
``` 

The command for start is modified with arguments for forwarding localhost port 2222 to quest port 22 for ssh connection. 


