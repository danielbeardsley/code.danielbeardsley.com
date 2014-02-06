---
layout: post
title: Clean up your git -- pruning merged branches
tags:
   -- git
   -- terminal
   -- linux
location: San Luis Obispo, CA
summary: git prune only goes so far, here's how to delete merged branches
         locally and remotely.
---

Want to clean up all those merged feature branches in git, but don't feel like
installing a program like [git-sweep](http://lab.arc90.com/2012/04/03/git-sweep)
to do something that can be done in a one line bash command?

Delete local merged branches
----------------------------
{% highlight bash %}
git branch --merged master |  # list branches merged into master
   grep -v master |           # exclude master 
   xargs git branch -d        # tell git to delete them
{% endhighlight %}

Delete merged branches on your remote
------------------------------
{% highlight bash %}
git remote prune origin                # prune deleted tracking branches
git branch -r --merged origin/master | # list branches merged into master
   grep -v master |                    # exclude master
   sed -n "s| origin/|:|p" |           # use remote branch delete syntax
                                       # and only include origin branches
   xargs git push origin               # delete them on the remote
{% endhighlight %}


