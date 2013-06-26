---
layout: post
title: "Evolution of a Backbone application"
published: true
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
* Spend sometime to do search on Bitbucket/GitHub to find a real world open
  source application using Backbone. Just like Backbone itself, there are no
  standard way on how you organize your modules/code files. During my search, I
  was lucky to look into an example of
  [Cojiro](https://github.com/netalab/cojiro) which led me to
  backbone.boilerplate, whose structure I am using for our project.
* (NOTE: This point is something that I need to try out myself but I believe it
  pertinent to the problem in hand). Try to implement a small project (not the
  TODO MVC thats there everywhere) in multiple frameworks (Amber.js and
  Angular.js seems to be the more popular ones right now) to see how each one
  works. Even if you dont end up using those frameworks in any real life
  project, it will probably open up various other possibilities of improvements
  about how you write your application.

That's it for now.
