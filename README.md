# alienware13r3Ubuntu
##desiclaimer
I am not an expert, just desribing how I got it working...

Just my experience, two days of playing around to get 
18.04 running on new alienware 13 r3 laptop

did some of the update (BIOS) from windows, then made dualboot
installed, pwd login, so virtual terminals work
ubuntu18.04
grub nomodeset
no you can login, 
added ppa:graphics/ppa stuff
apt auto-clean, update, upgrade &c 
ubuntu-drivers devices
manually apt install nvidia-drivers-396
changed grub: (/etc/default/grub)
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"
#GRUB_CMDLINE_LINUX="nomodeset"
commented out the nomeodeset previously set to be able to do first startup
this worked for me. 
