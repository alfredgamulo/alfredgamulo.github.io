---
layout: post
title: "Gradle deploy to weblogic"
description: "Example Gradle deployment to Weblogic"
tags: 
  - code
modified: 2013-10-05
---

Found an alternative way to deploy to Weblogic with Gradle.[^1]

{% highlight groovy %}
apply plugin: 'groovy'
apply plugin: 'jetty'
apply plugin: 'eclipse'
apply plugin: 'maven'

//-- weblogic deployment 
configurations {
	weblogic
}
dependencies {
	weblogic files("${System.getenv()['MW_HOME']}/wlserver/server/lib/weblogic.jar",
	"${System.getenv()['MW_HOME']}/wlserver/server/lib/webservices.jar",
	"${System.getenv()['MW_HOME']}/modules/features/weblogic.server.modules_10.3.5.0.jar")
}

task deployToWeblogic(dependsOn:'war') << {
	def war = System.properties['war'] == null ? "project.war" : System.properties['war']
	def url = System.properties['url'] == null ? "t3://localhost:8080" : System.properties['url']
	def user = System.properties['user'] == null ? "weblogic" : System.properties['user']
	def password = System.properties['password'] == null ? "weblogic" : System.properties['password']
        ant.taskdef(name: 'wldeploy', 
             classname: 'weblogic.ant.taskdefs.management.WLDeploy',
             classpath: configurations.weblogic.asPath) 

	ant.wldeploy(action:'deploy', 
		source:"$war", 
		name:"portal", 
		adminurl: "$url", 
		user: "$user",
		password: "$password",
		upload:"true", 
		targets:"AdminServer",
		verbose:'true',
		debug:'false')
}
{% endhighlight %}

{% highlight bash %}
$ MW_HOME=/u01/apps/oracle/middleware
$ GRADLE_OPTS="-Xmx2048m -XX:MaxPermSize=512m -XX:+CMSClassUnloadingEnabled"
{% endhighlight %}

{% highlight bash %}
$ ./gradlew deployToWeblogic -Durl=t3://productionserver:8080 -Duser=mchammer -Dpassword=canttouchthis --stacktrace
{% endhighlight %}


[^1]: [http://gradle.1045684.n5.nabble.com/Simple-Example-War-Deployment-For-Weblogic-td4296554.html](http://gradle.1045684.n5.nabble.com/Simple-Example-War-Deployment-For-Weblogic-td4296554.html)