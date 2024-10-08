+++
title = "TP-Link TL-WR740N Recovery"
description = ""
date = 2021-03-13
lang = "en"
extra = { version = "v0.1" }
+++

I have an old TP-Link TL-WR740N that was given to me by a friend. After installing OpenWrt I used it as a wireless client to bridge internet connection next door. 

Couldn't install much software though with very limited flash storage and no external USB port.

We removed it some time after I purchased outdoor ethernet cables.

Thing died probably after an interrupted reset.

![](1.png)

Good thing there was a recovery guide OpenWrt [TP-Link TL-WR740N](https://openwrt.org/toh/tp-link/tl-wr740n)

Very dusty

![](2.jpg)

Soldering twisted pair as cables so we can have serial console

> TX pin is not connected to the CPU. In order to make the TX line working, the two points on the bottom side of the PCB must be connected with a small wire. The pin at the SOC is labeled TP18, the one at the serial connector is labeled TP28.

![](3.jpg)

A look at my workbench

![](4.jpg)

Hooking it up to my computer

![](5.jpg)

dnsmasq tftp config

```
dhcp-range=192.168.1.2,192.168.1.254,12h
enable-tftp
tftp-root=/home/kbeflo/tftp
```

start dnsmasq 

```
sudo dnsmasq -C tftboot.conf
```

start tftpboot on the device etc.

![](6.png)

Success~
