---
layout: post
title: "Proxying problem on Redhat"
description: "Configure SELinux to proxy"
tags: 
  - code
modified: 2014-04-12
---

I had a problem proxying on Redhat.

SELinux was being a bitch:

{% highlight bash %}
$ /usr/sbin/setsebool httpd_can_network_connect 1
{% endhighlight %}