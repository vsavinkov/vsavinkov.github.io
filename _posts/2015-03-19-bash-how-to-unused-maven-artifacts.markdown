---
layout: post
title: 'Bash: how to remove unused Maven artifacts'
date: '2015-03-19T11:47:00.000+03:00'
categories: Coding
comments: true
tags:
- bash
- maven
---

The following script will remove all but latest artifacts downloaded by Maven from your local repo (~/.m2). This will save disk space since maven don’t remove old artifacts automatically. Just add paths to desired artifacts instead of underlined paths.

	clear_artifacts(){
	  delete_all_but_latest(){
		pushd ~/.m2/repository/$1
		ls -t | tail +2 | tail -r | xargs rm -r
		popd
	  }
	  delete_all_but_latest com/name/path/to/artifact1
	  delete_all_but_latest com/name/path/to/artifact3
	  delete_all_but_latest com/name/path/to/artifact2
	}
