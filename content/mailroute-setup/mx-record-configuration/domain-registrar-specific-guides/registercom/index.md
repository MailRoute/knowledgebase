---
created_at: 2013-05-30 01:24:40
date: 2022-09-02 17:50:45
description: Detailed guide on how to configure MX records at Register.com to enable
  email routing through MailRoute's mail servers. Includes step-by-step instructions
  and links to documentation.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring the MX record
  for the Register.com domain registrar to enable email routing through MailRoute's
  mail servers. It also includes a link to Register.com's documentation and information
  about MailRoute's free trial and support contacts.
tags: null
title: Register.com
---


## MX Record Configuration: Register.com

  1. Log in to your account at [www.register.com](https://www.register.com/).
  2. Under the blue **My Accounts** tab, click the domain that you're using with MailRoute.
  3. Scroll down to the **Advanced Technical Settings** heading, and click **Edit Mail Exchanger Records**.
  4. Add an MX record for "mail.mailroute.net.": 
    * Leave the **Host Name** field blank
    * Select the "High" **Priority** in the drop down
    * Enter the fully-qualified server name **mail.mailroute.net.** in the **Mail Server** field. Include the period at the end of the server name!
  5. Delete any existing MX records, or lower their priority.
  6. Click **Continue**.
  7. Review your changes, and click **Continue**.

[Click here to link to Register.com
documentation.](https://www.register.com/knowledge)

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

