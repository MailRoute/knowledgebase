---
created_at: 2013-01-17 03:04:24
date: 2021-03-02 17:43:50
description: Configure Microsoft Exchange 2003/2007 to only accept emails from MailRoute
  by modifying SMTP virtual server access settings and allowing specific IP range.
  Covers additional considerations.
draft: true
params:
  author: Unknown
summary: The article provides instructions on how to configure Microsoft Exchange
  2003 and 2007 servers to only accept email from MailRoute servers by modifying the
  SMTP virtual server settings and allowing a specific IP range. It also notes additional
  considerations regarding permissions, anonymous users, and disabling content filters.
tags: null
title: Microsoft Exchange 2003 & 2007 - Locking Down the Server
---


Microsoft Exchange 2003 and 2007 can be locked down to only accept email from
the MailRoute servers by following these steps:

  1. Open **Exchange System Manager**
  2. Go to **Servers - > [MailServer Name] -> SMTP**
  3. Right click and go to **Properties for Default SMTP Virtual Server**
  4. Click the **Access** tab
  5. Click **Connections**
  6. Choose **Only the List Below**
  7. Click **Add - > Group of Computers** and enter our network block: 
    * Subnet Address: **199.89.0.0**
    * Subnet Mask: **255.255.248.0**

Microsoft has an Administration Guide for Microsoft Exchange Server 2003
available at
http://www.microsoft.com/downloads/en/confirmation.aspx?FamilyID=98e45481-1458-4809-97d6-50d8aeebd8a1&displaylang=en

***

**NOTE** : If you stop receiving email and your configuration / firewall has
not changed, please check the permissions then select allow anonymous users.

Link to Microsoft Exchange Article About Permissions and Anonymous Users;
<http://technet.microsoft.com/en-us/library/bb629484(v=exchg.80).aspx>

**NOTE** : Content Filters and Sender IDs need to be disabled on the Exchange
server. If the server's mail traffic is filtered by MailRoute, it is not
necessary to keep them enabled.

Please see our article on how to do this
[here](https://support.mailroute.net/hc/en-us/articles/225721448)

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

