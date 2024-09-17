---
created_at: 2013-01-17 02:53:24
date: 2024-02-20 20:41:34
description: Get instructions to configure Microsoft Exchange 2007 & 2010 to send
  all outgoing emails through MailRoute's smart host. Covers Hub Transport settings,
  Edge Server config, and SPF settings.
draft: true
params:
  author: Unknown
summary: This article provides step-by-step instructions for configuring Microsoft
  Exchange 2007 and 2010 to send all outgoing emails through MailRoute's smart host
  or outbound service. It also includes additional notes for Edge Server configurations
  and SPF settings.
tags: null
title: Microsoft Exchange 2007 & 2010 - Configuring SmartHost or Outbound Service
---


Microsoft Exchange 2007 and 2010 can be configured to send all email out
through MailRoute with the following settings.

This article already assumes that your Exchange Server is able to send emails
externally, and so it must have a **Send Connector** properly set up and
configured correctly on the **Hub Transport Server**. And so we only need to
configure the settings on that **Send Connector**.

  1. Be sure you've added your mail server details to the Outbound Server tab in MailRoute's Control Panel.
  2. Open **Exchange Management Console.**
  3. Click on the ( **+** ) next to **Organization Configuration.**
  4. Select **Hub Transport** and
  5. Select the **Send Connectors** tab.
  6. Right-click on the existing **Send Connector** , select **Properties.**
  7. Choose the **Network** tab.
  8. Select **Route mail through the following smart hosts:** and click **Add**
  9. Choose the radio button labeled **Fully qualified domain name (FQDN):** and enter **outbound.mailroute.net**

  10. Click **OK**

**NOTE: If you use spf you will need to enter > "include:spf.mailroute.net".
It includes all our different servers that may relay email.**

The changes you've made should take effect without having to restart any
services.

Please feel free to contact us at
[support@mailroute.net](mailto:support@mailroute.net) if you have any
questions.

_______

**Exchange 2010 and Edge Server Config** ;  
If you haven't already done so and you provide Mailroute with the **Edge
Server IP** ; please be sure to change the **send connector** settings on the
**ES server** since the **ES** controls the configuration of the **Edge**
**server**.

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

