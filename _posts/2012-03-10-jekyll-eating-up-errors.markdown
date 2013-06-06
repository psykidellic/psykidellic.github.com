---
layout: post
title: "jekyll eats up error from your writing"
tags: [programming]
---
If you are like me and run **jekyll --auto --server**, here is a warning.

While writing your post, if you end up making a mistake that fails a successful jekyll compilation after saving, jekyll will silently ignore it and move ahead. Thinking that everything is correct, if you preview your local server, it will remain at the previous state leaving your wondering whats wrong.

Hoping that its a bug, I restarted WEBRick without any success. Even **jekyll --server** does not throw up any error. Finally I did, **jekyll --server** but no success.

Both the command will silently eat up everything. I had to run

> jekyll --no-auto --server

that actually stopped on an error to give me more details.
