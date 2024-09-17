---
created_at: 2013-05-30 01:24:44
date: 2021-03-02 17:48:54
description: Learn how to configure MX records on Registerfly.com to route your domain's
  email through MailRoute's secure email service. Step-by-step guide with screenshots.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring the MX records
  for the domain registrar Registerfly.com to use MailRoute's email service.
tags: null
title: Registerfly.com
---


## MX Record Configuration: Registerfly.com

  1. Log in to your account at [Registerfly.com](http://registerfly.com/).
  2. Click **Manage Domains**.
  3. Click the domain that you'd like to use with MailRoute.
  4. Expand **DNS Settings (Zone file)**.
  5. Click **Configure**.
  6. If asked to change name servers to registerfly nameservers, do so. If you have hosting that requires you to use other nameservers, these instructions may not work for you.
  7. Note your existing MX records, in case you need to revert to them later.
  8. Clear all existing MX Records by checking the box next to each record and clicking **Remove selection**.
  9. Add a new MX Record:
    * HostName: **@**
    * Record Type: **MX**
    * IP Address/URL: **mail.mailroute.net**
    * Pref: **10**

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

