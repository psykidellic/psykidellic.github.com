---
layout: post
published: true
title: "One terminal to rule them all - for the power users"
date: "Thu Jun 28 14:04:59 -0700 2012"
---

Couple of weeks back, while researching on completely unrelated topic, I came
across various blog/references espousing the effectiveness of working on command
line. Over years, I have noticed and have been fascinated by many who have
absolutely fantastic in getting their job done from the command line. For as
long as I remember, I have been thinking of moving to similar workflow but due
to one reason or another, never took the effort to spend time to set it up.

Workflow
========

* Editor for coding (since I have been doing Python/Ruby/Scala development
  lately, complete IDE have become redundant).
* Browser for GMail, Google Reader, Twitter, Facebook, Reddit, Browsing.
* The venerable Terminal.

Problems
========

Overtime, I tried using tools specific to things like Twitter, Facebook but the
hassle of learning another tool, dealing with Adobe Air updates just made the
whole process painful. Couple with that Mac updates needing restart, I would
have to reopen everything again. Yes, there are ways/tools to set the apps that
have to started etc. but overtime they are just hassle to maintain. I spent
some time learning Quicksilver when I got my first Mac during college but since
I had to move to use Linux almost exclusively, I never got the chance to master
it.

I still have vivid memories of my number of attempts of getting my config files
into code repository with varying level of success. With each app keeping
configs in their own way - maintaining a GIT version is almost always
impossible.

Last but not least, doing Alt-Tab to browse between myriad of apps plus the keys
to jump to each applications window/buffer takes time.

Setup
=====

After reading over various setups, basically the setup boiled down to:

* iTerm.app - Really, Terminal.app is crappy. Linux/\*nix users are fine.
* Homebrew - If you are on Mac. Again, Linux/\*nix users are fine.
* MacVim - I dont use the GUI version but the homebrew version comes bundled
  with lot of goodies. Again, Linux/\*nix users with latest version of vim would
  be fine.
* tmux
  * Mac users may also want to read upon and install reattach-to-usernamespace
  although I have yet to have use of it but probably as I use this setup, more I
  will face the hurdle.
* mutt with sidebar-patch
* WeeChat and BitlBee - irc/gtalk/twitter
* Newsbeuter - Newsreader
* cmus - Music player

Personally, I like to have the same color scheme across all my apps but
different people may have different likings. I use zenburn everywhere (there are
themes for iTerm/various terminals/vim) but people have been reviewing
solarized/tomorrow a lot.

Use your favorite package manager to install the above applications. Needless,
to say - it is given that you setup all of your dotconf into a code repository.
1000s of people have released their dotconf files on the internet. Its very
interesting read through and see how people work. I would say 80% of things in
my conf are picked up from others.

**It is important that you setup your terminal colortheme. Just setting up your
editor or other app themes will not work.**

NOTE: In this post, I would explain some of the issues that I faced while having the
setup on my Mac. Most of them was because of iTerm behaves and default function
keys of Mac. You may or may not have these issues.

Common buffer/window/pane movement
==================================

`a.k.a - how I like to move around`

As you would notice after getting using all the apps, there is a notion of
splitting the main view window into sub windows. iTerm/tmux calls it
windows/panes, vim has its windows which you can split, weechat with its windows
etc. Its easy if you setup a common pattern in moving between them. An important
thing to remember is to choose different keystrokes so that one app does not eat
other apps key strokes. After long trial and error, I use the following
keybindings for my window/pane movement.

