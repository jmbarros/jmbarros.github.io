---
author: slowe
comments: true
date: 2017-01-03
layout: post
title: "My (Evolving) Multi-Platform Toolbelt"
categories: Information
tags:
- Linux
- Macintosh
- CLI
- Markdown
- Encryption
- Writing
- Messaging
---

A few days ago [I posted a tweet][link-1] about a new tool I'd (re-)discovered called `jrnl`. Someone [replied][link-2] to that tweet, asking me to list my "multi-platform toolbelt." While it's still evolving (every day!), I thought it might make for a good blog post. So, here's a list of my still-evolving multi-platform toolbelt.

* _Sublime Text:_ Over the last few years, I've moved to creating the vast majority of my content in Markdown (MultiMarkdown, to be more specific). At first I was using OS X-specific text editors (first TextMate 1.x, then BBEdit), but last year I switched to [Sublime Text][link-3]. Sublime Text supports OS X, Linux, and Windows. I don't have any Windows-based systems, so I only use it on OS X and Linux.

* _Wire:_ My use of [Wire][link-9] is still a bit limited, but only because the reach of the platform is also still a bit limited (this is a classical example of [network effect][link-8]). I'm currently using Wire on Linux and OS X, with plans to extend to iOS and Android. (If you're using Wire, feel free to look me up! My username is "scottslowe").

* _IMAP/SMTP:_ I've standardized on using IMAP/SMTP for all my e-mail accounts, which gives me quite a bit of flexibility in clients and OSes. It's very likely I'll standardize on [Thunderbird][link-11] (which supports OS X, Linux, and Windows), though I'm not quite there yet.

* _CalDAV/CardDAV:_ To help keep my contacts and calendars up to date on all my devices and platforms, I use CalDAV and CardDAV (on OS X, iOS, and Android---haven't found a good Linux client yet). [fruux.com][link-13] is my CalDAV/CardDAV provider (great service, by the way---highly recommended).

* _Unison:_ This [cross-platform file synchronization tool][link-5] helps keep my files in sync across my OS X and Linux systems.

* _Dropbox:_ [Dropbox][link-6] gives me access to non-confidential files from any of my devices or platforms (OS X, iOS, Android, and Linux).

* _VirtualBox:_ [VirtualBox][link-4] supports Linux, OS X, and Windows, providing one solution for hosted virtualization. It's not nearly as feature-rich as VMware Fusion or VMware Workstation, but given how I use hosted virtualization (see [this post][xref-1]) it's the best fit for _my_ workflows. (I still use [VMware Fusion][link-12] on my OS X workstation as well.)

* _jrnl:_ [`jrnl`][link-7] is a CLI tool is used for journaling, and has built-in support for encryption (a plus for me). The nice thing about `jrnl` which is itself multi-platform (runs on OS X and Linux) is that it also works with [Day One][link-10], which is a hugely-popular journaling tool for OS X (and one that I use).

* _Enpass:_ This multi-platform password manager supports OS X, Linux, iOS, and Android (other platforms are supported, but those four are the only platforms I use). It's not quite as feature-rich or polished as [1Password][link-14] (which supports OS X, Windows, iOS, and Android), but it will do for now. (Hey Agile Bits, all you need is a Linux version of 1Password---hint, hint.)

* _TaskPaper-formatted text files for task management:_ I've adopted the TaskPaper format for using plain text files for task management. Check out [this post][xref-2] for more details.

* _Firefox and Firefox Sync:_ For web browsing, I'm using [Mozilla Firefox][link-16] and Firefox Sync across Linux, OS X, iOS, and Android. I'll occasionally use Google Chrome as needed.

Some tools that I'm still evaluating:

* Hexchat (for IRC; works great on Linux and also supports OS X and Windows)
* XMind (for mind mapping; works OK on Linux but haven't tested it on OS X yet)

Well, that's it for now. I'll keep this post updated as my toolbelt evolves. In the meantime, if you have any suggestions for tools that I should evaluate, feel free to [hit me up on Twitter][link-15] (or Wire, for that matter).



[link-1]: https://twitter.com/scott_lowe/status/815836813583613954
[link-2]: https://twitter.com/mhmd_io/status/816175975792775168
[link-3]: http://www.sublimetext.com/
[link-4]: https://www.virtualbox.org/
[link-5]: http://www.cis.upenn.edu/~bcpierce/unison/
[link-6]: https://www.dropbox.com/
[link-7]: http://jrnl.sh/
[link-8]: https://en.wikipedia.org/wiki/Network_effect
[link-9]: https://wire.com/
[link-10]: http://dayoneapp.com/
[link-11]: https://www.mozilla.org/en-US/thunderbird/
[link-12]: http://www.vmware.com/products/fusion.html
[link-13]: https://fruux.com/
[link-14]: https://1password.com/
[link-15]: https://twitter.com/scott_lowe/
[link-16]: https://www.mozilla.org/en-US/firefox/
[xref-1]: {% post_url 2016-09-28-why-now-using-virtualbox-with-vagrant %}
[xref-2]: {% post_url 2017-01-19-plain-text-productivity-redux %}
