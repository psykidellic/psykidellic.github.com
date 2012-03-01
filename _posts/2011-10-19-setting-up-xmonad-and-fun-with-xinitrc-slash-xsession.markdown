---
layout: post
title: Setting up Xmonad and fun with xinitrc/xsession
post-link:
tags: [programming]
---
Finally, after years of procastinating, I finally installed Xmonad on a
new virtual machine that I have been setting up for another project.
Since I have been doing almost everything new in the sphere of
technology, might as well start a new experience with desktop
environment.

Setting up Xmonad was a breeze with apt-get but the next step of setting
up GDM to use xmonad for my session turned out to be more fun then I had
imagined. When you start your Ubuntu you are presented with the login
screen by GNOME. At this time, you can select various session/profile
that you would like to use with the login. This information comes from
files at `/usr/share/xession`. One sample:

    [Desktop Entry]
    Encoding=UTF-8
    Name=XMonad
    Comment=Lightweight tiling window manager
    Exec=xmonad
    Icon=xmonad.png
    Type=XSession

The above one is installed with xmonad and selecting the session while
logging gives you the simplest `xmonad` installation. Though this works,
I wanted to configure something extra to my needs e.g. `gnome-session`
as it some of the window drawing look nicer (specifically Firefox,
Chrome). So thinking that just like back in the days, I have to setup
`.xinitrc` file and it will work, I went ahead and created one with the
details I needed. Logout and login and nothing happens. Figuring, I did
something wrong I spent sometime making sure the config was correct to
the best of my knowledge. Eventually, after much hassles and Googling,
figured out Ubuntu uses `$HOME/.xsession` file. With the knowledge, just
doing:

    cp .xinitrc .xsession

and selecting `User Defined Session` in the login window and everybody
is happy. In my last 30hours or about of using
[[http://www.xmonad.org][]][], I am already loving it. No more time
spent on resizing and moving around windows on my big monitor. Terminal
is just `mod+space+return` away and xterm with **Droid Sans Mono** is
simmply gorgeous.

  [http://www.xmonad.org]: http://www.xmonad.org
  [[http://www.xmonad.org][]]: xmonad
