# Seagate_central_linux

The following two files are patch for OpenWRT 15.05's cns3xxx kernel

1. 901_seagate_central_ethernet_smp.patch

2. config_seagate_smp

Usage:

Clone linux-3.18.y stable branch, apply OpenWRT 15.05's cns3xxx target kernel patch, then apply this patch. Cross-compile the kernel on a Debian PC and the kernel should boot on Seagate Central NAS with Debian Jessie armel rootfs. SATA, Ethernet and SMP are working fine in my test and I can compile the kernel itself on Seagate Central with -j2 to validate the stability of kernel. USB and RTC is not working yet. All the thanks goes to OpenWRT.



The rest files are mainline linux patch for Seagate Central NAS 4.x (linux-4.2.y), to be cleanup into another branch.

see: http://forum.doozan.com/read.php?2,22114
the config_seagate_good0 after apply patch is a basic configuration for Debian Jessie.

Works: sata, ethernet
Not yet: smp, usb, rtc, mtd

Note for the ethernet driver, cns3420 uses edge triger irq.
http://www.linuxfoundation.org/collaborate/workgroups/networking/napi#non-level_sensitive_IRQs

This is a Wip patch, in progress of cleaning up and try to upstream later.
The files are copied from OpenWRT, and the patch applies on top of them.
