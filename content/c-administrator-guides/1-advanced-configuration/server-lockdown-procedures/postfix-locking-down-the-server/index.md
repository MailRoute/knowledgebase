---
created_at: 2013-01-29 20:34:16
date: 2021-03-02 17:43:50
description: Learn how to configure Postfix email server to only accept emails from
  MailRoute servers by modifying the main.cf file and setting appropriate network
  and client restrictions.
draft: true
params:
  author: Unknown
summary: The article provides a general guide on how to lock down the Postfix email
  server to only accept emails from MailRoute servers by modifying the main configuration
  file and specifying the appropriate network and client restrictions.
tags: null
title: Postfix - Locking Down the Server
---


Postfix can be locked down to only accept email from the MailRoute servers.
Because of the wide range of possibilities for postfix configuration, please
consider this a general guide, and not a hard-and-fast set of instructions.

  1. Edit your **main.cf** file. This is usually found in **/etc/postfix/main.cf**
  2. Add **199.89.0.0/21** to **mynetworks**
  3. Set **smtpd_client_restrictions = permit_mynetworks, reject**
  4. Execute **postfix reload** to reload the settings and have them take effect right away

Please feel free to contact us at
[support@mailroute.net](mailto:support@mailroute.net) if you have any
questions. We use postfix ourselves, and we'll do whatever we can to help.

***for OS X Servers; Add our addresses to mynetworks, change
"smtpd_client_restrictions" as specified, and then restart the server. On a
mac, that might require a reboot.

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

