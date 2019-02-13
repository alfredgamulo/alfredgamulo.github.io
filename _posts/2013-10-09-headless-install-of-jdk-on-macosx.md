---
layout: post
title: "Headless install of JDK on MacOSX"
description: "Chef script to install JDK"
tags: 
  - code
modified: 2013-10-09
---

Chef and terminal examples for headlessly installing JDK.

Chef:

{% highlight ruby %}
case node["platform_family"]
when "mac_os_x"

	destfile = '/tmp/jdk-7u40-macosx-x64.dmg'
	execute "curl -k -O #{web/adddress/to/jdk}" do
	  cwd '/tmp'
	  not_if { ::File.exists? destfile }
	end		

	execute "attach dmg" do
	  cwd "/tmp"
	  command "hdiutil attach -noverify -nobrowse -mountpoint /tmp/jdk #{destfile}"
	end

	execute "install jdk" do
	  cwd "/tmp"
	  command "sudo installer -verbose -pkg jdk/JDK\\ 7\\ Update\\ 40.pkg -target /"
	end

	execute "detach dmg" do
	  cwd "/tmp"
	  command "hdiutil detach /tmp/jdk"
	end

	execute "rm -rf /tmp/jdk"

	execute "ln -s /Library/Java/JavaVirtualMachines/jdk1.7.0_40.jdk/Contents/Home/ /Library/Java/Home"

	ENV["JAVA_HOME"] = "/Library/Java/Home"
end
{% endhighlight %}

Terminal:

{% highlight bash %}
$ cd /tmp
$ curl -k -O #{web/adddress/to/jdk}
$ hdiutil attach -noverify -nobrowse -mountpoint /tmp/jdk #{path/to/downloaded/file}
$ sudo installer -verbose -pkg jdk/JDK\ 7\ Update\ 40.pkg -target /
$ hdiutil detach /tmp/jdk
$ ln -s /Library/Java/JavaVirtualMachines/jdk1.7.0_40.jdk/Contents/Home/ /Library/Java/Home
{% endhighlight %}