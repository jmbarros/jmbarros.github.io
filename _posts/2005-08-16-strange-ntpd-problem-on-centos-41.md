---
author: slowe
comments: false
date: 2005-08-16 23:58:48+00:00
layout: post
slug: strange-ntpd-problem-on-centos-41
title: Strange NTPd Problem on CentOS 4.1
wordpress_id: 76
categories: Rant
tags:
- Linux
---

So I've been working with [CentOS](http://www.centos.org/), the "free as in free beer" equivalent of Red Hat Enterprise Linux, and for the most part I like it. (See [here]({{site.url}}/2005/08/08/brief-impressions-of-centos-41/) for some additional comments about CentOS 4.1.) However, I've run into this strange problem with NTPd.

The problem is it doesn't work. Yes, I've added the appropriate rules in iptables. Yes, the NTPd daemon is running. Yes, I've checked connectivity to the time server with which I am trying to synchronize. The ntpdate utility works like a champ, but NTPd just won't keep the server's time synchronized. OK, am I missing something here? I have [OpenBSD](http://www.openbsd.org/) and Red Hat Linux 9.0 servers that synchronize just fine, but not this server.

Finally, fed up with the problems, I just scheduled an hourly cron job with ntpdate. It's not ideal, but it works.
