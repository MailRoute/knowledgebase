---
created_at: 2020-02-03 17:09:10
date: 2021-03-02 17:48:54
description: Step-by-step guide to configure Zoho Mail for use with MailRoute email
  service by turning off spam filtering, pointing MX record to mail.mailroute.net,
  and addressing a potential Zoho alert.
draft: true
params:
  author: Unknown
summary: The article provides instructions on how to configure Zoho Mail to work with
  MailRoute by disabling spam filtering and pointing the MX record to mail.mailroute.net.
  It also mentions an alert that may be received from Zoho regarding the MX record
  change.
tags: null
title: 'Zoho '
---


To use MailRoute with Zoho, you will need to turn off spam filtering.

  * Login to [Zoho Mail account](https://www.zoho.com/mail) as domain administrator.
  * Click on **Control Panel** (on the top right) >> **Mail & Docs** >> **Mail Administration** >> **Org Settings**.
  * You will see an option ' **Organization Spam Process Type** ' - Click on the drop down button and select **Off**.
  * Click **Save**.
  * Log out of your account and Login again and the changes would be effective.

Once spam filtering is disabled, please point the **MX record** to
**mail.mailroute.net** and be sure you are set to the correct inbound server.

****** You will likely receive an alert from Zoho like this

"You are receiving the alert, as the domain XXXX added in Zoho for email
hosting, does not have the MX records pointed to Zoho Servers. As a result,
the emails to the domain based accounts will not be delivered to Zoho Mail.

Zoho states: We have a schedule to check the MX records for the domains hosted
with Zoho when we see the MX records are pointed to a different location we
give a notification stating that you may not receive emails, please ignore
this notification as it an alert for administrators who has incorrectly
pointed their MX record.

Fore more information, please see the full support thread
[here.](https://help.zoho.com/portal/community/topic/using-zoho-with-
mailroute-net)

[Start a a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

