---
created_at: 2013-05-30 01:25:14
date: 2021-03-02 17:48:54
description: Detailed instructions on configuring MX records for a domain using ZoneEdit
  DNS management service to enable email routing through MailRoute's servers. Covers
  logging in, domain selection, deleting existing records, and adding the proper MX
  entry.
draft: true
params:
  author: Unknown
summary: The article provides a step-by-step guide on how to configure MX records
  for a domain using the ZoneEdit DNS management service. It covers logging in, selecting
  the domain, deleting existing MX records, and adding the correct MX record for MailRoute.
tags: null
title: ZoneEdit
---


## MX Record Configuration: ZoneEdit

  1. [Log in](https://www.zoneedit.com) to your account at [ZoneEdit.com](https://www.zoneedit.com).
  2. Select the zone that has the MX entries you would like to change.
  3. Click **Mail Servers (MS)**.
  4. Delete the current entries: Select all checkboxes in the **delete** column.
  5. Press the **Delete** button.
  6. Click **Yes** to verify.
  7. Add the MX record: 
    * **MailServer** , add **mail.mailroute.net**. (note the trailing dot "."!)
    * Select * _1st *_ priority for the rank
    * Add the name of your domain.
    * Click **Add New Mail Server**.
  8. You will be asked to confirm the operation. Press **Yes**.

**Note:** If your MX record is not updating first check to make sure that the
@ symbol appears in the Subdomain window. The Type will be MX, the TTL can be
set to 1800, Set the Preference to 10 and the Host to mail.mailroute.net. If
there is still an issue please make sure that your A record is set up
correctly

[Click here for more information on configuring Zoneedit
settings.](https://support.zoneedit.com/index.php?/Knowledgebase/List)

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

