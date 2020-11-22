# pi-ramdisk

Alongside a project using a Raspberry PI, I became quite concerned as several SD cards had been ruined by various PI projects in the past.  Given the Raspberry Pi 4 has 8GB of RAM (well, at least that specific model) I figured it was time to figure out how to make this work.  I am still a linux noob, so I decided to put my learnings into a readme to help future me's in the making.

## Major points:
* configurations for this are in /etc/fstab
* if you mess this up, you have to rescue your system in user mode
  * copying and pasting text from OneNote into /etc/fstab whilst using Putty will put invisible bad charaters into your file and it wont boot
  * i put text into notepad and copied out again, and then run 'dos2unix against it - this tool is accessible in the distro (if you sudo apt install it first)
* if you haven't put a password on your root account (unlikely - nothing I've seen so far actually asks) you won't be able to rescue it using linux boot methods
  * I found a link that took me through holding a key at a certain moment, which took forever
* if you are using a raspberry pi, thankfully they have a text file which you can edit boot properties with and still fix it
  * Instructions for this are at: https://linux.tips/tutorials/how-to-boot-raspberry-pi-into-single-user-mode
* if you do what I have done, logs will be lost on boot.  (this was suitable for a particular project for me, and worthwhile doing for it)

## New Lines in my /etc/fstab file:
~~~
tmpfs                 /tmp            tmpfs   defaults,noatime,nosuid,size=100m   0       0
tmpfs                 /var/tmp        tmpfs   defaults,noatime,nosuid,nodev,noexec,size=100m,mode=0755    0       0
tmpfs                 /var/log        tmpfs   defaults,noatime,nosuid,mode=0755,size=100m,mode=0755      0       0
tmpfs                 /var/run        tmpfs   defaults,noatime,nosuid,mode=0755,size=100m,mode=0755       0       0
~~~

## Lines I wan't sure about:
~~~
tmpfs    /var/spool/mqueue    tmpfs    defaults,noatime,nosuid,mode=0700,gid=12,size=50m    0 0
~~~
a swapfile is not a swap partition, no line here use  dphys-swapfile swap[on|off]  for that

