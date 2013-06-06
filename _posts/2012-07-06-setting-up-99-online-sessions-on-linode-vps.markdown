---
layout: post
published: false
title: "Setting up 99% online sessions on Linode VPS"
date: "Fri Jul 06 20:37:09 -0700 2012"
---

This has been now exlipsed by just using Gmail etc. The only thing I required was Gmail.

ssh root@XX.XXX.XXX.XXX
echo 'acidity' > /etc/hosts
dpkg-configure tzdata
apt-get update
  #Setup a timer
apt-get upgrade --show-upgraded
adduser riteshn
vim /etc/sudoers
  # root, riteshn ALL=(ALL:ALL) ALL
  #preferred way

ssh-copy-id -i ~/.ssh/id_rsa riteshn@XX.....

#eventually you might want to use
http://phildawson.tumblr.com/post/484798267/ssh-copy-id-in-mac-os-x



# On your local machine
cat ~/.ssh/id_rsa.pub | ssh riteshn@66.175.218.116 'cat >>
~/.ssh/authorized_keys'

Update /etc/ssh/sshd_config,
and set: PasswordAuthentication no
ChallengeResponseAuthentication no

ONLY if you’ve created a new user and given them sudo permissions should you
modify this line:

PermitRootLogin no
Reload your sshd config file (using Ubuntu’s upstart):

$ sudo service ssh reload

... logout ... login again

sudo apt-get install git zsh ruby rubygems rake tmux mutt-patched urlview lynx weechat bitlbee
newsbeuter
chsh -s /usr/bin/zsh

clone src
clone oh-my-zsh

cd src/dotconffiles
./bootstrap.sh

-- mutt gave: http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=664249

turned out that I didnt, set the /etc/hostname

http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=664249




Reference
---
http://library.linode.com/getting-started#sph_setting-the-hostname


