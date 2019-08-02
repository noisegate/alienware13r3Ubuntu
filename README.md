# alienware 13 R3 Ubuntu 18.04
## How I got my new Alienware 13 r3 OLED laptop working with Ubuntu18.04

## DISCLAIMER
I Am Not An Expert, just describing how I got it working...

 My experience, two days of playing around to get  
18.04 running on new alienware 13 r3 laptop with OLED/touch screen.

## in windows:
did some of the update (BIOS) from windows, then made dualboot

installed ubuntu 18.04 with  pwd login, so virtual terminals work

### problem:
Installer always got stuck:

press shift after BIOS loading to get into GRUB menu.

https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time

and set grub nomodeset
now the installer will work smoothly


## start

added PPA repository for nvidia drivers:

```bash
add-apt-repository ppa:graphics-drivers/ppa
```

then:
```bash
apt auto-clean
apt update
apt upgrade
```
Now you can take a look at:

```bash
ubuntu-drivers devices
```

and install recommended drivers

```bash
ubuntu-drivers autoinstall
```
### Update
First time:
I however did it manually:

```bash
apt install nvidia-drivers-396
```

but a second time I did the recommended, 415
it turned out to be at the time.


changed grub: (/etc/default/grub)

```bash
sudo vi /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"
#GRUB_CMDLINE_LINUX="nomodeset"
```
ie: I added ```nvidia-drm.modeset=1``` to ```GRUB_CMDLINE_LINUX_DEFAULT``` and
commented out ```GRUB_CMDLINE_LINUX="nomodeset"``` previously set to be able to do first startup
this worked for me.

after editing the grub file:

```bash
update-grub
```
and reboot.

## wifi

to get the Killer 1550 working:
https://askubuntu.com/questions/1016903/alienware-17-r4-ubuntu-16-04-wifi-driver

so (citing them:)

```bash
sudo apt-get install git
git clone https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git
cd backport-iwlwifi
make defconfig-iwlwifi-public
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
make -j4
sudo make install

after kernel update u need to https://gist.github.com/awesomebytes/87071f45b88eea334c6c8065a5956614
repeat sudo make install


```
## Keyboard color fx

https://github.com/trackmastersteve/alienfx

works on my laptop, had to use the newcmdpacket though...

## Hardware
: NVIDIA(R) GeForce(R) GTX 1060 with 6GB GDDR5 graphics memory

Killer 1550 Wireless Driver

13.3" QHD (2560 x 1440) Touch Technology, OLED Technology, 400-nits Display

## Slow dekstop

After update very slow desktop. This was caused by
```GRUB_CMDLINE_LINUX="nomodeset" 
``` 
which should have been commented out but 
somehow reappeared at the bottom of the grub file.


## Wifi

After a while slows down, possible remedy:

https://askubuntu.com/questions/1030653/wifi-randomly-disconnected-on-ubuntu-18-04-lts

So, 
```
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf and changing
```

```
wifi.powersave = 3
```

to 

```
wifi.powersave = 2
```


