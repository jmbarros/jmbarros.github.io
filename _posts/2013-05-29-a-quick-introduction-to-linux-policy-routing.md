---
author: slowe
comments: true
date: 2013-05-29 09:00:00+00:00
layout: post
slug: a-quick-introduction-to-linux-policy-routing
title: A Quick Introduction to Linux Policy Routing
wordpress_id: 3193
categories: Education
tags:
- CLI
- Linux
- Networking
- Ubuntu
---

In this post, I'm going to introduce you to policy routing as implemented in recent versions of Ubuntu Linux (and possibly other Linux distributions as well, but I'll be using Ubuntu 12.04 LTS). Policy routing actually allows us a great deal of flexibility in how we direct traffic out of a Linux host; I'll discuss a rather practical application of this configuration in a future blog post. For now, though, let's just focus on how to configure policy routing.

There are a couple parts involved in policy routing:

* _Policy routing tables:_ Linux comes with three by default: local (which cannot be modified or deleted), main, and default. Somewhat unintuitively, routes added to the system without a routing table specified go to the main table, not the default table.

* _Policy routing rules:_ Again, Linux comes with three rules, one for each of the default routing tables.

In order for us to leverage policy routing for our purposes, we need to do three things:

1. We need to create a custom policy routing table.

2. We need to create one or more custom policy routing rules.

3. We need to populate the custom policy routing table with routes.

Let's look at each of these steps separately.

## Creating a Custom Policy Routing Table

The first step is to create a custom policy routing table. Each table is represented by an entry in the file `/etc/iproute2/rt_tables`, so creating a new table is generally accomplished using a command like this:

    echo 200 custom >> /etc/iproute2/rt_tables

This creates the table with the ID 200 and the name "custom". You'll reference this name later as you create the rules and populate the table with routes, so make note of it. Because this entry is contained in the `rt_tables` file, it will be persistent across reboots.

## Creating Policy Routing Rules

The next step is to create the policy routing rules that will tell the system which table to use to determine the correct route. In this particular case, I'm going to use the source address (i.e., the originating address for the traffic) as the determining factor in the rule. This is a common application of policy routing, and for that reason it's often referred to as _source routing._

To create the policy routing rule, use this command:

    ip rule add from <source address> lookup <table name>

Let's say that we wanted to create a rule that told the system to use the "custom" table we created earlier for all traffic originating from the source address 192.168.30.200. The command would look like this:

    ip rule add from 192.168.30.200 lookup custom

You can see all the policy routing rules that are currently in effect using this command:

    ip rule list

As I mentioned in the beginning of this article, there are default rules that govern the use of the local, main, and default tables (these are the built-in tables). Once you've added your rule, you should see it listed there as well.

There is a problem here, though: rules created this way are ephemeral and will disappear when the system is restarted (or when the networking is restarted). To make the rules persist, add a line like this to `/etc/network/interfaces`:

    post-up ip rule add from 192.168.30.200 lookup custom

You'd want to place this line in the configuration stanza that configures the interface with the address 192.168.30.200. With this line in place, the rule should persist across reboots or across network restarts.

## Populating the Routing Table

Once we have the custom policy routing table created and a rule defined that directs the system to use it, we need to populate the table with the correct routes. The generic command to do this is the `ip route add` command, but with a specific `table` parameter added.

Using our previous example, let's say we wanted to add a default route that was specific to traffic originating from 192.168.30.200. We've already created a custom policy routing table, and we have a rule that directs the system to use that table for traffic originating from that address. To add a new default route specifically for that interface, you'd use this command:

    ip route add default via 192.168.30.1 dev eth1 table custom

Naturally, you'd want to substitute the correct default gateway for 192.168.30.1 and the correct interface for eth1 in the above command, but this should give you the right idea. Of course, you don't have to use default routes; you could install specific routes into the custom policy routing table as well. This also works on VLAN sub-interfaces, so you could create per-VLAN routing tables:

    ip route add default via 192.168.30.1 dev eth0.30 table vlan30

This command installs a default route for the 192.168.30.x interface on VLAN 30, using a table named "vlan30" (note that the table needs to created before you can add routes to it, as far as I can tell).

As with the policy routing tables, routes added this way are not persistent, so you'll want to make them persistent by adding a line like this to your `/etc/network/interfaces` configuration file:

    post-up ip route add default via 192.168.30.1 dev eth1 table custom

This will ensure that the appropriate routes are added to the appropriate policy routing table when the corresponding network interface is brought up.

## Summary

There's a great deal more functionality possible in policy routing, but this at least gives you the basics you need to understand how it works. In a future post, I'll provide a specific use case where this functionality could be put to work. In the meantime, feel free to share any corrections, clarifications, questions, or thoughts in the comments below.
