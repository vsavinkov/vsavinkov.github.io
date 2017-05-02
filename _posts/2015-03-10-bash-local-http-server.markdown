---
layout: post
title: 'Bash: how to create local HTTP server to share files'
date: '2015-03-10T13:56:00.001+03:00'
categories: Coding
comments: true
tags:
- bash
- MacOS
---

The following script will create HTTP server on random port in range 1000-2000 and copy its URL to clipboard.

Would be useful to share files with someone from your subnet.
Usage: go to desired folder, run 'server' command, open URL from clipboard.

So we just set 'random' variable to random number from 1000 to 2000 and initiate HTTP server on port.

	alias ip="ifconfig|grep 'inet '|awk '{print \$2}'|grep -v '127.0.0.1'|grep -v '192.168'"

	server(){
	  number=$RANDOM; let "number %= 1000"; let "number += 1000"
	  echo 'http://'`ip`':'$number | pbcopy
	  python -m SimpleHTTPServer $number
	}
