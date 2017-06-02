---
author: slowe
comments: true
date: 2012-12-10 09:00:00+00:00
layout: post
slug: update-on-markdown-and-boxcryptor-on-ios
title: Update on Markdown and BoxCryptor on iOS
wordpress_id: 3006
categories: Information
tags:
- Encryption
- Interoperability
- Macintosh
- OSS
- Storage
- Markdown
---

A short while ago, I talked about [how to add client-side encryption to Dropbox using EncFS][1]. In that post, I suggested using BoxCryptor to access your encrypted files. A short time later, though, I uncovered [a potential issue][2] with (what I thought to be) BoxCryptor. I have an update on that issue.

In case you haven't read the comments to [the article about the potential BoxCryptor-Markdown problem][2], it turns out that the problem with using Markdown files with BoxCryptor doesn't lie with BoxCryptor---it lies with Byword, the Markdown editor I was using on iOS. Robert, founder of BoxCryptor, suggested that Byword doesn't properly register the necessary handlers for Markdown files, and that's why BoxCryptor can't preview the files or use "Open In" functionality. On his suggestion, I tried [Textastic](http://www.textasticapp.com/).

It works flawlessly. I can preview Markdown files in the iOS BoxCryptor client, then use "Open In" to send the Markdown files to Textastic for editing. I can even create new Markdown files in Textastic and then send them to BoxCryptor for encrypted upload to Dropbox (where I can, quite naturally, open them using my EncFS filesystem on my Mac systems). Very nice!

If you are thinking about using EncFS with Dropbox and using BoxCryptor to access those files from iOS, and those files are text-based files (like Markdown, plain text, HTML, and similar file formats), I highly recommend Textastic.

[1]: {% post_url 2012-11-23-using-encfs-with-dropbox-and-boxcryptor %}
[2]: {% post_url 2012-11-30-problem-with-markdown-files-in-boxcryptor-on-ios %}
