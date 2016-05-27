---
layout: post
title: "Apache reverse proxy multiple domains on a single server"
description: "Example Apache config for multiple reverse proxy"
tags: 
  - code
modified: 2013-10-07
---

I recently moved to Digital Ocean for web hosting as their SSD droplets were higher performing than any other VPS in the price range. With that move and the performance increase, I also consolidated many of my websites to one server. To use apache to reverse proxy multiple domains on one server, use the following example and add it to the bottom of your /etc/httpd/conf/httpd.conf file.

{% highlight Apache config files %}
NameVirtualHost *:80
<VirtualHost *:80>
ServerName www.domain1.com
ServerAlias domain1.com
DocumentRoot /var/www/html/domain1
</VirtualHost>
<VirtualHost *:80>
ServerName www.domain2.com
ServerAlias domain2.com
DocumentRoot /var/www/html/domain2
</VirtualHost>
<VirtualHost *:80>
ServerName domain3.us
ServerAlias www.domain3.us domain3.com
DocumentRoot /var/www/html/domain3
</VirtualHost>
{% endhighlight %}
