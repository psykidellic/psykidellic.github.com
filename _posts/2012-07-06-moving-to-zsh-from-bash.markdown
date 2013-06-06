---
layout: post
published: true
title: "Moving to zsh from bash"
date: "Fri Jul 06 03:55:12 -0700 2012"
---

Alright, after finally stalling it for years, I have finally moved to `zsh` from
the old and trusted `bash`. I would have to say that I never ever used bash to
its maximum power nor I would probably use the maximum features of `zsh`. But I
wanted to see if `zsh` provides better features for normal to average user like
me. Getting the defaults right is big win for me.

Mac OS X comes with a pretty recent version of zsh so you can simply use it or
if you like to be on bleeding edge, get it from brew (make sure its then added
to `/etc/shells`). Change your default shell using `chsh`.

Improvements
============

* _Autocompletion_ - Honestly, the autocompletion is just better. Showing me all
  the options as menu is awesome.
* _Autosuggestion and autocorrection_ - 90% of the time I have achieved right
  option from zsh. It even autocorrets/suggests aliases.
* _Finding files_ - No more complex `find` commands. All my searches for last
  week has been `ls **/prefix*`.
* _Better movement between folders_ - I have found that zsh does better
  completion of directories and when you want to go back one level up.

.oh-my-zsh
==========

From [their site](https://github.com/robbyrussell/oh-my-zsh/):

> A handful of functions, auto-complete helpers, and stuff that makes you shout…
> “OH MY ZSHELL!”

In short, its a collection of community plugins and options that should make
your life easier from start but as with all great power comes great
responsibility. Its really is double edged sword. On one hand, you get many
readymade plugins and solutions that it will cover 99% of your work. On the
other, it will be very magic when you cannot figure out why something is working
or not working. E.g., I have tmux setup with `set-window-option -g
automatic-rename off` but it was not working because zsh was updating the title.
I had to spend some time on Google and finally a fine folk at `#tmux` pointed me
to the right direction.

Conclusion
==========

All in all, I like it and hopefully with more time spent with it, my command
line environment is going to get better.

__Further reading:__ One of these days, I am going to sit down and read through
the [zsh cheatsheet](http://www.bash2zsh.com/zsh_refcard/refcard.pdf).

