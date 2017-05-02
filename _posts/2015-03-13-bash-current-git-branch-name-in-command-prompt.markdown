---
layout: post
title: 'Bash: how to get current git branch name in command prompt'
date: '2015-03-13T17:39:00.001+03:00'
categories: Coding
comments: true
tags:
- bash
- Git
---

If you use git and its ‘branches’ feature in your project then this method would be useful for you.
Add the following to your .bash_profile (or .bashrc on Ubuntu):

	get_git_branch() {
     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
    }
	PS1='[\e[1;34m]\W[\e[0m]$(get_git_branch) '

You can replace 4th string by your own prompt, just add $(get_git_branch) there.
Now your command prompt will contain current git branch name. If you are not in git repository then regular command prompt will appear.
