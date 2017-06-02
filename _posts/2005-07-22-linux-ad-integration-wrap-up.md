---
author: slowe
comments: false
date: 2005-07-22 11:19:08+00:00
layout: post
slug: linux-ad-integration-wrap-up
title: Linux-AD Integration Wrap-Up
wordpress_id: 56
categories: Information
tags:
- Interoperability
- ActiveDirectory
- Kerberos
- LDAP
- Linux
- Microsoft
- Networking
- Windows
---

Well, my Linux-AD integration task is pretty much complete. I have three Linux servers authenticating via [Kerberos](http://web.mit.edu/kerberos/www) to Active Directory, and using LDAP for name/group resolution. Only one Linux server remains; I need to do some research on how [SASL](http://asg.web.cmu.edu/sasl/) with interact with PAM before I can switch over that particular server. My [OpenBSD](http://www.openbsd.org) server I'm going to leave alone for now; perhaps later I'll get it integrated as well.

Next, I think I'm going to see what is involved in using RADIUS to authenticate VPN tunnels on my hardware firewall.
