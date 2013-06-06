---
layout: post
published: true
title: "Using tmux to copy text between two sessions"
date: "Thu Jul 05 11:36:52 -0700 2012"
---

As I mentioned in my previous post, I did not yet find a problem where I could
effectively use the cut-paste between tmux buffers. But now I do. This post will
describe the steps to copy text from one of your remote session to local session
using tmux buffers.

__NOTE:__ You can probably do the same using Mac OS X buffer (using mouse to
select text and Cmd-C/Cmd-V). This post will show you a way without moving your
hand away from your keyboard, which I believe is much more efficient. If you are
Linux/\*nix, check out this [stackexchange
question](http://unix.stackexchange.com/questions/15715/getting-tmux-to-copy-a-buffer-to-the-clipboard).

{% highlight bash %}
setw -g mode-keys vi
unbind p
bind p paste-buffer
bind -t vi-copy v begin-selection
bind -t vi-copy y copy-selection
bind -t vi-copy Escape cancel
bind y run "tmux save-buffer - | reattach-to-user-namespace pbcopy"
{% endhighlight %}

Here is a perfect use case example.

* Open a file in your local session.
* Split your tmux pane.
* Login to a remote server
* Open a text editor.
* Get into copy-mode by pressing `<prefix>[`
* Select lines of text pressing `v`. You can use vi movement commands too
* `y` to yank to tmux buffer
* `Esc` to get out of copy-mode.
* Move to your local session pane.
* Get in insert mode in vim.
* `<prefix>p` to paste from the tmux buffer.
