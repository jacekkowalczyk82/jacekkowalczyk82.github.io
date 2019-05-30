---
layout: post
title: How to create a custom Debian ISO with DWM
date: 2019-05-29 15:38 +0200
categories: update manuals linux
tags: [debian,linux,stretch,buster,live-build,iso,livecd]
---

Year ago I started playing with customizing Kali Linux. I generated many custom Kali Linux ISO images with light window managers: DWM, i3, and Openbox. 
You can read about it at [this page](/my-kali-linux/). 


Since the very beginning I wanted also to try out building custom Debian Linux. 
I started reading about debian live build project and finally I tried it. 

![Debian Buster DWM screenshot](/assets/images/debian-buster-dwm-scrot.png)

## What is neede to build custom Debian ISO 

* I installed Debian Buster RC system with XFCE and added these packages:

```
sudo apt install dwm suckless-tools stterm libx11-dev libxft-dev libxinerama-dev nitrogen feh 
```

* Next I installed DWM

```
mkdir -p /opt/  && cd /opt
git clone git://git.suckless.org/dwm
cd dwm

```
I made these changes in dwm source files:

```
diff --git a/config.def.h b/config.def.h
index 1c0b587..fc42d00 100644
--- a/config.def.h
+++ b/config.def.h
@@ -44,7 +44,7 @@ static const Layout layouts[] = {
 };

 /* key definitions */
-#define MODKEY Mod1Mask
+#define MODKEY Mod4Mask
 #define TAGKEYS(KEY,TAG) \
        { MODKEY,                       KEY,      view,           {.ui = 1 << TAG} }, \
        { MODKEY|ControlMask,           KEY,      toggleview,     {.ui = 1 << TAG} }, \
@@ -57,7 +57,7 @@ static const Layout layouts[] = {
 /* commands */
 static char dmenumon[2] = "0"; /* component of dmenucmd, manipulated in spawn() */
 static const char *dmenucmd[] = { "dmenu_run", "-m", dmenumon, "-fn", dmenufont, "-nb", col_gray1, "-nf", col_gray3, "-sb", col_cyan, "-sf", col_gray4, NULL };
-static const char *termcmd[]  = { "st", NULL };
+static const char *termcmd[]  = { "stterm", NULL };

 static Key keys[] = {
        /* modifier                     key        function        argument */


```

And builded DWM :

```
cd /opt/dwm/
sudo make clean install 

```

I created `~/.xinitrc` file :

```

exec nitrogen --restore &
#exec feh --bg-scale /usr/share/desktop-base/spacefun-theme/wallpaper/contents/images/3840x2160.svg  &
#exec feh --bg-scale /home/kowalczy/Pictures/futureprototype_login.png & 
exec compton -b &
dropbox_status_string=""
while true ; do 
#    dropbox_status=$(dropbox-cli status | head -n 1)
#    if [ "$dropbox_status" == "Up to date" ]; then 
#        dropbox_status_string="Dropbox: "$(echo $dropbox_status)
#    else 
#        dropbox_status_string="Dropbox: "$(echo $dropbox_status|awk -F " " '{print $1}')
#    fi 

    load=$(cat /proc/loadavg |cut -d " " -f 3 )
    uptime=$(uptime -p)
    load_uptime="Load15: ${load}; ${uptime}"

    xsetroot -name "`date '+%Y-%m-%d %H:%M.%S' ` $load_uptime $dropbox_status_string "; sleep 1; 
done &
#exec /usr/bin/dropbox & 
exec /opt/dwm/dwm

```
and symbolic link `~/.xsession`

```
cd ~
ln -s .xinitrc .xsession
chmod 755 ~/.xinitrc
```

* I created a Xsession desktop file `/usr/share/xsessions/custom-dwm.desktop` to be able to select my custom DWM at LightDM screen:

```
[Desktop Entry]
Name=Kowalczy-DWM
Exec=/etc/X11/Xsession

```

At this point I was able to start building new ISO

## How to build Debian live ISO

* Firsty I needed to install some additional packages:

```
sudo apt install curl git live-build debootstrap 
```

* For building Debian Stretch 

```
mkdir -p my-debian/live-build-stretch
cd my-debian/live-build-stretch
sudo lb config --debian-installer live -d stretch

```

I added my packages to `config/package-lists/live.list.chroot`

