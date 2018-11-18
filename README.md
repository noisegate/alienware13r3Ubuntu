# alienware13r3Ubuntu
## How I got my new Alienware 13 r3 OLED laptop working with Ubuntu18.04

## disclaimer
I am not an expert, just desribing how I got it working...

Just my experience, two days of playing around to get  
18.04 running on new alienware 13 r3 laptop

## in windows:
did some of the update (BIOS) from windows, then made dualboot

installed ubuntu 18.04 with  pwd login, so virtual terminals work

## reboot
press shift after BIOS stuff to get into recovery mode
grub nomodeset
no you can login

added ppa:graphics/ppa stuff
apt auto-clean, update, upgrade &c

ubuntu-drivers devices

manually did 

```bash
apt install nvidia-drivers-396
```

changed grub: (/etc/default/grub)

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"
#GRUB_CMDLINE_LINUX="nomodeset"
```

commented out the nomeodeset previously set to be able to do first startup
this worked for me. 
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
```
## Keyboard color fc

https://github.com/trackmastersteve/alienfx

works on my laptop, had to use the newcmdpacket though...

## Hardware
: NVIDIA(R) GeForce(R) GTX 1060 with 6GB GDDR5 graphics memory

Killer 1550 Wireless Driver

13.3" QHD (2560 x 1440) Touch Technology, OLED Technology, 400-nits Display
