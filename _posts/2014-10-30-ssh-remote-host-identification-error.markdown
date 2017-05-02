---
layout: post
title: 'Bash: SSH - avoiding ''remote host identification has changed'' error'
date: '2014-10-30T14:07:00.002+03:00'
categories: Coding
comments: true
tags:
- bash
---

If you use SSH for remote hosts management there may be the following scenario: your cloud provider gives you nodes with SSH access, you do something with them and then they got removed.

Most probably provider have limited pool of IP addresses and reuse them. So there may be case when you connect to newly created remote host, but its IP address was used early with other host which you connected to. In this case you will see exception like:

	WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
	IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!

The root cause is obvious - SSH stored public key for this host earlier and now tries to reuse it with new host.
How to avoid that? Just add

	Host *
		StrictHostKeyChecking no
		UserKnownHostsFile=/dev/null

into your ~/.ssh/config file. This will disable strict host key check for all the hosts. If you prefer to disable specified subnet only (200.200.* in an example), specify it like that:


	Host 200.200.*
		StrictHostKeyChecking no
		UserKnownHostsFile=/dev/null
