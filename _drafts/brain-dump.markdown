---
title: brain dump
post-link:
---
weTouchscreen
-- Comptt/Similar - kivy etc.

Cloud based MySQL/PostgreSQL monitoring?
-- LogicMonitor
-- NewRelic

Maybe just port Monyog?

Instagram like application for receipts. I could not remember from Hawaii.
-- Question - is it legal to use the photograph? What if we lose the receipt but the things will be kept in the cloud.
-- There is expensify,

Footytube like for crickets.
-- Where is the content? Crawling will not work. Get news broadcasters?
-- there is always mycrickethighlights

 imdb for indian movies
I could not fine

Marketplace for digital touchups and small things. Apart from touchups - one could ask for hero  unit images, icons etc.
-- http://www.wowapic.com/
-- http://www.blowuplab.com/page39/page39.html?gclid=CKyGrO74160CFaEZQgoda1P66w
-- http://www.digitalpickle.com/prices/index.shtml
http://www.wowapic.com/affiliates.php
http://pixsharp.com/index.php/photo-enhancement/animal-retouching/ - one can use those resources to make a feature plan.

 Maybe just start with listing and add braintree.


Various crowdsourced work ... adding to that ... jingle maker etc.

www.expressinmusic.com
www.userfarm.com
www.poptent.com

-- specifically for animated films. One could be like 5second videos.

Atfer you have excelled in it - look into lawpivot and ask dad. Then you can create the app very quickly.

Look into end to end phone connection support so that they can just call the lawyer. Ask uday as he has lot of experience in it.


Payment processing in India
http://www.startupdunia.com/india-startups/comparison-of-payment-gateways-in-india-2087


... For crowdsourcing: playlist.com.
... Religious music
...

Free trial product as shown by Pete Atkins @ Meraki. I am pretty sure every company is getting into it. So build a centralized process? We could do lot of BI on it....And tight integration with Salesforce?

Social customer service like Github is for social coding. I believe tello.com is doing something like it.

Real technical...

chas

>> While having lunch we discussed about job retention. How some of the sales people are leaving. We can manage and keep track of subejcts like, what makes people join us. Keep a company wide statistics. One could compare it to employinsight.com Make it easier for events like: http://www.facebook.com/Engineering/posts/124940890965225

>> Crate a more technical product, funkload.com


Like playing talents: http://gridroom.com/

http://www.ship-rack.com/screenshots

>>> commands:

Time tracking softwares as discussed with Ansul: http://www.exaktime.com/lp/reality?ibp-adgroup=LP80&gclid=CLXslamFya4CFYEBRQodbGHFAg,

https://www.toggl.com/
http://www.paymo.biz/ - a quick qould be for outsourcing companies who work on multiple prokects. They might just want to keep track and create invoice?
http://en.wikipedia.org/wiki/Comparison_of_time_tracking_software
Like playing talents: http://gridroom.com/

ms/ruby-1.9.2-p290/gems/capistrano-2.11.2/lib/capistrano/server_definition.rb:16:in `[]': wrong number of arguments(2 for 1) (ArgumentError)

 exception while rolling back: TypeError, can't convert Symbol into String - this rfequired the necessary / at the end.

 Password: /Users/riteshn/.rvm/gems/ruby-1.9.2-p290/gems/capistrano-2.11.2/lib/capistrano/configuration/connections.rb:128:in `join': Interrupt

 - i had to add the keys ssh-add ~/.

http://stackoverflow.com/questions/6310086/capistrano-git-deployment-could-not-create-work-tree-dir-permission-denied - got similar permission error like.

 * executing "if [ -d /home/ubuntu/rangeela/shared/cached-copy ]; then cd /home/ubuntu/rangeela/shared/cached-copy && git fetch -q origin && git fetch --tags -q origin && git reset -q --hard 4815db2d361a5d8a6b420626d8e57031dc8fc269 && git clean -q -d -x -f; else git clone -q git@bitbucket.org:psykidellic/rangeela.git /home/ubuntu/rangeela/shared/cached-copy && cd /home/ubuntu/rangeela/shared/cached-copy && git checkout -q -b deploy 4815db2d361a5d8a6b420626d8e57031dc8fc269; fi"
    servers: ["184.169.133.80"]
    [184.169.133.80] executing command
    [184.169.133.80] sh -c 'if [ -d /home/ubuntu/rangeela/shared/cached-copy ]; then cd /home/ubuntu/rangeela/shared/cached-copy && git fetch -q origin && git fetch --tags -q origin && git reset -q --hard 4815db2d361a5d8a6b420626d8e57031dc8fc269 && git clean -q -d -x -f; else git clone -q git@bitbucket.org:psykidellic/rangeela.git /home/ubuntu/rangeela/shared/cached-copy && cd /home/ubuntu/rangeela/shared/cached-copy && git checkout -q -b deploy 4815db2d361a5d8a6b420626d8e57031dc8fc269; fi'
 ** [184.169.133.80 :: out] fatal: could not create work tree dir '/home/ubuntu/rangeela/shared/cached-copy'.: Permission denied
 ** [184.169.133.80 :: out]




sudo -p 'sudo password: ' mkdir -p /home/ubuntu/rangeela /home/ubuntu/rangeela/releases /home/ubuntu/rangeela/shared /home/ubuntu/rangeela/shared/system /home/ubuntu/rangeela/shared/log /home/ubuntu/rangeela/shared/pids"



drwxrwxr-x  5 root   root   4096 2012-03-03 09:22 .
drwxrwxr-x 16 ubuntu ubuntu 4096 2012-03-03 09:22 ..
drwxrwxr-x  2 root   root   4096 2012-03-03 09:22 log
drwxrwxr-x  2 root   root   4096 2012-03-03 09:22 pids
drwxrwxr-x  2 root   root   4096 2012-03-03 09:22 system

bundle not found????

https://rvm.beginrescueend.com/integration/capistrano/
 sh: bundle: command not found

 had to update nginx to current folder.

 after "deploy", "deploy:restart"

Build upon the jeyull CMS

-- www.page.ly
-- www.squarespace.com
-- www.harmony.com


Hahaha, Finarta comptt?

http://www.artlogic.net/artlogic/costs/


 >>> Some this like open feedback publishing system. Maybe check out with dad.

 Trying to figure out the rails asset pipeline ordering.

>>>

rsyslog and absence of /var/log/messages in Ubuntu

So I had to install LDAP on a recent Oneric machine. To see the logs, you have to set logLevel in slapd.conf which should put the logs in /var/log/syslog . Now if you want to log it separately in say /var/log/ldap.log - you have to update /etc/syslog.conf - but on my Oneric there is no /etc/syslog.conf. Turns out with Ubuntu Natty, we use rsyslog by default.

So we have to update /etc/rsyslog.conf

local4.*


Download

Where is /var/log/messages
--------------------------

Another change with Natty is that there is no /var/log/messages and everything has been consolidated to log into **/var/log/syslog**.

Installing Kayboard Layout

Download it from

https://public.me.com/thgewecke



select product_id,n.id,mac,last_reported_at from nodes n,node_stats s where n.id=s.id and product_id in (select id from products where is_wired) and mac like '00:18:0a:00%' and last_reported_at is null and n.network_id = 31;

...

Multiple avatar that is randomly selected for your blog.

