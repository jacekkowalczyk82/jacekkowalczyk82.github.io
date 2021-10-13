---
layout: post
title: How to play audio from youtube in console at FreeBSD
date: 2021-10-11 16:28 +0200
categories: update manuals linux freebsd
tags: [freebsd,linux,youtube,audio,youtube-dl,mplayer]
---

I am using FreeBSD  computer also for playing some music while I am working on HomeOffice. 
Till today I had two options: 
* 1st - start X11 on FreebSD and run web browser with youtube to play some music, 
* 2nd - to download audio first using youtube-dl and then add it to cmus playlist, for example. 

Both of these solutions I found inconvenient in some cases. 

Today I created a script that mixes both solutions. The script allows me to play instantly any youtube audio I want without starting X11. 

I can play some music like this:

```
playtube.sh https://www.youtube.com/watch?v=15kWzIAq4gA

```

and here is the script

```

#!/usr/bin/env bash

VIDEO_URL=$1

if [[ -z $VIDEO_URL ]]; then 
    echo "ERROR: Missing VIDEO_URL param " 
    exit 1
fi 

mkdir -p ~/private/music/youtube-dl-temp
cd ~/private/music/youtube-dl-temp

FILE_NAME=$(youtube-dl -f 251 --get-filename --restrict-filenames $VIDEO_URL )

youtube-dl -f 251 -o $FILE_NAME $VIDEO_URL 

mplayer -novideo $FILE_NAME


```

Day later after this post I started improving my console player. I created this python script https://github.com/jacekkowalczyk82/py-playtube. 
There will be changes to that script as I have few improvments in my mind. 
