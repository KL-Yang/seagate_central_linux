# seagate_centeral_linux
mainline linux patch for Seagate Central NAS 4.x (linux-4.2.y)

see: http://forum.doozan.com/read.php?2,22114
the config_seagate_good0 after apply patch is a basic configuration for Debian Jessie.

Works: sata, ethernet
Not yet: smp, usb, rtc, mtd

Note for the ethernet driver, cns3420 uses edge triger irq.
http://www.linuxfoundation.org/collaborate/workgroups/networking/napi#non-level_sensitive_IRQs
