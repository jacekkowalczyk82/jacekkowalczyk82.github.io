---
layout: post
title:  "How to install OpenBSD 6.4 with DWM?"
date:   2019-03-07 10:12:00 +0100
categories: update manuals bsd
tags: [tips,manual,dwm,openbsd,openbsd64]
---


Baic installation of the OpenBSD 6.4 is straightforward. For most installer questions you just press Enter. 

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
|(I)nstall, (U)pgrade (A)utoinstall or (S)hell ?        |   |
|(I)nstall, (U)pgrade (A)utoinstall or (S)hell ?        |   |
|(I)nstall, (U)pgrade (A)utoinstall or (S)hell ?        |   |
|(I)nstall, (U)pgrade (A)utoinstall or (S)hell ?        |   |
|(I)nstall, (U)pgrade (A)utoinstall or (S)hell ?        |   |
|(I)nstall, (U)pgrade (A)utoinstall or (S)hell ?        |   |
|(I)nstall, (U)pgrade (A)utoinstall or (S)hell ?        |   |


## Installing additional applications 

```
pkg_add sudo htop i3 nano vim firefox geany 


```


