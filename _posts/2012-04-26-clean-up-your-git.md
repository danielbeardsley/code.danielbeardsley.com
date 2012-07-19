---
layout: post
title: Clean up your git -- pruning merged branches
tags:
   -- git
   -- terminal
   -- linux
---

{{ page.title }}
================

<p class="meta">2012 / 04 / 26 - San Luis Obispo, CA</p>

Want to clean up all those merged feature branches in git, but don't feel like
installing a program like [git-sweep](http://lab.arc90.com/2012/04/03/git-sweep)
to do something that can be done in a one line bash command?

Delete local merged branches
----------------------------
{% highlight bash %}
git branch --merged master |
   grep -v master |
   xargs git branch -d
{% endhighlight %}

Delete branches on your origin
------------------------------
{% highlight bash %}
git branch -r --merged origin/master |
   grep -v master |
   sed "s| origin/|:|" |
   xargs git push origin
{% endhighlight %}
