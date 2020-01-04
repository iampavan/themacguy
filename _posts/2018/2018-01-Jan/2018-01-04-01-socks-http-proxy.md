---
title: "SOCKS proxy? HTTP proxy?"
date: 2018-01-04 23:55:59 +0530
tags:
  - SECURITY
  - NETWORKING
  - SERVER
permalink: "/blog/:title.html"
header:
  teaser: "/assets/images/blog-posts-images/09-free-proxy-servers.png"
published: true
---

![09-free-proxy-servers.png](/assets/images/blog-posts-images/09-free-proxy-servers.png)

### Why would an organization want to use a proxy on their network?

1. The first reason is to optimize bandwidth usage.
<br/><br/>
Proxies can improve speed by caching Internet content locally after a client requests it. Clients that request the same content will get it locally instead of downloading it again from the Internet.

2. Another reason is content filtering.
<br/><br/>
Specific websites can be blocked or approved or content can be filtered dynamically with a third-party service. Such filtering is commonly used in educational settings.

3. Some organizations use a proxy to monitor users’ network traffic for leakage or exfiltration of sensitive data.
<br/><br/>
Many kinds of proxies are available, including reverse and SOCKS proxies, HTTP web proxies.

<br/>

A SOCKS server is a general purpose proxy server that establishes a TCP connection to another server on behalf of a client, then routes all the traffic back and forth between the client and the server. It works for any kind of network protocol on any port. SOCKS Version 5 adds additional support for security and UDP. The SOCKS server does not interpret the network traffic between client and server in any way, and is often used because clients are behind a firewall and are not permitted to establish TCP connections to servers outside the firewall unless they do it through the SOCKS server. Most web browsers for example can be configured to talk to a web server via a SOCKS server. Because the client must first make a connection to the SOCKS server and tell it the host it wants to connect to, the client must be “SOCKS enabled.”

<br/>

An HTTP proxy is similar, and may be used for the same purpose when clients are behind a firewall and are prevented from making outgoing TCP connections to servers outside the firewall. However, unlike the SOCKS server, an HTTP proxy does understand and interpret the network traffic that passes between the client and downstream server, namely the HTTP protocol. Because of this the HTTP proxy can ONLY be used to handle HTTP traffic, but it can be very smart about how it does it. In particular, it can recognize often repeated requests and cache the replies to improve performance. Many ISPs use HTTP proxies regardless of how the browser is configured because they simply route all traffic on port 80 through the proxy server.

<br/>

## Reference articles :

- <http://www.jguru.com/faq/view.jsp?EID=227532>{:target="_blank"}

- [How to setup an HTTP Proxy server](https://www.godaddy.com/garage/how-to-set-up-an-https-proxy-server/){:target="_blank"}
