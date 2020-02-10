--
layout: post
title: BSD Bluetooth audio
date: 2020-02-09 10:58 +0100
categories: update manuals bsd
tags: [freebsd,openbsd,bsd,bluetooth,audio,adapter]
---

//// BT audio on devices without bt but with mini jack out and AUX ports.

I was strugling a lot with Sound and Bluetooth on my ThinkPad x240 laptop, which is running FreeBSD 12.1. 
This laptop has some issue with the speaker, volume is very low, I hardly hear anything, but the mini jack works ok. 
There were few ways to solve it.
1. Repair the built in speaker, but it was the last thing I wanted to do. 
2. Use headphones or external speakers connected with cables to mini jack headphones port, but again cables. 
3. Use Bluetooth speaker or headphones. 

I thought BT audio is a nice idea and I wanted to try it out. It turned out that Bluetooth support at FreeBSD is quite poor, and at OpenBSD they remove the Bluetooth stack completely. 
I bought CSR 4.0 Bluetooth USB dongle and Bluetooth audio receiver BTR-302 (v3.0 + EDR ). I managed to create a BT audio connection. 

```
sudo service bluetooth start ubt1

# search for BT devices 
sudo hccontrol -n ubt1hci inquiry 

#it found a device 30:21:65:55:11:29

sudo hccontrol -n $ubt1hci create_connection 30:21:65:55:11:29

# Disable kernel's /dev/dsp
sudo sysctl hw.snd.basename_clone=0

sudo virtual_oss -C 2 -c 2 -r 48000 -b 16 -s 768 -R /dev/null -P /dev/bluetooth/30:21:65:55:11:29 -d dsp

```
After that I  was able to play music from audacious and videos by mplayer:

```
mplayer -ao oss:/dev/dsp movie-file-mp4
```

It is important to stop BT stack

```
sudo service bluetooth stop ubt1
```

It workd with the BT dongle and this small BT receiver, but the receiver has a very small battery so I is not enought for watching or listening for 2 hours. 

I did not managed to connect to more modern BT headphones or spekers like JBL Flik4 or Fioo uBTR. 



4. I found BT adapters that can work as transmitter and receiver.  I bought two of them and gues what they can easily connect to each other. 
transmitter adapter I can connect to my ThinkPad or any device that has oudio out by mini jack. The receiver I can connect with external speakers or headphones also by mini jack. 
These BT adapters do not have any batteries and thy need to be powered by USB type A port. 


