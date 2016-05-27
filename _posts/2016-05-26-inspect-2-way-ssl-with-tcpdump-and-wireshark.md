---
layout: post
title: "Inspect 2-way authentication with Tcpdump and Wireshark"
description: "Use Wireshark to decrypt and inspect 2-way authentication tcp stream"
tags: [code]
modified: 2016-05-26
---

At work, I run an Nginx server that is configured for 2-way authentication. 
The following are notes that I took to show how to use Wireshark to inspect the tcp stream of encrypted traffic.


Convert certificates to .p12
---
First, we need to have both client and server certificates. With Wireshark it is preferred that we have PKCS12 format files so we need to convert our certificates to that format. The client in this case is a Tomcat server but sometimes a JMeter client which is used for testing. 

To convert a JKS file to PKCS12 format:
{% highlight bash %}
$ keytool -importkeystore -srckeystore client.jks \
> -srcstorepass weblogic \
> -destkeystore client.p12 \
> -deststorepass weblogic \
> -srcalias client \
> -deststoretype pkcs12
{% endhighlight %}

To convert a PEM file to PKCS12 format:
{% highlight bash %}
$ openssl pkcs12 -export -out server.p12 \
> -inkey server.key \
> -in server.pem \
> -certfile server-cacert.pem 
{% endhighlight %}


Form the tcpdump command
---

In my environment, the backend server is behind an AWS Elastic Load Balancer so we need to find the IP addresses of the ELB:
{% highlight bash %}
$ host my-loadbalancer-1234567890.us-east-1.elb.amazonaws.com
my-loadbalancer-1234567890.us-east-1.elb.amazonaws.com has address 10.201.100.100
my-loadbalancer-1234567890.us-east-1.elb.amazonaws.com has address 10.201.100.101
{% endhighlight %}

Use the ELB IP addresses to form the tcpdump command:
{% highlight bash %}
$ sudo tcpdump -i any -s0 -w output.pcap host 10.201.100.100 or 10.201.100.101
{% endhighlight %}

If you want to be specific about the port then a more advanced command:
{% highlight bash %}
$ sudo tcpdump -i any -s0 -w output.pcap \
> '(host 10.201.100.100 or 10.201.100.101) and port 443'
{% endhighlight %}


Sending the request
---
To properly capture 2-way authentication and be able to decrypt the tcp stream in Wireshark, the traffic must be encrypted with RSA. Traffic encrypted with any version of Diffie-Hellman will not work.

On the server, list the available ciphers and narrow down to the relevant ones that will work for Wireshark inspecting:
{% highlight bash %}
$ openssl ciphers | tr ':' '\n' | grep AES | egrep -v 'DH|PSK'
AES256-GCM-SHA384
AES256-SHA256
AES256-SHA
AES128-GCM-SHA256
AES128-SHA256
AES128-SHA
{% endhighlight %}

With the listed ciphers from the server, form the curl request and specify a compatible cipher:
{% highlight bash %}
$ curl -v --tlsv1.2 --cipher rsa_aes_128_sha --cert client.p12:weblogic \
> https://my-loadbalancer-1234567890.us-east-1.elb.amazonaws.com:443/test
{% endhighlight %}

Unfortunately, if you are on a Mac, the curl request will not work. Since Mavericks, the Transport Security Layer disables the ignores the option to set the cipher suite.[^1]
In my case, I was able to restrict the encryption to RSA by setting the Nginx server configuration:
{% highlight conf %}
ssl_ciphers RSA;
{% endhighlight %}

After setting the Nginx server to only accept RSA encryption, I could send requests from JMeter with no issue or further configuration.


Inspect with Wireshark
---
Finally, once the pcap file has been created which captures the traffic sent from curl or JMeter, open it in Wireshark.
Open the Wireshark preferences and select SSL from the protocol list. Select "Edit..." for the RSA Key List and add both the client certificate and the server certificate that we generated earlier in this tutorial. Afterward, you should now be able to see the unencrypted traffic. If you right-click and select "Follow > SSL Stream", then you should see the requests made in clear text including header values and body data.


[^1]: [https://curl.haxx.se/mail/archive-2013-10/0036.html](https://curl.haxx.se/mail/archive-2013-10/0036.html)
