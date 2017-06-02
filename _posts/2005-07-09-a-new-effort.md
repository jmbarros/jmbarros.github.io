---
author: slowe
comments: false
date: 2005-07-09 23:09:53+00:00
layout: post
slug: a-new-effort
title: A New Effort
wordpress_id: 39
categories: Information
tags:
- Kerberos
- LDAP
- Linux
- Microsoft
- Windows
- Interoperability
- ActiveDirectory
---

I suppose I should be finishing one project before starting another, but I can't help myself. I'm going to take on the project of integrating my Linux systems with Microsoft Active Directory, so that a single Active Directory account can be used to authenticate to both Windows-based systems as well as Linux-based systems on our network.

This new effort comes while I have yet to finish my [projects]({{site.url}}/2005/05/13/miscellaneous-projects/) on Squid log analysis tools or an internal news server running INN. At least I did get [Perdition working]({{site.url}}/2005/05/15/perdition-working-now/) as expected, and figured out how to get [Mail.app to use STARTTLS with IMAP4]({{site.url}}/2005/07/02/starttls-and-imap-in-mailapp/).

A couple of the resources I'm using for this effort are bookmarked in my [del.icio.us](http://del.icio.us/slowe/) bookmark list. I'll be adding more there as I find them.

I also have yet to decide if I will use Samba/Winbind or LDAP to handle the cross-platform authentication. I'd love to hear any comments or feedback in this regard.
