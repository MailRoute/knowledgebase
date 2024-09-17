---
created_at: 2016-08-19 18:23:57
date: 2022-09-02 15:35:56
description: MailRoute supports automatic TLS encryption for secure email communications,
  ensuring end-to-end protection against eavesdropping and tampering. Learn how to
  configure TLS on your email server.
draft: true
params:
  author: Unknown
summary: The article explains MailRoute's support for Transport Layer Security (TLS)
  encryption for email communications, ensuring secure end-to-end communication. It
  also provides guidance on configuring TLS on various email servers.
tags: null
title: Email Encryption by MailRoute
---


MailRoute’s team built the first cloud-based email filtering company, which we
sold to Microsoft in 2005. Then we built MailRoute, an improved version of the
original. After nearly 20 years in this industry, we offer email protection
based on what we consider to be best practices, including using TLS to encrypt
mail.

We are HIPAA and ITAR compliant, and sign BAA’s with our many customers who
are in the healthcare industry.

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
  * [MDaemon [link being fixed]](http://help.altn.com/mdaemon/en/ssl_mdaemon.html)

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

