---
layout: post
title: "How I use Gmail to consume Github notifications"
author: Daniel Beardsley
author_url: https://github.com/danielbeardsley
summary: Github notifications are great but consuming them via the 
         notifications web UI can be slow. Opening a new tab for every
         notification with no *read-it-later* option is painful.
         Gmail and filters can make it awesome.
tags:
   - github
   - gmail
   - workflow
location: San Luis Obispo, CA
---

### Background
I've been using Github notifications for as long as github has had them
but they've always been a bit tedius.
Subscribing to a whole repo and getting notified
on *everything* that happens often generates too many notifications;
At least too many to usefully consume via the web UI.
I've also had github send notifications to my email address
so I can consume them that way as well.
Since 2012, notification emails [have had some great features][email features]
that I've only recently taken advantage of.

### How I read notifications
![Gmail Labels](/images/gmail-github-labels.png)
All github notification emails end up with one of two labels applied,
skipping my inbox.
`Github-All` contains all notifications from threads 
that I'm not explicitly subscribed to or mentioned in.
`Github-Me` contains all notifications from threads
I'm currently subscribed to or mentioned in.
I usually go though all unread notifications in `Github-Me` first.
Using j/k to navigate emails
and Enter/u to open and close the single-email view.
I occasionally mark something as *Unread* and come back to it later.

### Advantages over Web UI
* See entire content of the notifications in a thread, in gmail, and reply.
* Great keybaord shortcuts for the whole thing
* "Mark as unread"
* "Mark as unread from here" when you want to read the rest of a thread later
* Easy Mobile consumption
* See / search already consumed notifications

### How to set it up

![Gmail Filters](/images/gmail-github-filters.png)
![Github Notification Settings](/images/github-notification-settings.png)

Features

   [email features]: https://github.com/blog/1214-notification-email-improvements

