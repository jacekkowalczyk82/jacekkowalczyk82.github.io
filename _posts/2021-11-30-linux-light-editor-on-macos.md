---
layout: post
title: Linux light editor on MacOs
date: 2021-11-30 11:36 +0100
categories: update manuals linux 
tags: [macos,linux,docker,pluma,light,editor,gui]
---

In this  manual I will explain how to run some lightweight linux editor on MacOS (in my case it is MacOS Big Sur). 

Why? most of the text editors for MacOS are quite slow, and sometimes I just want  to quickly edit some text or code file with gui application. 

Yes, there are alternatives: 
VSCode/VSCodium, Geany. 

But, I wanted also to learn a bit and I like pluma text editor which is not available for MacOS natively. 

#### Prerequisities

* Install Docker Destop for Mac
* Install Homebrew
* Install XQuartz for Mac (X11 server)
* Enable the option `Allow connections from network clients` in XQuartz settings
* Install sockat `brew install socat` - it will be needed to forward connections to the XQuarz X11 server. 

#### Create a docker image and pluma startup script

* Create a `Dockerfile`

```
FROM debian:buster

RUN echo "building debian-editor"

RUN apt-get update
RUN apt-get -y install pluma

COPY run-editor.sh /run-editor.sh
RUN chmod 755 /run-editor.sh

ENTRYPOINT [ "/run-editor.sh" ]

```

* Create `run-editor.sh`  script

```
#!/bin/bash 

/usr/bin/pluma "$@"
```

* Build docker image

```
docker build -t debian-editor .
```

* Create a script to start this conatiner based pluma editor

```
#!/bin/bash

FILE=$1
OPEN_FILE=""

if [[ -z $FILE ]]; then 
    OPEN_FILE=""
else 
    OPEN_FILE="/tmp/$FILE"
fi 

mkdir -p ~/docker-home/pid_files/
PID_FILES=~/docker-home/pid_files/

SOCAT_STARTED=0
if [ -e ${PID_FILES}/socat_PID.pid ]; then 
    echo "socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\" is already running in the background, with PID: $(cat ${PID_FILES}/socat_PID.pid )"
    SOCAT_STARTED=0

else 
    socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\"  & 
    socat_PID=$(echo $!)
    echo "$socat_PID" > ${PID_FILES}/socat_PID.pid
    echo "socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\" is running in the background, with PID: $socat_PID"
    SOCAT_STARTED=1
fi 

docker run -it --rm -e DISPLAY=host.docker.internal:0  -v `pwd`:/tmp/ debian-editor $OPEN_FILE


cat ${PID_FILES}/socat_PID.pid
ps aux |grep socat 

if [ $SOCAT_STARTED -eq 1 ] ; then 
    # killing socat only if it was started by this script instance
    echo "killing $(cat ${PID_FILES}/socat_PID.pid )"
    kill -s TERM $(cat ${PID_FILES}/socat_PID.pid )
    ps aux |grep socat 

    rm ${PID_FILES}/socat_PID.pid
fi 
echo "done"


```

* Open any file on your MacOS system by just typing `pluma filepath` in the terminal.



