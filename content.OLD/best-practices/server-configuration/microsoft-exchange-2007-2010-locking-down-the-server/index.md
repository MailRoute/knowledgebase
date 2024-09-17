---
created_at: 2013-01-29 20:34:09
date: 2021-03-02 17:43:50
description: Step-by-step guide on locking down Microsoft Exchange 2007 & 2010 servers
  to only accept email from MailRoute servers by configuring the receive connector
  settings, allowing anonymous users, and disabling content filters and sender IDs.
draft: true
params:
  author: Unknown
summary: The article explains how to configure Microsoft Exchange 2007 and 2010 servers
  to only accept email from MailRoute servers by modifying the receive connector settings.
  It also provides a note on allowing anonymous users and disabling content filters
  and sender IDs for MailRoute-filtered traffic.
tags: null
title: Microsoft Exchange 2007 & 2010 - Locking Down the Server
---


Microsoft Exchange 2007 can be locked down to only accept email from the
MailRoute servers by following these steps:

  1. Open **Exchange Management Console**
  2. Under the **Server Configuration** node, select **Hub Transport**
  3. Choose the receive connector you are using for your incoming SMTP traffic, right click and select **Properties**
  4. Click the **Network** tab
  5. Find where it says **Receive mail from remote servers which have these IP addresses**
  6. Select **Add - > IP Address**
  7. In the **Add IP address(es) of Remote Servers** box, enter the MailRoute network in CIDR notation:
    
        199.89.0.0/21
    

  8. There is probably a default entry in there for an address range that will need to be removed, because it allows connection from any IP address. It looks like this:
    
        0.0.0.0 - 255.255.255.255
    

These changes should take effect right away without having to restart any
services, but we have seen some instances where a restart of Exchange services
is required.

Microsoft has online documentation on how to do this at
http://technet.microsoft.com/en-us/library/bb691331(EXCHG.80).aspx

You may need to refer to other sections of that technical reference document
if your Exchange configuration is non-standard.

___________

**NOTE: If you stop receiving email and your configuration / firewall has not
changed please check the permissions and select allow anonymous users**

**<http://technet.microsoft.com/en-us/library/bb629484(v=exchg.80).aspx>**

**NOTE** : Content Filters and Sender IDs need to be disabled on the Exchange
server. If the server's mail traffic is filtered by MailRoute, it is not
necessary to keep them enabled.

Please see our article on how to do this
[here](https://support.mailroute.net/hc/en-us/articles/225721448)

Start a free 30-day trial today.

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

