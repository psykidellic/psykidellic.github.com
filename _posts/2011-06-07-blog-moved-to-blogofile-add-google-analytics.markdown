---
layout: post
title: Blog moved to Blogofile - add Google Analytics
post-link:
---
As a continuation from my last post, listed below are the other two
changes that I have applied to my setup.

Vaporfile fix
=============

As you would know, I am using [Amazon S3][] for this blog. I also use
the excellent vaporfile script. After updating the second post
yesterday, I found a bug with the script. After it updates an existing
file (after matching the checksums), vaporfile fails to set the
permission correctly. This results in `index.html` to have incorrect
access permission and you end up getting AccessDenied from Amazon when
you try to access your blog.

After around 20 minutes of investigation, I found the error and the
patch is available at [my fork of the project][].

Addition of Google Analytics
----------------------------

Apart from Disqus, I believe Google Analytics is probably the next
feature that almost everybody uses. I plan to submit this patch to
Blogofile in coming days but you just need to add the following to
`_config.py`:

{% highlight python %}
### Google analytics integration
blog.analytics.enabled = True
#### enter your 'web property id' here
blog.analytics.id    = "UA-XXXXXX-6"
{% endhighlight %}

and to `footer.mako`:

{% highlight html %}
    ### Google analytics integration
    blog.analytics.enabled = True
    #### enter your 'web property id' here
    blog.analytics.id    = "UA-XXXXXX-6"
{% endhighlight %}

and to `footer.mako`:

{% highlight html %}    % if bf.config.blog.analytics.enabled:
    <script type="text/javascript">

      var _gaq = _gaq || [];
      _gaq.push(['_setAccount', '${bf.config.blog.analytics.id}']);
      _gaq.push(['_trackPageview']);

      (function() {
        var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
        ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
        var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
      })();

    </script>
    % endif
{% endhighlight %}

  [Amazon S3]: http://aws.amazon.com/s3/
  [my fork of the project]: https://github.com/psykidellic/Vaporfile/commit/0a866ad8715bb4267d6ee4f5672764f4e54b7e8a
