---
layout: post
title: Blog moved to Blogofile
post-link:
---
**tl;dr** I would have saved couple of hours by just reading the mailing
list.

The following post is very much inspired by [this entry][]. To get the
blog up, I used `blogofile init simple_blog` generating a minimal setup
with no themes worked. I spent some time figuring out how to make my
index page similar to chronological page. The docs was lacking on this
part and in my eagerness, I went ahead and updated `index.html.mako`
with code from `chronological.mako`. Realizing that its a criminal
duplication of code, I was convinced that there has to be a better way.
Quick walk through the mailing list pointed me to the [following
conversation][]. Unfortunately, contrary to what is mentioned in the
list, I had to set **blog.path = “”** in my `_config.py`. Otherwise, all
the links become **[http://page/1][]** instead
of **[http://MYHOST/page/1][]**.

Setting up syntax highlighting for code samples using Pygments turned
out to be more work then expected. It seemed after [reading][] and this
post by [Morgan Goose][] led me to think that syntax highlighting will
be automatically enabled. Unfortunately, it was not to be. I had to
update the config file with (this options are present if you init
blogofile.com):

{% highlight python %}
filters.syntax_highlight.style   = "murphy"
filters.syntax_highlight.css_dir = "/css"
filters.syntax_highlight.preload_styles = ["murphy"]

blog.post_default_filters = {
    "rst": "rst, syntax_highlight",
}
{% endhighlight %}

Apart from the above change, I also liked zzzeek’s changes to the
`syntax_highlight.py` which enables me write code samples using
`#!python` directive. Lets face some facts - it will be sometime before
I post anything other than Python.

Next step is to get yourself registered with [Disqus][] and setup
Blogofile by adding to the config [file:][]:

> !python blog.disqus.enabled = True
> blog.disqus.name = “YOUR-DISQUS-APPNAME”

As a side note, if you are using `VIRTUALENV` along with blogofile, do
not forget to start your environment name with `_`. Otherwise, blogofile
will simply copy it to \_site and it will get synced to your remote
folder. I just use `_ENV` instead of `ENV`.

  [this entry]: http://techspot.zzzeek.org/2010/12/06/my-blogofile-hacks/
  [following conversation]: http://groups.google.com/group/blogofile-discuss/browse_thread/thread/292c32bfe35b8466
  [http://page/1\*]: http://page/1*
  [http://MYHOST/page/1\*\*]: http://MYHOST/page/1**
  [reading]: http://www.blogofile.com/demo/sample_posts.html
  [Morgan Goose]: http://morgangoose.com/blog/2010/09/28/switching-to-blogofile/
  [Disqus]: http://www.disqus.com
  [file:]: file:
