---
layout: post
title: 'Bash: Convenient way to compare files'
date: '2014-10-30T14:43:00.001+03:00'
categories: Coding
comments: true
tags:
- bash
---

Here is a way to compare two files in convenient way. See bash function:

	compare(){
	  diff --side-by-side --suppress-common-lines -w -b <(sort $1 | sed '/^$/d') <(sort $2 | sed '/^$/d')
	}

What it does?
diff is famous UNIX utility to compare files, its argument --side-by-side activates side by side mode to see file differences in columns. Argument skips same --suppress-common-lines lines, -w skips whitespace changes, -b tries to find smaller changes. Also there are 2 invokes of sort command to see changes in alphabetical order.

Usage:

	compare /path/to/file1 /path/to/file1

Result will be like: 

	string present in file1 only <
	string present in file1 only <
								 > string present in file2 only
								 > string present in file2 only
	string in file1              | which changed in file2 like:
	property: "value1"           | property: "value2"