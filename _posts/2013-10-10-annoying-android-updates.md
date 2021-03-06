---
layout: post
title: "Annoying Android updates"
description: "Modify Android phone to ignore OTA updates"
tags: 
  - code
modified: 2013-10-10
---

Have you rooted and modified your Android phone? Are the vendor-pushed updates getting annoying? Follow this guide to silence those updates and be in control of your own upgrades:

Step 0: Be root.

{% highlight bash %}
$ su
{% endhighlight %}


Step 1: Mount the /system folder as read/write.

{% highlight bash %}
$ mount -o remount,rw /system
{% endhighlight %}

Step 2: Create an unwanted apps folder.

{% highlight bash %}
$ cd /system
$ mkdir app_hell
{% endhighlight %}

Step 3: Move the unwanted app (In this case, we’re moving the firmware upgrade app).

{% highlight bash %}
$ mv app/FWUpgrade.apk app_hell/. 
$ mv app/FWUpgrade.odex app_hell/.
{% endhighlight %}

Step 4: Remount the /system folder back to read-only.

{% highlight bash %}
$ mount -o remount,ro /system
{% endhighlight %}

Step 5: Drink a beer.