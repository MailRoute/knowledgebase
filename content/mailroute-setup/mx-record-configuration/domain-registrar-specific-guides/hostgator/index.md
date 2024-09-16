---
created_at: 2013-05-30 01:23:48
date: 2021-03-02 17:48:54
description: Detailed guide on configuring MX records in HostGator's cPanel for routing
  email through MailRoute. Covers adding a new MX record, selecting the correct mail
  exchanger option, and removing old MX records.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions on how to configure MX records
  for HostGator's cPanel to set up email routing through MailRoute. It highlights
  the importance of selecting the "LOCAL Mail Exchanger" option.
tags: null
title: HostGator
---


## MX Record Configuration: HostGator

  1. Log in to your HostGator cPanel account.
  2. In the **Mail** section, click **MX Entry**.
  3. If you have more than one domain, select the domain you’re using with MailRoute - look for this under the **Domain** heading.
  4. Under **Email Routing** , select _ **LOCAL**_ **Mail Exchanger** (PLEASE DO NOT SELECT REMOTE OR AUTO)
  5. Click the **Change** button.
  6. In the **Add New Record** section, create an MX record for MailRoute: 
    * Priority: **1**
    * Destination: **mail.mailroute.net**
  7. Under **MX Records** , note any old MX records, in case you need them later.
  8. Under **MX Records** , delete any original MX records

_________

**PLEASE NOTE** : After adding our mx records it has been reported that the
Mail Exchanger either sets to Auto Detect or Remote. Please be sure to select
**LOCAL MAIL EXCHANGER** and click **CHANGE. You may have to do this more than
once to ensure that the setting sticks.** LOCAL M.E is the only setting that
will allow mail to start flowing correctly.

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

