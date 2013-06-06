---
layout: post
title: Big changes and using blogofile with GitHub and BitBucket
post-link:
---
Oh wow, its again almost 3 months before you see a new post from me.
Couple of big changes in life that have happened over last couple of
months.

-   I changed jobs and now I am a *Member of Technical Staff* at
    [Meraki][]. We make the easiest Cloud Managed Enterprise Networks.
-   The new job entails me to work on Ruby on Rails so from now you will
    see rather less Python and more Rails/JavaScript posts.

On a side note, as a chronic habit - a new post would mean that I have
changed my way of writing and hosting my blog. Maybe, changing my system
forces me to write a blogpost. Anyway, long story short, even though
Blogofile is great, working with Vaporfile and S3 was just not working
out. Then I found out Steve’s post on [Free Hosting at Bitbucket][].
Since I use BitBucket as my DVCS provider, I wanted to check it out.

Creating a new repository with name *psykidellic.bitbucket.org* was not
hard and pushing a build version of \_site was even easier.
Unfortunately, the way Bitbucket shows a static page is not compatible
with Blogofile link generation. It would seem that blogofile creates
links to post like
*[http://psykidellic.github.com/2011/06/08/finding-an-item-based-on-computed-value/][]*
whereas the final page is
*[http://psykidellic.github.com/2011/06/08/finding-an-item-based-on-computed-value/index.html][]*
and Bitbucket does not default to index.html. So all the links redirect
back to the main page. Maybe there is something wrong with my
configuration but I was too bored to dig deeper. I have seen various
posts about using Blogofile with Github page and quick Googling brought
me to [Manuels post][]. It uses *git submodule* feature and reading upon
similar Mercurial feature of [subrepos][] say that *hg* supports git as
subrepos natively.

I like to keep my drafts private and thus the original repository is
private at Bitbucket. But the user facing has to be public. So in no
time, I had [psykidellic.github.com][] up and running. Mercurial
subrepos work great with git and you see the result. So now the flow of
my post is:

-   Continuously write drafts and commit.
-   When the time comes, blogofile build.
-   git add NEWFILES && hg push

**note:** I am planning to make the third part as one script which
should be easy depending upon your needs.

  [Meraki]: http://www.meraki.com
  [Free Hosting at Bitbucket]: http://hgtip.com/tips/beginner/2009-10-13-free-hosting-at-bitbucket/
  [http://psykidellic.github.com/2011/06/08/finding-an-item-based-on-computed-value/]: http://psykidellic.github.com/2011/06/08/finding-an-item-based-on-computed-value/
  [http://psykidellic.github.com/2011/06/08/finding-an-item-based-on-computed-value/index.html]: http://psykidellic.github.com/2011/06/08/finding-an-item-based-on-computed-value/index.html
  [Manuels post]: http://manuel-ohlendorf.de/blog/2010/12/23/hosting-a-blogofile-blog-on-github-with-github-pages/
  [subrepos]: http://mercurial.selenic.com/wiki/Subrepository#Git_subrepositories
  [psykidellic.github.com]: http://psykidellic.github.com
