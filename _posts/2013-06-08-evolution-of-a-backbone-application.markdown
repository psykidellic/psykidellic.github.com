---
layout: post
title: "Evolution of a Backbone application"
published: false
---

In my weekend free time, I moonlight as amateur Backbone application development
working on a music discovery site for independent electronic music. This also
helps me with my general JavaScript knowledge as I getting more involved in
front UI work.

Being my first real life JavaScript heavy application, I had to face some issues
which may or not be unique to other people. My impression and thoughts:

* Backbone being too agnostic with how the developers manage their modules and
  code is a double edged sword. On one hand, it completely lets the developer
  decide and choose about how to setup the project, it takes away lot of your
  initial time on design issues which probably could be better spent in real
  life problems. As a result, no single dominant framework has come up like Ruby
  on Rails.
* For any decent size application, you will end up using one of the wrapper
  frameworks (Backbone.LayoutManager, ChaplinJS, Backbone.Marionette), so after
  your first TODO example, its worthwhile to investigate one of the above.
* Its probably worthwhile to learn up a module loader like Requirejs (if you
  have not yet done so). For a long period of time, I avoided reading up on the
  library and just bundle up various JS files using Rails "include" directive.
  This will eventually lead up to having multiple global objects which you
  definitely want to avoid.
* Spend sometime to do a search on 


  asdh
