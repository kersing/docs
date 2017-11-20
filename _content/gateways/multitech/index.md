---
title: MultiTech Conduit
section: Hardware
redirect_from:
 - /current/multitech/
 - /multitech/
ambassador:
  name: Jac Kersing
  username: kersing
image: /gateways/multitech/image.jpg
zindex: 900
---

Currently MultiTech provides two LoRaWAN gateways:
* The [MultiConnect® Conduit™](http://www.multitech.net/developer/products/multiconnect-conduit-platform/) is a configurable, scalable cellular communications gateway for industrial IoT applications. Conduit allows users to plug in two MultiConnect mCard™ accessory cards supporting wired or wireless interfaces.

![MultiTech Conduit](image.jpg)

* The [MultiConnect® Conduit™ AP](http://www.multitech.net/developer/products/multiconnect-conduit-access-point/) (MTCAP) connects thousands of IoT assets to the cloud using the LoRaWAN® protocol. It expands LoRa network coverage to difficult to reach areas and is capable of packet forwarding user data between LoRa end points and a centrally located network server on the cloud, in a data center, or a public network.

This guide will help you set up these gateways to communicate over The Things Network.

## Prerequisites

* MultiTech Conduit or MultiTech Conduit AO [AEP](http://www.multitech.net/developer/software/aep/) or [mLinux](http://www.multitech.net/developer/software/mlinux/) model

  > There is no need to update any of the MultiTech software on the conduit.

* For the MultiTech Conduit (not AP model) an MultiTech [MTAC-LoRa LoRa accessory card](http://www.multitech.net/developer/products/multiconnect-conduit-platform/accessory-cards/mtac-lora/), installed as [instructed in the Quickstart Guide](http://www.multitech.net/developer/wp-content/uploads/2016/12/Accessory-Card-QSG.pdf).

  > Do not forget to mount the antenna to the mCard after fitting it in the conduit.
  
* Computer with USB port and terminal software. Mac OS and Linux come with terminal software. For Windows you can use something like [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).
* For the MultiTech Conduit mLinux version you'll need a USB stick.
