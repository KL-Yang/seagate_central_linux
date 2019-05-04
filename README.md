# Seagate_central_linux (Single Disk Version)

For linux-3.18.y and 4.4.y kernel, use corresponding branch; master is updated to 4.19.y.

The 4.19.y kernel is still WIP. Copy the files in files directory overlay to linux-4.19, 
then apply the patch accordingly. Foundamental patches are from OpenWRT of cns3xxx kernel, 
they are copied and merged for convinence.
One of the hacky patch is to fix the ethernet setup problems that specific to Seagate Central. 
config_seagate_smp is a working example of kernel configuration.

USB and RTC is not working yet. USB is likely due to missing PHY/VBUS configuration. SATA, Ethernet and SMP are 
working fine in my test of compiling the kernel itself on Seagate Central with -j2.

Kernel can be compiled with command: $LOADADDR=0x02000000 make uImage

# Prebuild images
Kernel and Rootfs, TO BE Rebuild based on Debian Buster. Older version refer to older branch. 

All the thanks goes to OpenWRT. Some discussion can be found on http://forum.doozan.com/read.php?2,22114

The kernel is built on Seagate Central. After booting, find the DHCP address on you router, ssh login, 
and root password is password.
Note, the MAC address was set to a random value by me, it cannot read the value in your firmware.

Unpack and copy uImage to the first (sda1) partition, and copy the rootfs to sda3, it should boot.
The stock uboot seems passing kernel parameters in a strange way, the rootfs must be seat on sda3. 
You may need force kernel command line argument to put rootfs on other partition.

This is a Wip patch, use ON YOUR OWN RISK.
