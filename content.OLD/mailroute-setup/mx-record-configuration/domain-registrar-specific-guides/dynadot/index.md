---
created_at: 2013-05-30 01:23:23
date: 2021-03-02 17:48:54
description: Detailed guide on how to set up MX records for your domain hosted with
  Dynadot to route inbound email through Mailroute's filtering service, covering MX
  entry changes in both Mailroute and Dynadot admin interfaces.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring MX records
  for the Dynadot domain registrar and hosting provider, including adding inbound
  mail servers in the Mailroute admin panel and updating MX record entries in the
  Dynadot control panel.
tags: null
title: Dynadot
---


## MX Records: Dynadot

  1. Log into [Mailroute.net](https://admin.mailroute.net/accounts/login) and navigate to **All Domains** -> **Delivery** -> **Inbound Servers**
  2. Delete any existing MailServer entries (with the red ‘x’ on the right)
  3. Click **Add** , and enter **mail.yourdomain.com** , and a priority of **0,** where you need to use the actual domain name hosted at Dynadot. 
  4. Log into [Dynadot.com](https://www.dynadot.com/account/signin.html) and navigate to **Your Account** -> **Summary**
  5. If using **cPanel** , select **Local** **Mail** **Exchanger** and make sure it saves
  6. Click on the **cPanel** login at the bottom of the page, under ‘Dynadot Hosting’, and log in to cPanel
  7. In the **Mail** section, click on **MX Entry**
  8. Select the domain name that’s associated with the e-mail accounts you want to filter
  9. Delete any existing MX Records
  10. Add a new record with priority **0** and destination **mail.mailroute.net**

****

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

