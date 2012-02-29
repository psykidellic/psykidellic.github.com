---
layout: post
title: Finding an item based on computed value
post-link:
---
Recently, at work I had to implement some code which had the pattern:

    #!python
    found = None
    for x in foo:
        if bar(x) == baz:
            found = x

One could do this in a more Pythonic way as:

    #!python
    try:
        found = next(x for x in foo if bar(x) == baz)
    except StopIteration, e:
        found = None
