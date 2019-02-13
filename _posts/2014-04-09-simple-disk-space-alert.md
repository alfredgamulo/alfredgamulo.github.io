---
layout: post
title: "Simple disk space alert"
description: "Get an alert if disk space is low"
tags: 
  - code
modified: 2014-04-09
---

We had a need to get alerts in case we are close to running out of disk space on multiple servers but we didn’t want to over complicate it with heavy processes and monitoring. My solution:

{% highlight bash %}
#!/bin/bash
CURRENT=$(df /u01 | grep /u01 | awk '{ print $4}' | sed 's/%//g')
THRESHOLD=1000000
TO=\
user1@example.com \
user2@example.com

if [ "$CURRENT" -lt "$THRESHOLD" ] ; then
mail -s 'Disk Space Alert' $TO << EOF
/u01 partition is running low on disk space. $CURRENT bytes left.
EOF
{% endhighlight %}

Drop that bad boy in /etc/cron.hourly and you got yourself a heartbeat baby!