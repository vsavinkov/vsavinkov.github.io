---
layout: post
title: 'Bash: Fix keyboard layout (Punto Switcher-like)'
date: '2014-10-30T14:48:00.001+03:00'
categories: Coding
comments: true
tags:
- bash
- MacOS
---

The following script will transcript clipboard content from English keyboard layout to Russian and vice versa.

For example, 'Ghbdtn!' will be trabsformed into 'Привет!'. Note that transformation is MacBook Pro 2012 (and MacOS) specific. It should be amended for other devices/keyboards.

See script:

	fixlayout(){
	  en="qwertyuiop\[]asdfghjkl;'\zxcvbnm,.QWERTYUIOP{}ASDFGHJKL:\"|ZXCVBNM<>\@№%%^&*"
	  ru="йцукенгшщз\хъфывапролджэёячсмитьбюЙЦУКЕНГШЩЗХЪФЫВАПРОЛДЖ\ЭЁЯЧСМИТЬБЮ\"#$:,.;"
	  pbpaste | sed y=$en$ru=$ru$en= | pbcopy
	}

So, we just taking difference in English and Russian keyboard layouts into variable and transforming it.
