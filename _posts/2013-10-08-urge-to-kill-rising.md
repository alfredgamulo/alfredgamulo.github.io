---
layout: post
title: "Urge to kill rising"
description: "How to kill everything"
tags: 
  - code
modified: 2013-10-08
---

Sometimes you just gotta kill something. Here’s a useful script for killing a process if it exists.

{% highlight bash %}
$ ps -ef  | grep [b]itchProcess | awk '{print $2}' | xargs -r kill
{% endhighlight %}

The square brackets will filter out the grep command from the process list.

