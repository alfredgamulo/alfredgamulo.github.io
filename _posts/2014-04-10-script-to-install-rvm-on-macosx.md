---
layout: post
title: "Script to install rvm on MacOSX"
description: "Script to install rvm"
tags: [code]
modified: 2014-04-10
---

{% highlight Bash shell scripts %}
#!/bin/bash -l
current_version=`ruby -v | awk '{print $2}'`
if [ $current_version != "1.9.2" ]; then
if [[ ! -x `which rvm` ]]; then
curl -L https://get.rvm.io | bash -s stable
source ~/.rvm/scripts/rvm
rvm autolibs homebrew
rvm pkg install openssl
fi
rvm install 1.9.2
rvm reload
rvm --default use 1.9.2
fi
{% endhighlight %}