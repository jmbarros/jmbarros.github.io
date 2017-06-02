---
author: slowe
comments: true
date: 2009-11-09 20:13:38+00:00
layout: post
slug: enabling-jumbo-frames-on-a-nexus-5000
title: Enabling Jumbo Frames on a Nexus 5000
wordpress_id: 1732
categories: Tutorial
tags:
- Cisco
- Networking
- Nexus
- CLI
---

I've been doing a pretty fair amount of work recently with the Cisco Nexus 5000 series of switches, as evidenced by the flurry of Nexus-related articles:

[Connecting Nexus 5000 to Older Gigabit Ethernet Switches][1]  

[Setting Up FCoE on a Nexus 5000][2]  

[FCoE and VLAN Trunking on Nexus 5000][3]

One thing I hadn't yet documented was how to enable jumbo frames on a Nexus 5000. Since jumbo frames are now officially supported for VMkernel traffic with VMware vSphere, the combination of jumbo frames and 10Gb Ethernet is an attractive one. I've covered the ESX/ESXi side ([ordinary vSwitches here][4] and [distributed vSwitches here][5]), but here's the Nexus side.

The commands are pretty straightforward, and I've included the commands for both NX-OS 4.0 and NX-OS 4.1 (they are different between versions). _**Important note:** if you enabled jumbo frames under NX-OS 4.0 and then upgraded the switch to version 4.1, you'll need to re-do your jumbo frame configuration._

For NX-OS 4.1, the commands to enable jumbo frames are:

	switch(config)# policy-map type network-qos jumbo  
	switch(config-pmap-nq)# class type network-qos class-default  
	switch(config-pmap-c-nq)# mtu 9216  
	switch(config-pmap-c-nq)# exit  
	switch(config-pmap-nq)# exit  
	switch(config)# system qos  
	switch(config-sys-qos)# service-policy type network-qos jumbo

Now, contrast the commands above with the following commands, which you would have used to enable jumbo frames on NX-OS 4.0:

	switch(config)# policy-map jumbo  
	switch(config-pmap)# class class-default  
	switch(config-pmap-c)# mtu 9216  
	switch(config-pmap-c)# exit  
	switch(config)# system qos  
	switch(config-system)# service-policy jumbo

The end result of these differences is this: if you upgrade NX-OS from 4.0 to 4.1, then your jumbo frames configuration will go away, and you'll need to enter the commands for version 4.1 in order to enable jumbo frame support again. This little gotcha caused me quite a headache when my NFS-based datastores suddenly went offline after the NX-OS upgrade.

More information on the necessary commands can be found [here for version 4.0](http://www.cisco.com/en/US/docs/switches/datacenter/nexus5000/sw/configuration/guide/cli_rel_4_0_1a/QoS.html#wp1150612) and [here for version 4.1](http://www.cisco.com/en/US/docs/switches/datacenter/nexus5000/sw/configuration/nxos/Cisco_Nexus_5000_Series_NX-OS_Software_Configuration_Guide_chapter33.html#con_1150612).

[1]: {% post_url 2009-08-27-connecting-nexus-5000-to-older-gigabit-ethernet-switches %}
[2]: {% post_url 2009-10-25-setting-up-fcoe-on-a-nexus-5000 %}
[3]: {% post_url 2009-11-03-fcoe-and-vlan-trunking-on-nexus-5000 %}
[4]: {% post_url 2008-04-22-esx-server-ip-storage-and-jumbo-frames %}
[5]: {% post_url 2009-05-21-vmware-vsphere-vds-vmkernel-ports-and-jumbo-frames %}
