---
layout: post
title: SSH in the background
---

{{ page.title }}
================

<p class="meta">2012 / 03 / 27 - San Luis Obispo, CA</p>

I found myself wanting to launch and control a port-forwarding ssh session from
a shell script today and I eventually figured out how to do it.

The tricky part was that I also wanted the script to do other things (start a
Selenium server) and kill off the ssh connection when it was done.

## The Code ##
{% highlight bash %}
remote_port=1234
local_port=1234
# Start an ssh port-forwarding command in the background
ssh user@host.com -TN -R $remote_port:localhost:$localport >/dev/null /2>&1 &

# Get pid of ssh background process -- tricky
ssh_pid=$!

# kill the ssh process on exit
trap "kill $ssh_pid" EXIT

# Do other stuff that uses the forwarded port.
#
# In my case, start Selenium
java -jar selenium-server-standalone* 
{% endhighlight %}

## How it works ##

The SSH command is the trickiest bit, so here it is, more in depth.

{% highlight bash %}
ssh user@host.com

   # Disable tty allocation (needed for backgrounding)
   -T

   # Dont run a remote command (i.e. only does port forwarding)
   -N

   # Setup remote port to forward to local port
   -R $remote_port:localhost:$localport

   # Redirect stdin and stdout to /dev/null
   # and put the process in the background (the $)
   >/dev/null /2>&1 &
{% endhighlight %}

