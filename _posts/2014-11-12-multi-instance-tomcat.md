---
layout: post
title: "Getting Tomcat manager working for a multi-instance Tomcat on localhost"
description: "Configure a multi-instance Tomcat"
tags: [code]
modified: 2014-11-12
---

All day I had the pleasure of trying to get the Tomcat manager gui working on local instanced Tomcat. Manager had always loaded up fine when I ran Tomcat as a single server on my local machine. Today, I had a need to run multiple instances of Tomcat on my local computer and there are several resources that discuss the process[^1]. However, I kept running into an issue where the manager for the instanced server wouldn’t work. The username/password prompt would show up but it would not accept the username/password that I had configured in the tomcat-users.xml file; it would just re-prompt me resulting in 401/403 html errors. Finally, I found a post[^2] that discussed a solution to the problem, though doesn’t go into the explanation of why this is the solution.

The solution is as follows:

In the `server.xml` under the `Engine` context add:

{% highlight Apache config files %}
<Realm className="org.apache.catalina.realm.MemoryRealm" />
{% endhighlight %}

According to the Tomcat resource[^3]:

> The purpose of the MemoryRealm implementation is to provide a mechanism by which Tomcat can acquire information needed to authenticate web application users, and define their security roles, from a simple text-based configuration file in XML format. This is intended to simplify the initial installation and operation of Tomcat, without the complexity of configuring a database or directory server based Realm. It is not intended for production use.

With that in mind, I still don’t know why it was unnecessary for the single instance Tomcat setup I had earlier…


Sources:

[^1]: [https://tomcat.apache.org/tomcat-7.0-doc/RUNNING.txt](https://tomcat.apache.org/tomcat-7.0-doc/RUNNING.txt)
[^2]: [https://geekflare.com/tomcat-login-problem/](https://geekflare.com/tomcat-login-problem/)
[^3]: [https://tomcat.apache.org/tomcat-7.0-doc/funcspecs/fs-memory-realm.html](https://tomcat.apache.org/tomcat-7.0-doc/funcspecs/fs-memory-realm.html)