---
created_at: 2013-05-30 01:20:40
date: 2022-09-02 17:04:31
description: Detailed guide on how to configure MX records for Dreamhost to enable
  email delivery through MailRoute's third-party email service. Includes links to
  relevant Dreamhost resources.
draft: true
params:
  author: Unknown
summary: This article provides step-by-step instructions for configuring MX records
  for the email hosting service Dreamhost to work with MailRoute, a third-party email
  service. It also mentions additional resources from Dreamhost about using their
  services with outside email providers.
tags: null
title: Dreamhost
---


## MX Record Configuration: Dreamhost

  1. Log in to your account at [Dreamhost](https://panel.dreamhost.com).
  2. Click **Main Menu** Select **Mail** and then [Custom MX](https://help.dreamhost.com/hc/en-us/articles/215035328-Configuring-custom-MX-records)
  3. Under **Manage Email Delivery** , Click **Edit** next to the domain you will be using with MailRoute.
  4. Under **Custom MX Records** , note your existing MX records, in case you need them later.
  5. Delete any existing MX records.
  6. In the first entry where it says " **MX record** required", enter **10 mail.mailroute.net**
  7. Select the checkbox " **I will still check my email at Dreamhost"**
  8. Click **Update your custom MX records now!**
  9. Be sure to set your mailservers here at MailRoute with the appropriate mail servers that Dreamhost specifies where it says "Dreamhost MX Records". They will look something like "mx1.sub3.homie.mail.dreamhost.com". You can learn more about setting your mailservers up at MailRoute [here.](https://support.mailroute.net/hc/en-us/articles/115000393247-Inbound-Mail-Delivery-Servers)

Dreamhost has [their own article on using Dreamhost with outside email
providers](https://help.dreamhost.com/hc/en-us/articles/216445687-Mail-
Service-Providers).

Please see under "Extra Step Needed For Anti-Spam Users" in the Dreamhost wiki
link.

The only comment I can add to that is that their budgetary suggestions under
Section 1 of "How to use an MSP with Dreamhost" is inaccurate. We're much less
expensive than that!

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

