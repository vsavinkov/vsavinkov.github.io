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
Usage: go to desired folder, run ‘server’ command, open URL from clipboard.

Description:
2nd string will set ‘random’ variable to random number from 1000 to 2000.
3rd one will paste your IP address with ‘http://’ prefix and :[random] postfix to clipboard.
4th will initiate HTTP server.

	server(){
	  number=$RANDOM; let “number %= 1000”; let “number += 1000”
	  echo ‘http://’ifconfig|grep 'inet '|awk '{print \$2}'|grep -v '127.0.0.1's’:’$number | pbcopy
	  python -m SimpleHTTPServer $number
	}
