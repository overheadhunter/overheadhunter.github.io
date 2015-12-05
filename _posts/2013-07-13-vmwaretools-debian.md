---
layout: post
title:  "VMWare Tools auf Debian installieren"
date:   2013-07-13
tags: [vmware, linux]
---
Hab mir heute Debian Wheezy in VMware Fusion 4 installiert, was mich einiges an Googlei gekostet hat. Daher hier for the record das richtige Vorgehen:

Voraussetzungen:

```shell
apt-get install libglib2.0-0 build-essentials linux-headers-`uname -r`
```

Anschließend übers Host-Sytem im VMware-Menü auf „Virtuelle Maschine“ -> „VMware Tools installieren“ klicken und im Gast-System die CD mounten (falls nicht schon geschehen):

```shell
mount /dev/cdrom
```

Nun können die Tools entpackt und installiert werden.

```shell
cd /tmp
cp /media/cdrom/VMwareTools-XXXXXX.tar.gz .
tar -xzf VMwareTools-XXXXX.tar.gz
vmware-tools-distrib/vmware-install.pl
```
