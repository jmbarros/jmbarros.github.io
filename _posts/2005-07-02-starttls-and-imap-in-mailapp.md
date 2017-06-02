---
author: slowe
comments: false
date: 2005-07-02 20:47:16+00:00
layout: post
slug: starttls-and-imap-in-mailapp
title: STARTTLS and IMAP in Mail.app
wordpress_id: 30
categories: Information
tags:
- Encryption
- IMAP
- Macintosh
- Messaging
- Microsoft
- SSL
---

I [blogged]({{site.url}}/2005/05/14/nonstandard-implementations/) earlier about my frustration with the [Mac OS X](http://www.apple.com/macosx/) Mail.app mail client and its apparent lack of STARTTLS support with IMAP4. Well, on a whim today I decided to take this issue back up again.

Since [Microsoft Exchange](http://www.microsoft.com/exchange/) does not support STARTTLS, I had to use [Perdition](http://www.vergenet.net/linux/perdition/) as an IMAP proxy in front of Exchange. Earlier attempts to get Mail.app to do STARTTLS had failed (not sure why), but today I decided to try changing the IMAP port from 993 (the default when you check the "Use SSL" box) to 143 (the standard IMAP4 port). Oddly enough, it seemed to work!

Curious to find out for sure, I trotted out `tcpdump` on the mail gateway running Perdition to capture traffic to/from Mail.app and to/from the back end mail server. The traffic to/from the back end mail server was transmitted in the clear (I used plain text messages so that I could see the content), but the traffic to/from Mail.app was not readable. I also saw Mail.app issue a CAPABILITY command, then issue a STARTTLS command. Bingo!

So, it appears that Mail.app does indeed support STARTTLS for IMAP, but only if you set the port number back to 143 after checking the "Use SSL" checkbox.
