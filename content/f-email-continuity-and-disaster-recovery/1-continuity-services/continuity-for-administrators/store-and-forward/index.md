---
created_at: 2013-03-20 05:35:46
date: 2016-12-28 22:11:56
description: MailRoute's Store and Forward service acts as a backup for your email
  infrastructure, holding emails for up to 15 days if your server is down, ensuring
  no bounces and protecting your reputation. It's part of their Inbound filtering
  service, requiring no configuration.
draft: true
params:
  author: Unknown
summary: MailRoute's Store and Forward service provides a backup for your internal
  email infrastructure by holding your email for up to 15 days if your server is down,
  ensuring no email is bounced and your reputation is protected. It's an integral
  part of their Inbound email filtering service and requires no configuration or maintenance.
tags: null
title: Store and Forward
---


### Store and Forward

MailRoute's highly redundant cloud of email processing servers can provide a
backup to your internal email infrastructure.

Email is a complicated service to provide, and yet it's an absolute necessity
for just about all of us. If your server crashes, or if you have to take it
offline for upgrade or maintenance, MailRoute will hold your email for you for
up to 15 days, until your servers are back up and running, and ready to handle
taking on email delivery. This ensures that no email is bounced, and your
reputation is protected.

**How It Works**

The Store and Forward/Disaster Recovery service is an integral part of our
Inbound email filtering service. Once you change your MX record to direct
email to MailRoute, we filter it, and send it on its way to your server.

But if your server is down, or if you're installing a new version of the OS,
or if it's overloaded and out of disk space or RAM, or even if you're having
some sort of temporary internet connectivity problems, we will hold the email.
We don't bounce it back to the sender - that would be embarassing, like having
your phone disconnected. Instead, we queue it up, and retry your server
periodically, until we detect that it's back up and receiving email. Then we
feed the email at a slow pace to start, and ramp up speed if we see that your
server can handle it. We'll get all your stored email to you as quickly as
possible, and your email senders will never even know you were down.

**Features**

  * Fully automated
  * Requires no configuration or maintenance. We detect the downtime automatically, queue email, and initiate delivery when you're back up and running, with no intervention required.
  * MailRoute's highly available cloud network provides reliability that's incredibly difficult and expensive to create in-house.
  * Compatible with all email systems - regardless of platform or underlying operating systems
  * Implementation takes only minutes and is risk-free
  * 99.999% uptime guaranteed

**Benefits**

  * Risk-free implementation.
  * Filtering and blocking begin once you make the DNS change.
  * No embarrassing explanations to your customers or partners about why you can't seem to keep your email server running.
  * Reduced risk from valuable, critical mail messages being lost due to maintenance windows, planned, or unplanned downtime.
  * Increased server and network efficiency.
  * Solution does not require you to update servers or desktops.
  * Frees up valuable IT resources.
  * Requires no hardware or software.

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

