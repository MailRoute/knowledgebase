---
created_at: 2013-05-30 01:23:26
date: 2021-03-02 17:48:54
description: Detailed guide on setting up MX records for email routing via MailRoute
  using the DynDNS DNS service, including updating preference values and pointing
  to MailRoute mail servers.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring MX records
  using the DynDNS DNS management service to properly route email through the MailRoute
  email hosting service.
tags: null
title: DynDNS
---


## MX Record Configuration: DynDNS

  1. Log in to your account at [dynDNS](http://dyn.com/managed-dns-express/).
  2. Click **My Services** below your username.
  3. Under **Zone Level Services** , Click **Custom DNS** next to the domain you will be using with MailRoute.
  4. Under **Mail eXchanger (MX) Records** , note your existing MX records, in case you need them later.
  5. Then select all existing domains, and click **Delete MX**. (If you currently have no MX records created, you won't see an option to Delete MX, in that case, skip this step).
  6. Next to **Mail eXchanger (MX) Records** , click **Add New MX**.
  7. For **Preference** , select **5 -- Highest**.
  8. For **Mail Exchanger** , enter **_mail.mailroute.net._** (don't forget the trailing dot "."!)
  9. Click **Modify MX**.
  10. Click **Return to** , if you have more than one mail server and continue to set the mx record and preference. 

  * It may take up to 48 hours for the changes to take effect.

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

