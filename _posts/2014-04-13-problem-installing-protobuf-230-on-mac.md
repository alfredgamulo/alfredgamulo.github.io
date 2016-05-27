---
layout: post
title: "Problem installing Protobuf 2.3.0 on Mac"
description: "Edit protobuf script to install 2.3.0 on Mac"
tags: [code]
modified: 2014-04-13
---

Installing the 2.3.0 version of google protobuf using homebrew was being problematic. I ended up trying instead to make it manually using the source from google but ran into the same troubles. The solution[^1] never made its way to the homebrew repo, I guess, or google’s archive.

{% highlight C %}
// replace the following in protobuf-2.3.0/src/google/protobuf/message.h

#ifdef __DECCXX
// HP C++'s iosfwd doesn't work.
#include 
#else
#include 
//#include 
#endif
{% endhighlight %}

[^1]: [https://code.google.com/p/protobuf/issues/detail?id=570](https://code.google.com/p/protobuf/issues/detail?id=570)