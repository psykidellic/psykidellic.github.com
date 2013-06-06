---
layout: post
published: true
title: "Using spellchecking with VIM"
date: "Thu Jul 05 16:46:20 -0700 2012"
---

Starting with 7.x, vim integrates a powerful spell checker. You can enable it by
either adding it to your `.vimr` or setting as toggable command.

`:setlocal spell`

You basically need to know about:

* `]s` — move to the next misspelled word
* `[s` — move to the previous misspelled word
* `zg` — add a word to the dictionary
* `zug` — undo the addition of a word to the dictionary
* `z=` — view spelling suggestions for a misspelled word
  * One useful feature is that you can append `[n]` before the command and it
    will automatically select the nth option from suggestion. If you do lot of
    writing that invovles spell checking, I will suggest that you map the three
    characters to something more convenient. 90% of the time, you want to use
    `1z=`.
