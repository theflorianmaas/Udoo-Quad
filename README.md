# Udoo Quad - Boot from sata driver with Ubuntu 16.04

Based on the original istructions for Ubuntu 14.04 https://www.udoo.org/docs/Hardware_&_Accessories/Boot_from_SATA.html

Boot from SATA

This guide will show you how to boot your UDOO QUAD (not tested on DUAL, but it should work) from an attached SATA drive with the help of a small SD card.

NOTE: It is not possible to boot without an SD card, it is hoped that this feature will be added in the future.
Prerequisites

    A SATA drive
    A SD card
    A micro USB cable such as one for charging a smart phone
    UDOObuntu 3.0 (beta)

1. Flash the boot SD card

You need an SD card with the bootloader in order to boot from SATA. 
Download the file Udoo_qdl-sata-3.zip that contains the boot image and, after unzipping it, flash it to the SD:

    dd if=udoo_qdl-sata-3.img of=/dev/mmcblk0 bs=1M

2. Flash the SATA drive

Download the latest UDOObuntu from the official site [Udoobuntu 3.0beta1](https://drive.google.com/file/d/1jmVr4k3DuE1jLi9FneefZ1Y0tJlcYw76/view)

Decompress the image and flash it to the SATA drive:

# in this example, the SATA drive device is /dev/SATA
    
    dd if=udoobuntu-udoo-qdl-desktop_3.0beta1.img of=/dev/SATA bs=1M

 Remember to patch the /etc/fstab inside the SATA disk:

    mount /dev/SATA2 /mnt/sata 

 (/dev/SATA2 is the second partition, available after flashing UDOObuntu;)

 Edit /etc/ftab
    
    sudo nano /etc/fstab
    
 Replace the content with these two lines and save:

    /dev/sda2  /      ext4  defaults,noatime               0  0
    /dev/sda1  /boot  vfat  defaults,noatime               0  0
    
3. Install

    Insert the boot SD card

    Attach the sata driver

    Reboot



