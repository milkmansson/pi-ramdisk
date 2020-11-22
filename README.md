# pi-ramdisk

Alongside a project using a Raspberry PI, I became quite concerned as several SD cards had been ruined by various PI projects in the past.  Given the Raspberry Pi 4 has 8GB of RAM (well, at least that specific model) I figured it was time to figure out how to make this work.  I am still a linux noob, so I decided to put my learnings into a readme to help future me's in the making.

Major points:
* configurations for this are in /etc/fstab
* if you mess this up, you have to rescue your system in user mode
* if you haven't set up a user mode (unlikely - nothing I've seen so far actually asks) you won't be able to rescue it using linux boot methods
* if you are using a raspberry pi, thankfully they have a text file which you can edit boot properties with and still fix it
  * Instructions for this are at: https://linux.tips/tutorials/how-to-boot-raspberry-pi-into-single-user-mode

