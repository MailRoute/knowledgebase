---
created_at: 2013-01-17 02:48:25
date: 2024-02-20 20:41:34
description: Detailed guide on configuring an SMTP connector in Microsoft Exchange
  2003 to send all outgoing emails through MailRoute's smarthost outbound.mailroute.net
  for email routing and delivery.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions on how to configure a smarthost
  or outbound service for Microsoft Exchange 2003 to route emails through MailRoute's
  service.
tags: null
title: Microsoft Exchange 2003 - Configuring SmartHost or Outbound Service
---


How To Configure a Smarthost on Exchange 2003

Open **Exchange System Manager** and click on the **+** next to **Connectors**
to see if you are already using an SMTP Connector.

If you need to create a new connector:  
Right-click on **Connectors** and select **New - SMTP Connector...**

If a SMTP Connector already exists: Right-click on it and choose
**Properties**

The **SMTP Connector - Properties** page opens which has 8 tabs.

(There could be a 9th tab called **Security** if you've previously enabled
this tab by a registry change, but, in any case, there's nothing to configure
on this tab.)

We'll start on the **General** tab where there are 3 things to configure:

  1. **Name**

Call it what you want, but " **All Outgoing Email** " is a good name.

  2. **Smarthosts**

Select " **Forward all mail through this connector to the following smart
hosts** " and enter MailRoute's smarthost.  
The full string to enter is: **outbound.mailroute.net**

"Copy and Paste" the above line into your **SMTP Connector** if you like.

  3. **Bridgehead Server**

This is your Exchange server.  
Click **Add...** and there will only be one option.

Go to the **Address Space** tab.

Click **Add...** and select the default options which are:

    
    
        Type = SMTP  
        Email Domain = *  
        Cost = 1  
        Connector scope = Entire Organisation  
    
        "**Allow messages to be relayed to these domains**" is **_not_** selected
    

Click **OK** and close **Exchange System Manager**.

In order for the new settings to take effect, you need to restart the
following services:  
* **Microsoft Exchange Routing Engine** * **Simple Mail Transport Protocol (SMTP)**.

Rebooting the server will also enable the new settings, if this is easier.

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