```
live-boot
live-config
live-config-systemd

xorg
xfce4
#DWM
dwm
suckless-tools
#dmenu
#slock

stterm
libx11-dev
libxft-dev
libxinerama-dev

lightdm 
compton
nitrogen
feh
scrot
fonts-dejavu

#editors 
mousepad
geany

#accessories
gpicview
evince
lxrandr
galculator
xarchiver
lxinput
libreoffice

#terminals
xterm
#lxterminal
#terminator
xfce4-terminal

#web browsers
#chromium
firefox-esr

youtube-dl

#dev tools
meld

# file manager
thunar
tango-icon-theme
adwaita-icon-theme
hicolor-icon-theme


breeze-icon-theme
faba-icon-theme
faenza-icon-theme
moka-icon-theme
tango-icon-theme
numix-icon-theme
papirus-icon-theme



#systray apps
pulseaudio
pavucontrol
pasystray
udiskie
network-manager
network-manager-gnome
clipit
xfce4-power-manager
xscreensaver
plank

#utilities
sudo
git
git-gui
curl
mc
vim
htop
openssh-server
apt-transport-https
screenfetch
neofetch
gmrun
i3lock

#simple firewall
#gufw                   # package not found 

#live-build
#cdebootstrap

#printers
system-config-printer


#for firefox developer edition, 
#firefox-developer-edition is installed in /opt/firefox 
libdbus-glib-1-2

#multimedia 
vlc
mpv
smplayer
audacious
audacious-plugins

#packages for virtualbox guest additions
build-essential
module-assistant


```


And added customization files to `config/includes.chroot/`

```
mkdir -p config/includes.chroot/opt/
mkdir -p config/includes.chroot/opt/backgrounds/
mkdir -p config/includes.chroot/etc/skel/.config/

cp ~/.xinitrc config/includes.chroot/etc/skel/
pushd config/includes.chroot/etc/skel/
ln -s .xinitrc .xsession
popd

#I downloaded some wallpaper from the web
cp opt/backgrounds/futureprototype_login.png config/includes.chroot/opt/backgrounds/futureprototype_login.png

cp usr/share/xsessions/custom-dwm.desktop config/includes.chroot/usr/share/xsessions/custom-dwm.desktop

cp -r /opt/dwm config/includes.chroot/opt/


```

Build Debian Buster ISO

```
#when rebuilding run also clean
sudo lb clean --purge
#build ISO
sudo lb build --debug --verbose 2>&1 |tee lb-build-stretch-`date '+%Y-%m-%d_%H%M%S'`.log

```

* Building Debian Stretch was quite similar

```
cd my-debian/live-build-buster
sudo lb config --debian-installer live -d buster
#add your packages to config/package-lists/live.list.chroot
#add your customization files to config/includes.chroot/
#when rebuilding run also clean
sudo lb clean --purge

#build ISO
sudo lb build --debug --verbose 2>&1 |tee lb-build-buster-`date '+%Y-%m-%d_%H%M%S'`.log

```

but a bit harder because the debian installer Linux Kernel is a bit older then the packages for the regular Debian Buster. 
When I was booting the generated ISO I was getting error: "No kernel modules were found. This is due to a mismatch between the kernel used by this version of the installer and the kernel version available in the archive. "

I made tricky hack and replaced the kernel files for installer 
 
```
sudo apt install genisoimage
mkdir hack
cd hack 
mkdir iso
mkdir hackediso
#assuming the lb generated debian-buster-dwm-live-amd64.hybrid.iso file
mv ../debian-buster-dwm-live-amd64.hybrid.iso ./
sudo mount -t iso9660 -o loop debian-buster-dwm-live-amd64.hybrid.iso  iso

cp -r iso/ hackediso/
# replace vmlinuz  and initrd.gz and gtk directory in hackediso/install/ with the correct debian installer daily image 
# from https://d-i.debian.org/daily-images/amd64/20190529-00:24/cdrom/

wget https://d-i.debian.org/daily-images/amd64/20190529-00:24/cdrom/vmlinuz 
#rebuild iso again

cd my-debian/live-build-buster/hackediso/install/ 
wget https://d-i.debian.org/daily-images/amd64/20190529-00:24/cdrom/vmlinuz 
wget https://d-i.debian.org/daily-images/amd64/20190529-00:24/cdrom/initrd.gz 
cd my-debian/live-build-buster/hackediso/install/gtk/ 
wget https://d-i.debian.org/daily-images/amd64/20190529-00:24/cdrom/gtk/vmlinuz 
wget https://d-i.debian.org/daily-images/amd64/20190529-00:24/cdrom/gtk/initrd.gz 
cd my-debian/live-build-buster/hackediso/
sudo genisoimage -o ../debian-buster-dwm-live-20190529-amd64.hybrid.hacked-2.iso -r -J -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-info-table -boot-load-size 4 ./

```

* In the ned I got Debian Buster Live ISO with DWM that I can install or use as livecd. 



## Links 

Links to raw notes and configs [at my debian page](/my-debian/)
