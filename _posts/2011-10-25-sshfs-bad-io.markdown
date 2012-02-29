---
layout: post
title: ssfs-bad-io
date: 2011-10-25 14:29
post-link:
---
So at work, we have a flow where mount one folder over sshfs and almost
everybody has a shell window open all time to work on this folder.
Though recently, we had a network change and after I come get back to
work, even simple commands like `cp` or `ls` would just stuck and even
on parent folder of the mount. Doing a quick:

    ps aux | grep CURRENT_COMMAND

shows me that the process is hung with state **S+** which according to
manual means:

    S: Interruptible sleep

Having a hunch that this is definitely related to sshfs and the network
issues. After some time of Googling, came across [bug report on
sshfs][]. I did this to get out of the problem:

    $ ps aux | grep sshfs
    $ kill -9 PID
    $ fusermount -u MOUNT
    #You need to do the above or you will get:
    #ls: cannot access manage: Transport endpoint is not connected
    $ sshfs AND_THE_REST

Hope it helps.

  [bug report on sshfs]: http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=565229

