---
layout: post
title: 'iTerm: How to set tab name and color from command line'
date: '2014-11-11T16:52:00.000+03:00'
categories: Coding
comments: true
tags:
- iTerm
- bash
- MacOS
---

This function will set tab name and background color for current tab in iTerm. It uses [iTerm escape sequences](https://iterm2.com/documentation-escape-codes.html).

	set_title_and_color(){
	    echo -ne "\033]0;$1\007\033]6;1;bg;red;brightness;$2\a\033]6;1;bg;green;brightness;$3\a\033]6;1;bg;blue;brightness;$4\a"
	}

Usage:

	set_title_and_color 'tab name' red green blue
	
Where red, green and blue are numbers from 0 to 255 which represent tab color. Examples:

	set_title_and_color 'name 1' 255 0 0
	# Red tab background

	set_title_and_color name 255 255 0
	# Yellow tab background

Result:
![](/assets/images/2014/iterm_tab.png)
