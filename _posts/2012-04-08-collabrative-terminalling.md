---
layout: post
title: Collabrative Terminal -- Sharing a Screen Session
tags:
   -- ssh
   -- terminal
   -- linux
location: San Luis Obispo, CA
summary: It's easier than you think.
---

I often explain things to people that involve a lot of command-line work and
usually resort to screen-sharing with Google+ Hangouts or something similar.
This is not ideal and it's difficult to instruct someone when you can't both
affect the workspace.

There is a better way.

## Sharing a GNU Screen Session ##
I knew that [GNU screen](http://www.gnu.org/software/screen/manual/screen.html)
allowed multi-user sessions, and I finally figured out how to share a screen
session with another user.  It can be tricky, as the other person can easily
screw up your typing with a single keystroke, so I reccomend Voice-chatting at
the same time.

### Requirements ###
* Both users need to have ssh access to a single server.
* Both users need to have access to a single user-account on the server (you
  can use *sudo su*)

  OR you can run some special commands to allow another user access to your
  screen session.

## Using a Single User Account ##
### User 1 ###
{% highlight bash %}
sudo su user_2
script /dev/null
screen -S lets_share
{% endhighlight %}
### User 2 ###
{% highlight bash %}
screen -rx lets_share
{% endhighlight %}

## Using Your Own User Accounts ##
### User 1 ###
{% highlight bash %}
screen -S lets_share
# inside the screen session
C-a :multiuser on
C-a :acladd user_2
{% endhighlight %}
### User 2 ###
{% highlight bash %}
screen -r user_1/lets_share
{% endhighlight %}
