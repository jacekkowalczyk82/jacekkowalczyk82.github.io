---
layout: post
title: How to create USB stick with Kali Linux and persistence
date: 2021-02-25 11:22 +0100
categories: update manuals linux
tags: [kali,linux,live,usb,thinkpad,laptop]
---

In this tutorial I am going to show how to install Live Kali linux on USB stick with persistence.

I have got 16GB SanDisk Cruzer Fit USB stick. 

I use Balena Etcher to install live kali image to USB stick. 

Next I need to create and configure the persistence partition following the official tutorial from [Kali Linux  blog](https://www.kali.org/docs/usb/usb-persistence/)

```
sudo fdisk --list 

# which gave me the output 

Disk /dev/sdb: 14,33 GiB, 15376318464 bytes, 30031872 sectors
Disk model: Cruzer Fit      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf6bb8fe4

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *         64 7012351 7012288  3,4G 17 Hidden HPFS/NTFS
/dev/sdb2       7012352 7013823    1472  736K  1 FAT12

```

I switch to root account so I can run all commands without sudo.

```
sudo su - 
```

and change the work directory to location where my kali live iso file is stored. 

```
cd /home/jacek/Downloads/
```

Next I execute the commands sugested by the tutorial from the kali linux blog. 

```
read start _ < <(du -bcm kali-linux-2021.1-live-amd64.iso  | tail -1); echo $start
3426
end=7GiB
parted /dev/sdb mkpart primary ${start}MiB $end
fdisk --list 
```

Using these commands I created 3rd partition with size 3.7 GB.  I was trying to adjust start and end parameters to get 4GB partition, but it was quite difficult. 
I decided to use cfdisk tool to create 3rd partition with exact size 4GB. I heard that this is the maximal size allowed for persistence partition. But later on I thought is it really 4GB a maximal size? Lets try to use all remaining space and create bigger partition. So I finally created partition with size 11GB. 

In the last step I needed to inform my live kali instance that the USB stick has a persistence partition: 

```
mkfs.ext3 -L persistence /dev/sdb3
e2label /dev/sdb3 persistence
mkdir -p /mnt/my_usb
mount /dev/sdb3 /mnt/my_usb
echo "/ union" > /mnt/my_usb/persistence.conf
umount /dev/sdb3
```

To test it I am inserting the USB stick to laptop and booted it. I am selecting Live USB persistence on the GRUB screen. 
I am  creating test txt file on the Desktop and install htop. Finally I rebooting again to Live USB persistence mode to confirm that test file is there and htop is installed. 



