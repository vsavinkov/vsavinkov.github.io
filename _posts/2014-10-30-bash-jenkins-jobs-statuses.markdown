---
layout: post
title: 'Bash: Checking Jenkins jobs statuses from command line'
date: '2014-10-30T14:26:00.003+03:00'
categories: Coding
comments: true
tags:
- Jenkins
- bash
---

If you use Jenkins as Continue Integration tool then you may find useful to see a way to check statuses of its jobs from command line. Assuming that http://our-jenkins is an address of our server, see bash script:

	check_statuses(){
	  check_status(){
		wget http://your-jenkins/jenkins/job/$1/lastBuild/buildStatus &>temp
		if   [[ -n `cat temp | grep fol | grep blue`   ]]; then echo $2': blue'
		elif [[ -n `cat temp | grep fol | grep red`    ]]; then echo $2': red'
		elif [[ -n `cat temp | grep fol | grep yellow` ]]; then echo $2': yellow'
		fi
	  }
	  check_status FULL_JOB1_NAME Job1
	  check_status FULL_JOB1_NAME Job2
	  check_status FULL_JOB1_NAME Job3
	  rm buildStatus* smokes &>/dev/null
	}

Here FULL_JOB#_NAME is the name of job in Jenkins, Job# is friendly name to display. After execution script will provide results in the following way:

	Job1: blue
	Job2: blue
	Job3: red
