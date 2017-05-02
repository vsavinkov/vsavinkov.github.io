---
layout: post
title: 'Bash: checking internet connection speed from command line'
date:   2017-05-02 14:00:00 +0300
categories: Coding
comments: true
tags:
- bash
---

Here are several ways to check your internet speed from console.

### Simple
Just use wget and check how fast it downloads file of decent size:

50MB:

    wget -O /dev/null http://lg.stackdata.net/50MB.test

500MB:

    wget -O/dev/null http://speedtest.wdc01.softlayer.com/downloads/test500.zip

### Scripted
It uses speedtest.net:

    curl -s "https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py" | python

### Packaged
Uses speedtest.net too.
Ubuntu:

	sudo apt-get install speedtest-cli
	speedtest-cli

Mac:

	brew install speedtest-cli
	speedtest-cli
