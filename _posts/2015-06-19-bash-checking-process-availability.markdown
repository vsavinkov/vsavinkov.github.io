---
layout: post
title: 'Bash: how to check process availability'
date: '2015-06-19T11:30:00.005+03:00'
categories: Coding
comments: true
tags:
- bash
---

If you have script which deploys some product / runs some service, you may need to check whether it’s actually started. For example:

    #check if some process is running
    if [ ps aux | grep $PROCESS_NAME -c == '0' ]; then
        echo Process not started
    else
        echo Process started!
    fi

    #check if some application occupied some port
    l_TELNET=echo "quit" | telnet 127.0.0.1 $PORT_NUMBER | grep "Escape character is"
    if [ “$?” -ne 0 ]; then
         sleep 1
    fi

But what if your script need to wait until application started? I suggest to use recurrent function to do that:

	check_whether_service_started(){
	  sleep 3
	  if [ ps aux | grep $PROCESS_NAME -c == '0' ]; then
		echo Waiting for process to start...
		check_whether_service_started
	  else
		echo Process is running.
	  fi
	}

It will wait for 3 seconds and recheck process availability until it will be running.
