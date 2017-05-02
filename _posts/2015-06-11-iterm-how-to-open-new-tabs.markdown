---
layout: post
title: 'iTerm: how to open new tabs programmatically'
date: '2015-06-11T10:08:00.001+03:00'
categories: Coding
comments: true
tags:
- iTerm
- bash
- MacOS
---

This bash function will open new tab in iTerm and execute command there.
Useful when you need to do something in several tabs (deploy applications, pull repos, etc.).

	tab() {
        iterm() {
            osascript -e "tell application \"System Events\" to tell process \"iTerm\" to $1"
        }
        iterm 'keystroke "t" using command down'; iterm "keystroke \"$1\""; iterm 'key code 52'
    }

Can be modified to use regular Mac Terminal instead of iTerm - just change app name in 3rd string.

Examples:

	tab 'cd ~/Projects; git pull --rebase'
	tab 'ls'
