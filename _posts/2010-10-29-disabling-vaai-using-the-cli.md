---
author: slowe
comments: true
date: 2010-10-29 16:02:58+00:00
layout: post
slug: disabling-vaai-using-the-cli
title: Disabling VAAI Using the CLI
wordpress_id: 2147
categories: Tutorial
tags:
- CLI
- Interoperability
- Storage
- Virtualization
- VMware
- vSphere
---

As a quick follow-up to yesterday's article about [interoperability between RecoverPoint and the vStorage APIs for Array Integration (VAAI)][1], I wanted to post a short "how to" on disabling VAAI for interoperability with RecoverPoint. I'll show you how to disable all three VAAI primitives, but keep in mind that only the hardware-accelerated copy and hardware-accelerated zero functions need to be disabled if you are using array-based splitters (all three need to be disabled with fabric splitters).

Given that the future of VMware vSphere is ESXi, I'm using the vSphere Management Assistant (vMA) here as the basis for disabling VAAI from the command-line interface (CLI).

To disable hardware-accelerated copy, use the following command:

	vicfg-advcfg --set 0 DataMover/HardwareAcceleratedMove --vihost <ESX/ESXi host to reconfigure> --server <vCenter Server> --username <vCenter Server username>

This will prompt for the password of the specified user account unless you've already configured some other form of authentication.

To disable hardware-accelerated zero, use this command:

	vicfg-advcfg --set 0 DataMover/HardwareAcceleratedInit --vihost <ESX/ESXi host to reconfigure> --server <vCenter Server> --username <vCenter Server username>

Finally, for the sake of completeness, here's how to disable the hardware-accelerated locking (note that RecoverPoint with array-based splitters **_does support_** this feature currently):

	vicfg-advcfg --set 0 VMFS3/HardwareAcceleratedLocking --vihost <ESX/ESXi host to reconfigure> --server <vCenter Server> --username <vCenter Server username>

I'm still chasing down possible ways to restrict the use of VAAI in a more granular fashion, as using the commands above disable VAAI functionality for the entire VMware ESX/ESXi host. As soon as I have more information, I'll post it here.

[1]: {% post_url 2010-10-28-recoverpoint-and-vaai-interoperability %}
