---
author: slowe
comments: false
date: 2006-05-09 18:19:21+00:00
layout: post
slug: follow-up-on-windows-server-2003-r2-schema
title: Follow Up on Windows Server 2003 R2 Schema
wordpress_id: 244
categories: Information
tags:
- ActiveDirectory
- Microsoft
- Windows
---

The issue I described in my original post regarding [upgrading the schema to support Windows Server 2003 R2][1] as a domain controller is getting more attention.

Jorge de Almeida Pinto, a Windows Server MVP, has created his own blog entry about the need to use `ADPrep.exe` from the _second_ CD, and has also pointed out that Microsoft has created a Knowledge Base article about the problem as well:

Error message when you run the Active Directory Installation Wizard: "The version of the Active Directory schema of the source forest is not compatible with the version of Active Directory on this computer"
<[http://support.microsoft.com/?kbid=917385](http://support.microsoft.com/?kbid=917385)>

Have a look at [Jorge's full weblog entry](http://blogs.dirteam.com/blogs/jorge/archive/2006/05/06/930.aspx), as he lists some other helpful information as well.

[1]: {% post_url 2006-04-21-windows-server-2003-r2-schema %}
