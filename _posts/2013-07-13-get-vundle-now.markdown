---
layout: post
published: true
title: "Get Vundle now"
date: "Sat Jul 13 01:25:05 -0700 2013"
---

I have been using Vim (almost exclusively) with for 5 years now, with my
vimfiles saved along with my dotfiles and personal keys on a private git
repository. This is a folder that I have build over past couple of years, adding
plugins and tricks as and when I found them. In all those years,
I dont think I ever upgraded any of the plugins - as it just felt like a hassle. I knew
about [Vundle](https://github.com/gmarik/vundle) and
[Pathogen](https://github.com/tpope/vim-pathogen) for a long time and it was
always in my radar to try one of the out.

Last weekend, I finally took the plunge and setup a test VM to try it out and it
has just been a pleasure. Barring, two issues:

* [https://github.com/altercation/vim-colors-solarized/issues/40
](https://github.com/altercation/vim-colors-solarized/issues/40)
* [https://github.com/gmarik/vundle/issues/210](
https://github.com/gmarik/vundle/issues/210)

vundle was setup with all my existing plugins and keymappings in less than an
hour.

Though, I stumbled upon more issue when I cloned the new repository to an
existing machine to see how easy it is to setup. Unfortunately, I think I had my
submodules setup incorrectly and thus no checkouts were ever succesful. Scouring
the web to see how others have solved their issues, I realised there seems to be
couple of ways that people like to do it. This is how I am doing it.

* Separate out vim into its own repository. [My
  vimfiles](https://github.com/psykidellic/vimfiles). I changed the .vimrc to be
  just vimrc.
* In your dotfiles, .vimrc, have:

{% highlight bash %}
if filereadable(expand("~/.vim/vimrc"))
  source ~/.vim/vimrc
endif
{% endhighlight %}

assuming you cloned your vimfiles to ~/.vim. Another important part of code is
to [ignore the bundle
folder](https://github.com/psykidellic/vimfiles/blob/master/.gitignore)
