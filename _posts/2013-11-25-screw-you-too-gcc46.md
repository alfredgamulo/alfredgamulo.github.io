---
layout: post
title: "Screw you too, gcc46"
description: "gcc46 didn't work so gcc42"
tags: 
  - code
modified: 2013-11-25
---

{% highlight bash %}
admin$ brew install gcc46
==> Downloading http://ftpmirror.gnu.org/gcc/gcc-4.6.4/gcc-4.6.4.tar.bz2
Error: stack level too deep
{% endhighlight %}

Use gcc42, because stupid error.

{% highlight bash %}
admin$ brew install apple-gcc42
admin$ rvm install 1.9.3 --with-gcc=gcc-4.2
{% endhighlight %}
