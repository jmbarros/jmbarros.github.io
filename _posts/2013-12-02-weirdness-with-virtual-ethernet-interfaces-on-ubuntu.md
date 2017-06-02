---
author: slowe
comments: true
date: 2013-12-02 17:40:00+00:00
layout: post
slug: weirdness-with-virtual-ethernet-interfaces-on-ubuntu
title: Weirdness with Virtual Ethernet Interfaces on Ubuntu
wordpress_id: 3373
categories: Rant
tags:
- CLI
- Linux
- Networking
- Ubuntu
---

I've been doing some experimenting with virtual Ethernet (veth) interfaces in Ubuntu as part of the ongoing work with network namespaces, LXC, and related technologies. A few times I've run into a very weird situation, and I have yet to figure out exactly what's happening. I thought I might share it here in the hopes that someone else has seen this behavior and knows a) what causes it, and b) how to fix it.

I'll start with a pretty vanilla installation of Ubuntu 12.04 LTS and Open vSwitch (OVS). When I run `ip link list`, I get output that looks something like this (click the image for a larger version):

[
![Before adding the veth pair]({{ site.url }}/public/img/pre-veth-pair-link-list-small.png)]({{ site.url }}/public/img/pre-veth-pair-link-list.png)

OK, nothing unusual or unexpected there.

Next, I'll add a pair of veth interfaces:

    ip link add vmveth0 type veth peer vmveth1

Then the output of `ip link list` looks like this (I've circled some of the output to draw your attention; again, you can click for a larger version):

[
![After adding the veth pair]({{ site.url }}/public/img/post-veth-pair-link-list-small.png)]({{ site.url }}/public/img/post-veth-pair-link-list.png)

See? The name of the veth peer interface gets garbled up and somehow corrupted. Because of this, nothing works---I can't use the veth pair to connect network namespaces, or to connect a Linux bridge to OVS, or anything else. Rebooting the system does not fix the problem; only a rebuild seems to get rid of it.

Anyone have any ideas?
