---
created_at: 2013-02-21 19:28:10
date: 2024-04-12 14:40:30
description: Learn about Transport Layer Security (TLS) for secure email communication.
  This guide explains how MailRoute supports TLS automatically and provides instructions
  for configuring TLS on popular email servers like Exchange, Postfix, and others.
draft: true
params:
  author: Unknown
summary: The article explains what Transport Layer Security (TLS) is and how MailRoute
  supports it for secure email communication without additional configuration. It
  also provides guidance for configuring TLS on popular email servers.
tags: null
title: TLS - Transport Layer Security
---


MailRoute supports full "opportunistic" TLS - it's automatic and it requires
no configuration on our end.

### What is "TLS"?

TLS stands for "Transport Layer Security". It's a way of encrypting data over
the internet to provide for secure end-to-end communications. If you really
want to get into the details, check out [Wikipedia's article on
TLS](http://en.wikipedia.org/wiki/Transport_Layer_Security).

### What is TLS for email?

TLS provides certificate-based authentication and encryption between any two
email servers that are so configured. All communications between the two
servers are secure, preventing eavesdropping and tampering.

### How does MailRoute support TLS?

MailRoute uses "opportunistic" TLS. This means that we advertise that we
support it, and we turn it on whenever an email server we are talking to
advertises its availability as well. Here's a simplistic explanation:

When a sending mailserver connects to us, we tell it that we support TLS. Our
two servers then exchange encryption keys, and switch to a secure form of
communication.

When we connect to an outside mailserver to relay an outbound message, we look
for TLS support on that server, and if it's there, we use that.

The end result is that any communication between MailRoute and any other
server that supports TLS will be secure. And there's no additional
configuration required on the MailRoute end.

### Do I need to do something on my email server to support TLS?

Yes, you do. You need to acquire the appropriate certificates, install them on
your email server, and configure it to use TLS. How you do this depends on
your email server. Here are some links to help you configure it on your end:

  * [Microsoft Exchange](https://docs.microsoft.com/en-us/microsoft-365/compliance/exchange-online-uses-tls-to-secure-email-connections?view=o365-worldwide)
  * [Postfix](http://www.postfix.org/TLS_README.html)
  * [Sendmail](http://www.sendmail.org/%7Eca/email/starttls.html)
  * [MDaemon](http://help.altn.com/mdaemon/en/ssl__certificates.html)

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

