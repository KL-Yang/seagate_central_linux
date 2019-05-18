# Seagate_central_linux (Single Disk Version)

For linux-3.18.y and 4.4.y kernel, use corresponding branch; master is updated to 4.19.y, WIP.

To compile, copy and overlay the files to linux-4.19.y, then apply the patch accordingly. 
For native compile, use command: $LOADADDR=0x02000000 make uImage.
The foundamental patches are from OpenWRT, they are copied and merged here for convinence.
One of the hacky patch is to fix the ethernet configuration that is specific to Seagate Central. 
config_seagate_smp is a working example of kernel configuration.

USB and RTC is not working yet. USB is likely due to missing PHY/VBUS configuration. 
SATA, Ethernet and SMP are working fine in my test of compiling the kernel itself natively with -j2.

# Performance
iperf3 120 seconds average sending and receiving are 532 Mbits/sec and 487 Mbits/sec.

# Prebuild images
All the thanks goes to Debian and OpenWRT. Kerenl 4.19.41 and Debian Buster Rootfs:

https://drive.google.com/open?id=1RArbF_jtwHtqGJVlQWD_X0lkkJKFC_6d

The kernel is built on Seagate Central. After booting, find the DHCP address on you router, ssh login, 
and root password is password.
Note, the MAC address was set to a random value by me, it cannot read the value in your firmware.
Change according to your device.

Unpack and copy uImage to the first (sda1) partition, ext2, and copy the rootfs to sda3, ext4, it should boot.
The stock uboot seems passing kernel parameters in a strange way, the rootfs must be seat on sda3. 
You may need force kernel command line argument to put rootfs on other partition.
The /dev/sda2 is used as swap.

Use ON YOUR OWN RISK.
