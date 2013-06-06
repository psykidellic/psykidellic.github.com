---
layout: post
title: "rsyslog and absence of /var/log/messages in Ubuntu"
tags: [administration]
---
{% include JB/setup %}

So I had to install LDAP on a recent Oneric machine. To see the logs, you have to set logLevel in slapd.conf which should put the logs in /var/log/syslog . Now if you want to log it separately in say /var/log/ldap.log - you have to update /etc/syslog.conf - but on my Oneric there is no /etc/syslog.conf. Turns out with Ubuntu Natty, we use rsyslog by default.

So we have to update /etc/rsyslog.conf

local4.*

Where is /var/log/messages
--------------------------

Another change with Natty is that there is no /var/log/messages and everything has been consolidated to log into **/var/log/syslog**.