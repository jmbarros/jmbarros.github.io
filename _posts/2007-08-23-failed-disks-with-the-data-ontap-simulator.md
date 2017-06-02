---
author: slowe
comments: true
date: 2007-08-23 11:42:53+00:00
layout: post
slug: failed-disks-with-the-data-ontap-simulator
title: Failed Disks with the Data ONTAP Simulator
wordpress_id: 509
categories: Information
tags:
- NetApp
- Storage
---

Last year I wrote about using the Network Appliance [Data ONTAP Simulator on ESX Server][1], and in the comments to that article a number of people indicated that they'd been having problems with adding disks to the Simulator. The disks they added would show up as failed, and therefore couldn't be added to any aggregates or volumes.

Readers Sdodson and Jacek provided workarounds in their comments to that article; as it turns out, this is the official workaround from NetApp, as described in [this support article](http://now.netapp.com/Knowledgebase/solutionarea.asp?id=kb14670) (login required).

So, if you're using the Simulator and happen to run into this problem, the fix is simply to mark the disks as unfailed, zero them, and then you should be able to use the disks as you expect.

[1]: {% post_url 2006-06-27-netapp-ontap-simulator-and-esx-server %}
