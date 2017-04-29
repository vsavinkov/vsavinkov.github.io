---
layout: post
title: 'Bash: how to control programmable surge protector from console'
date: '2015-12-03T22:26:00.001+03:00'
categories: Coding
comments: true
tags:
- bash
---

If you have programmable LAN-controlled surge protector Energenie EG-PMS2-LAN, then you, like me, may be disappointed by fact that it only can be controlled via (ugly) web interface.

Here is a bash function which allow you to do that via console:

	powerlan() {
	  curl -f -d “pw=1”       http://192.168.0.2/login.html>/dev/null 2>/dev/null
	  curl -f -d “ctl”$1”=”$2 http://192.168.0.2/>/dev/null 2>/dev/null
	}

Here:
192.168.0.2 - IP address of LAN surge protector;
1 (in “pw=1”) - password for it (1 is default password) 

Usage:

	powerlan 1 1 #turns on socket 1
	powerlan 1 0 #turns off socket 1
	powerlan 2 1 #turns on socket 2

…and so on.
