# alienware13r3Ubuntu
## How I got my new Alienware 13 r3 OLED laptop working with Ubuntu18.04

## disclaimer
I am not an expert, just desribing how I got it working...

Just my experience, two days of playing around to get  
18.04 running on new alienware 13 r3 laptop

## in windows:
did some of the update (BIOS) from windows, then made dualboot

installed ubuntu 18.04 with  pwd login, so virtual terminals work

grub nomodeset
no you can login

added ppa:graphics/ppa stuff
apt auto-clean, update, upgrade &c

ubuntu-drivers devices

manually did apt install nvidia-drivers-396

changed grub: (/etc/default/grub)
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"
#GRUB_CMDLINE_LINUX="nomodeset"

commented out the nomeodeset previously set to be able to do first startup
this worked for me. 
## Hardware
: NVIDIA(R) GeForce(R) GTX 1060 with 6GB GDDR5 graphics memory
Killer 1550 Wireless Driver
OLED