{% highlight console %}
"iTerm
"Lot of command line apps do not recognise the Mac `cmd` so it helps
"to use them for Cocoa apps.
Cmd-},{ - Move focus. I rarely jump to a specific window. Its just easier to
press the key couple of times more.

"vim
The standard Ctrl+W keys. Its just not difficult.

"tmux - try to map the vim movement commands
<prefix>h,j,k,l - left, down, top, right

"weechat
"It really helps to read through: http://www.weechat.org/files/doc/devel/weechat_quickstart.en.html
<ctrl>h,j,k,l - left, down, top, right
{% endhighlight %}

My workflow
===========

Alright, the result. This is what am using these days:

* Three tmux session running. Work development, hobby development, personal
  stuff (email, chat etc).
* Two tmux tabs running (work or hobby development) and personal session.
* Work session has the root folder of the project/vim plus panes for testing,
  shell etc.
* mutt/weechat/newsbeuter and cmus/blog session.
* I tend to create a new iTerm tab for something quick and dirty.
  new window.

If I am working on backend project or something which does not involve constant
look up of browser. I like to use the `full screen` mode of iTerm. When I go
home, I just detach my tmux session and start the same from home machine. And
everything is as where I left. No need to reopen things in the browser, no need
to worry about restarts. Sometimes, when I do need to restart the machine or
session, I can get back up and running with scripts like:

{% highlight bash %}
tmux start-server
tmux new-session -d -s personal -n mutt
tmux new-window -t personal:2 -n chat
tmux new-window -t personal:3 -n news
tmux new-window -t personal:4 -n bitlbee
tmux new-window -t personal:5 -n blog

tmux send-keys -t personal:1 'mutt' C-m
tmux send-keys -t personal:4 'bitlbee -D -n -v' C-m
tmux send-keys -t personal:2 'weechat-curses -a' C-m
tmux send-keys -t personal:3 'newsbeuter' C-m
tmux send-keys -t personal:5 'blog; tmux split-window -h; cmus' C-m

tmux select-window -t personal:1
tmux attach-session -d -t personal
{% endhighlight %}

Shifting between various window is just a matter of right combination of
keyboard movements. They may seem daunting but you will be amazed how powerful
our brain is to grasp new stuff with enough training. I have been using this
setup for just two weeks and I seem to recall most of the commands on instinct.

I hear you say "Pictures are worth thousand words".

<iframe class="imgur-album" width="100%" height="550" frameborder="0"
src="http://imgur.com/a/3ODp7/embed"></iframe>

_Edit:_ Added images on 2012-07-05 @ 13:32PST.

Gotchas & Helpful References
============================

* [Why this setup is awesome](http://www.drbunsen.org/text-triumvirate.html#fn:1)
* In your iTerm Profile preferences, select terminal to be reported as
  `xterm-256color` and under `Keys` - Let option key acts as +Esc. This wil make
  your life with command line apps much easier.
* Make sure you upgrade your brew setup using `brew update`. The version I had
  was having problem compiling WeeChat with "--perl" and thus none of the perl
  scripts were running. They have support for other languages but until and
  unless, you have some specific needs - I have not seen much documentation on
  other language scripts for WeeChat.
* [Setting up mutt with
  GMail](http://crunchbanglinux.org/wiki/howto/howto_setup_mutt_with_gmail_imap)
* [Github issue #4383](https://github.com/mxcl/homebrew/pull/4383) - for patches
  to install STFL/newsbeuter.
* Default `brew install mutt` will not work. You will need to add the extra
  option for `sidebar-patch` to make it usable with your GMail labels.
* `brew install weechat --python --perl` and the first thing you should do is
  install
  [Weeget](http://www.weechat.org/files/doc/devel/weechat_quickstart.en.html#plugins_scripts).
  Also, consider `/weeget install urlgrab` & `/weeget install buffers.pl`
* [Connecting Bitlbee with GTalk](http://wiki.bitlbee.org/HowtoGtalk)
* [Connecting Bitlbee with Twitter](http://wiki.bitlbee.org/HowtoTwitter)
* I have not yet figured out how to run BitlBee in daemon mode using launchctl.
  I followed up at this
  [topic](http://forums.macrumors.com/showthread.php?t=791587). I will have to
  investigate further about this. This means, I have an extra window in my tmux
  session.
* [Read HTML mails in mutt](http://www.wiseguysonly.com/2012/05/15/reading-html-email-from-within-mutt/)
* [Importing Google contacts in mutt](http://atechnologyjobisnoexcuse.com/2010/04/google-contacts-in-mutt-and-vim/)
