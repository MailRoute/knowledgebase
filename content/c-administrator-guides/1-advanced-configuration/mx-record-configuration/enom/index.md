---
created_at: 2013-05-30 01:23:30
date: 2021-03-02 17:48:54
description: Step-by-step guide to configuring MX records for the domain registrar
  Enom to enable email routing through MailRoute, a hosted email service. Detailed
  instructions with screenshots.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring MX records
  for the domain registrar Enom to enable email routing through MailRoute.
tags: null
title: Enom
---


## MX Record Configuration: Enom

  1. Log in to your account at [Enom.com](https://www.enom.com/login.aspx?)
  2. Under the **Domains** menu, click **My Domains**.
  3. From your domain list, click on the domain name you’d like to use with MailRoute.
  4. Click **Email Settings** or from the **Manage Domain** drop-down list, click **Email Settings**.
  5. Change the **Service Selection** to "User (MX)”.
  6. Enter the MailRoute record: 

  * Enter a **Host Name** , leave the default setting to **@**.
  * Next to **Goes To Address** enter **_mail.mailroute.net_**
  * Set the Pref Value to **10**

7\. Click the **Save** button.

**Note:** It can take from 24-48 hours for changes in DNS to propagate.

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

