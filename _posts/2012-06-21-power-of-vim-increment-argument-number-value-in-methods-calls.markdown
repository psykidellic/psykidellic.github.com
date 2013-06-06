---
layout: post
published: true
title: "Power of VIM: Increment argument number value in methods calls"
date: "Thu Jun 21 15:27:48 -0700 2012"
---
Recently, I have had to write Scala code for a project at work. In real life, I tend to masquarade as Rails/UI developer. The project involves communicating to a PostgreSQL server and unlike Rails, Scala does not really have a good ORM framework, I had to write pure SQL (its been some years since I did that). The general pattern is:

{% highlight scala %}
pool.query(fooQuery) { rs =>
  while (rs.next()) {
    id = rs.getInt(1)
    name = getString(2)
  }
}
{% endhighlight %}

Now during prototyping, you are not exactly sure which columns you will need to fetch to do your work. Sometimes, you have to insert column in between (I like to group similar type/table columns) and correspondingly you have to go back to the code and increase every column parameter by 1. This problem gives us a practical example of using macro and applying it to series of lines/selection. For this to work, I will assume that you have to added a column between id and name, thus you have to increment rest of the column argument by 1.

We place the cursor somewhere in the line containing name.

{% highlight bash %}
qa              "Start recording and store it register a
$T(             "Go till end and search backwards till (
CTRL+A          "Increment argument value by
q               "Quit recording
{% endhighlight %}

Now you can apply the macro in multiple ways with the two most popular being:

* By replaying the macro [Macro Tip](http://vim.wikia.com/wiki/Macros)
* Using the global `:g` command [Power of G](http://vim.wikia.com/wiki/Power_of_g)

In our case, we will just visually select the block of lines and apply **:'<,'>normal @a**.

{% highlight bash %}
:\'<,\'>normal @a
{% endhighlight %}
