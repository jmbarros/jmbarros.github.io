---
author: slowe
comments: true
date: 2009-02-02 21:37:16+00:00
layout: post
slug: netapp-vif-member-limitations
title: NetApp VIF Member Limitations
wordpress_id: 1143
categories: Explanation
tags:
- NetApp
- Networking
- ONTAP
- Storage
---

I've written a couple of times about NetApp virtual interfaces (VIFs), which are Data ONTAP's name for a link aggregate using either EtherChannel or dynamic LACP. The earlier articles I wrote are:

[Cisco Link Aggregation and NetApp VIFs][1]  
[LACP with Cisco Switches and NetApp VIFs][2]

I came across an issue today of which I was not aware. I've been working on a new NetApp deployment with a fellow engineer that called for a number of different VIFs to be created: one for CIFS traffic, one for NFS traffic, and one for SnapMirror traffic. (Yes, I know the SnapMirror VIF won't really use more than one link because it's all point-to-point traffic; it's primarily for redundancy.) There were some really strange network issues going on, like losing connectivity to the default gateway one moment and then network connectivity being restored the next. We were having a hard time troubleshooting the problem until one of the network engineers casually commented that it looked like the static LACP bundles (the aggregated links represented by the VIFs on the NetApp storage array) weren't really coming up.

That comment lead to a deeper inspection of the NetApp VIFs and eventually a case with NetApp. The end result was that we learned that multimode VIFs can't span built-in NICs and add-in NICs. Since the FAS3000 series has a limited number of built-in NICs, we'd installed two additional quad-port NICs and then, as was customary, created VIFs spanning the built-in NICs and the add-in NICs for maximum redundancy. Well, that doesn't work!

Once we reconfigured the Cisco switches (these were Cisco Catalyst 3750 switches uplinked via 10 Gigabit Ethernet to Catalyst 6509 switches) so that the link aggregates only contained add-in NICs or built-in NICs but not both, the connections came up fully and the network connectivity issues disappeared.

So, when creating multimode VIFs, be sure to only include NICs from add-in cards **or** the built-in NICs, but not both.

[1]: {% post_url 2007-06-13-cisco-link-aggregation-and-netapp-vifs %}
[2]: {% post_url 2008-01-08-lacp-with-cisco-switches-and-netapp-vifs %}
