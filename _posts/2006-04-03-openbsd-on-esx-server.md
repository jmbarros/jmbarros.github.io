---
author: slowe
comments: false
date: 2006-04-03 09:29:42+00:00
layout: post
slug: openbsd-on-esx-server
title: OpenBSD on ESX Server
wordpress_id: 215
categories: Information
tags:
- BSD
- ESX
- Virtualization
- VMware
- UNIX
---

Having already successfully installed [OpenBSD](http://www.openbsd.org/) (version 3.8) on [GSX Server](http://www.vmware.com/products/gsx/), the task now becomes installing OpenBSD 3.8 on [ESX Server](http://www.vmware.com/products/esx/). For the most part, the experience is very similar, but there are a couple of important details.

First, of course, there is the [issue with the pcn0 driver][1] used by OpenBSD for the virtual NIC presented by VMware. This issue is [quickly and easily resolved][2]. At this time, there is no OpenBSD support for VMware's more efficient VMXnet driver---only the vlance driver.

Second, the virtual SCSI driver must be switched to LSI Logic instead of BusLogic. Since OpenBSD isn't a supported guest operating system, an alternate selection must be made when creating the virtual machine. [FreeBSD](http://www.freebsd.org/) is the next closest choice, but VMware will default to BusLogic SCSI adapters with FreeBSD virtual machines. However, once you change to the LSI Logic SCSI adapter, everything seems to work just fine.

From there, the installation is perfectly straightforward. There are no VMware Tools for OpenBSD, although I have heard rumors that people have gotten versions for other operating systems to run on OpenBSD.

[1]: {% post_url 2005-11-02-small-openbsd-38-speed-bump %}
[2]: {% post_url 2005-11-04-openbsd-pcn0-driver-issue-resolved %}
