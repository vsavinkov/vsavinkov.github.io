---
layout: post
title: 'iTerm: how to open new tabs programmatically'
date: '2015-06-11T10:08:00.001+03:00'
categories: Coding
tags:
- iTerm
- bash
- MacOS
---

This bash function will open new tab in iTerm and execute command there.
Useful when you need to do something in several tabs (deploy applications, pull repos, etc.).

	tab() {
	  osascript </span>
		-e ‘activate application “iTerm”’ </span>
		-e ‘tell application “System Events” to keystroke “t” using command down’ </span>
		-e “tell application "iTerm" to tell session -1 of current terminal to write text "$1"”
	}

Can be modified to use regular Mac Terminal instead of iTerm - just change app name in 3rd string.

Examples:

	tab ‘cd ~/Projects; git pull’
	tab ‘ls’