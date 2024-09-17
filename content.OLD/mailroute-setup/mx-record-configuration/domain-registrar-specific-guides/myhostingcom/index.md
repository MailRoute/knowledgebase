---
created_at: 2013-05-30 01:24:08
date: 2021-03-02 17:48:54
description: Detailed guide on configuring MX records for myhosting.com domain to
  route email through Mailroute's servers. Features step-by-step screenshots and additional
  information.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions on how to configure the MX
  record for the domain myhosting.com to point to Mailroute's mail servers.
tags: null
title: myhosting.com
---


## MX Record Configuration: myhosting.com

  1. Go to [myhosting.com](https://myhosting.com/).
  2. Click the **Account** link at the top of the page.
  3. Log in with your Domain Name and Password.
  4. Click the **Domain Name** tab.
  5. Click **DNS Management** in the left-hand pane.
  6. Click the **Manage DNS** button.
  7. Delete the existing **MAIL (MX) RECORDS**.
  8. Add the following **MAIL (MX) RECORD** :
    * Zone: **@**
    * Server: **_mail.mailroute.net._** (don't forget the trailing dot "."!)
    * Priority: **10**

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

