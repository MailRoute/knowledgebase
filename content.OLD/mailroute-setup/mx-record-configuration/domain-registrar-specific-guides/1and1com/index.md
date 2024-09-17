---
created_at: 2013-05-30 01:23:05
date: 2021-03-02 17:48:54
description: Detailed guide with screenshots explaining how to edit DNS settings on
  1and1.com to change MX records and point your domain's email to mail.mailroute.net
  for email delivery.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions on how to configure MX records
  for the domain name hosted on the 1and1.com platform to point to the mail.mailroute.net
  server for email delivery.
tags: null
title: 1and1.com
---


## MX Records: 1&1

  1. [Log in](https://www.1and1.com) to your **[1&1 Control Panel](https://www.1and1.com).**
  2. Click **Manage Domains** from the Domains panel.

![Domains_section.jpg](.jpeg)

3\. Click the **arrow icon** next to the domain name in question to display an
options menu.

![scr_mx_Records_01.jpg](.jpeg)

4\. Select **Edit DNS Settings** from the **Domain Settings** section of the
options menu.

![scr_A_record_02.jpg](.jpeg)

5\. Delete any existing MX records.

6\. Enter the following information:

  * Select **Other mail server** radio button from the Mail Exchanger (MX Records) section.
  * MX 1
  * MailServer: **_mail.mailroute.net_**
  * Priority: 10

7\. Click the **Save** button to save your changes.

![scr_mx_Records_03.jpg](.jpeg)

8\. A confirmation page is displayed informing you that the changes will be
updated accordingly.

As with all DNS changes, it may take up to **one hour** before the changes are
recognized by all servers/computers on the Internet.

![scr_mx_Records_04.jpg](.jpeg)

**PLEASE TAKE NOTE:** List mail.mailroute.net as your only MX. If you select
to use the 1and1 servers as your backup you will stop receiving email.

Source: <http://help.1and1.com/domains-c36931/manage-
domains-c79822/dns-c37586/editchange-the-domain-s-mail-servers-mx-
record-a594907.html>

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

