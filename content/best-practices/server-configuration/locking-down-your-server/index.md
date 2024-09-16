---
created_at: 2013-09-25 18:38:51
date: 2022-09-01 21:49:23
description: Learn how to lock down your mail server and restrict access to MailRoute's
  IP address block, preventing spammers and viruses from sending unwanted email directly
  to your server. Includes instructions for various server environments.
draft: true
params:
  author: Unknown
summary: The article provides instructions on how to lock down your mail server by
  restricting access to a specific block of IP addresses used by MailRoute, a third-party
  email service. This prevents spammers and viruses from connecting directly to your
  server and sending unwanted email.
tags: null
title: 'Locking Down Your Server '
---


**Very Important:** Do you control your firewall or mail server directly? If
not (perhaps because you use a third-party hosted email service without this
level of control), you won't be able to lock down your server directly.
Instead, you can create a simple rule in your email software (e.g., Outlook)
to remove email that bypassed MailRoute and was sent directly to your mail
server.

**[Click here](https://support.mailroute.net/hc/en-
us/articles/224059228-Reduce-Spam-on-Shared-Servers-Lockdown-) for more
details on shared servers.**

**I run my own mail server:**

Restrict access to your mailserver to our block of IP addresses: This prevents
spammers or viruses from connecting directly to your server and transferring
unwanted email. In our experience, many spammers store away old settings, so
some will have your old MX record archived, and will use that. Others use
portscanning, or simple guessing to find mail servers that are accepting
traffic on Port 25. Locking down this port allows you to prevent this from
happening.

There is one potential "gotcha": if you do this, you need to make the
appropriate accommodations for any mobile users you have who might be relaying
mail through your mail server. Many of our customers will require these remote
users to use SMTP authentication, or will add an SMTP service on a non-
standard port (like 2525), and have their users connect there instead of Port
25.

All MailRoute traffic will come from our block of addresses. It's a block of 8
Class C networks:

CIDR notation: 199.89.0.0/21  
Netmask notation: 199.89.0.0 with a netmask of 255.255.248.0  
Address range: 199.89.0.0 through 199.89.7.255

Articles for different in-house server environments:

[Office 365](https://support.mailroute.net/hc/en-us/articles/224059328--
Office-365-with-MailRoute)

[Allowing Mail From Mailroute](https://support.mailroute.net/hc/en-
us/articles/224059308)

[Exchange 2003 - 2007 - Locking Down The
Server](https://support.mailroute.net/hc/en-us/articles/224059088 "Exchange
2003 - 2007 Locking Down The Server")

[Exchange 2007-2010 - Locking Down The
Server](https://support.mailroute.net/hc/en-us/articles/224059108 "Exchange
2007-2010 Locking Down The Server")

[Configuring Exchange 2013](https://support.mailroute.net/hc/en-
us/articles/224059248 "Exchange 2013 Locking Down The Server")

[Mac OS X Server, 10.4 and Later - Locking Down The Server
](https://support.mailroute.net/hc/en-us/articles/224059148 "Mac OS X 10.4 and
Later Locking Down The Server ")

[Postfix - Locking Down The Server](https://support.mailroute.net/hc/en-
us/articles/224059128 "Postfix Locking Down The Server")

[SendMail - Locking Down The Server](https://support.mailroute.net/hc/en-
us/articles/225721408 "SendMail Locking Down The Server")

If you have further questions, please let us know.

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

