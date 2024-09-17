---
created_at: 2013-01-29 20:34:12
date: 2021-03-02 17:43:50
description: Step-by-step guide on locking down a Mac OS X Server (10.4+) to only
  accept email from MailRoute servers by configuring SMTP relay settings in Server
  Admin.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions on how to lock down a Mac
  OS X Server (version 10.4 or later) to only accept email from MailRoute servers.
  It also includes a link to the Apple manual for more information on configuring
  the mail service.
tags: null
title: Mac OS X Server, 10.4 and Later - Locking Down the Server
---


Mac OS X Server 10.4 or later can be locked down to only accept email from the
MailRoute servers by following these steps:

  1. In **Server Admin** , select **Mail** in the **Computer & Services** pane
  2. Click **Settings**
  3. Select the **Relay** tab
  4. Check **Accept SMTP relays only from these** :
  5. Edit the list of hosts: 
    * Click the Add (+) button to add a host to the list: 199.89.0.0/21

For more information about configuring Mac OS X server, please see
http://manuals.info.apple.com/en_US/Mail_Service_v10.4.pdf

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

