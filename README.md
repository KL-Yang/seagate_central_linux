# Seagate_central_linux

The following two files are patch for OpenWRT 15.05's cns3xxx kernel

1. 901_seagate_central_ethernet_smp.patch
2. config_seagate_smp

Usage:

Clone linux-3.18.y stable branch, apply OpenWRT 15.05's cns3xxx target kernel patch (a snapshot copy is in this project), then apply this patch. 
Cross-compile the kernel on a Debian PC and the kernel should boot on Seagate Central NAS with Debian Jessie armel rootfs. 
SATA, Ethernet and SMP are working fine in my test and I can compile the kernel itself on Seagate Central with -j2 to validate the stability of kernel. 
USB and RTC is not working yet. All the thanks goes to OpenWRT.

See: http://forum.doozan.com/read.php?2,22114

A Debian Jessie rootfs (debootstrap armel) and kernel 3.18.27 can be found here
https://drive.google.com/file/d/0B-PZDFHXqH6pWmRJQ0k3enUzNzg/view?usp=sharing
MD5: 39fa4a61da52e9e2da909fe90990dcee

The kernel is built on Seagate Central. After booting, find the DHCP address on you router, ssh login, 
and root password is password.
Note, the MAC address was set to a random value by me, it cannot read the value in your firmware.

Unpack and copy uImage to the first (sda1) partition, and copy the rootfs to sda3, it should boot.
The stock uboot seems passing kernel parameters in a strange way, the rootfs must be seat on sda3. 
You may need force kernel command line argument to put rootfs on other partition.

This is a Wip patch, ON YOUR OWN RISK.
The files are copied from OpenWRT, and the patch applies on top of them.
