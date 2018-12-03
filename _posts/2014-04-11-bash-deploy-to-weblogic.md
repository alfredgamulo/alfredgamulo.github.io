---
layout: post
title: "Bash deploy to Weblogic"
description: "Bash deploy to Weblogic"
tags: 
  - code
modified: 2014-04-11
---

{% highlight bash %}
java -classpath /u01/apps/oracle/middleware/wlserver_10.3/server/lib/weblogic.jar weblogic.Deployer \
	 -adminurl t3://localhost:6001 \
	 -username weblogic \
	 -password welcome1 \
	 -name AppName \
	 -targets ServerCluster \
	 -undeploy \
	 || true
{% endhighlight %}

{% highlight bash %}
java -classpath /u01/apps/oracle/middleware/wlserver_10.3/server/lib/weblogic.jar weblogic.Deployer \
	 -adminurl t3://localhost:6001 \
	 -username weblogic \
	 -password welcome1 \
	 -name AppName \
	 -targets ServerCluster \
	 -deploy app-0.1-SNAPSHOT.war
{% endhighlight %}
