---
layout: post
title: "Weblogic path alias"
description: "Use an apache proxy config to alias a weblogic path"
tags: [code]
modified: 2013-10-18
---

The WAR artifact that I’m deploying to weblogic is a snapshot and is named with the version. In its normal deployment, it can be reached with domain/artifact-0.1.0-SNAPSHOT and thats not really how I want to have it named in source code making reference to it. So, I wanted to find a way to alias that path with a simpler path in the apache httpd.conf file. The following sample code shows a proper way to do this:

{% highlight Apache config files %}
<Location /artifact>
 SetHandler weblogic-handler
 WebLogicCluster server:port
 PathTrim /artifact
 PathPrepend /artifact-0.1.0-SNAPSHOT
</Location>
{% endhighlight %}


This will redirect /artifact –> /artifact-0.1.0-SNAPSHOT