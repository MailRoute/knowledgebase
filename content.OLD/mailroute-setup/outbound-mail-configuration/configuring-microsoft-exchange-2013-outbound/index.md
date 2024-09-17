---
created_at: 2019-03-20 16:08:41
date: 2024-02-20 20:41:34
description: Configure Microsoft Exchange 2013 to route outbound email through a smart
  host by creating a new Send connector and specifying the smart host FQDN and address
  space.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions on how to configure a Send
  connector in Microsoft Exchange 2013 to route outbound email through a smart host.
  It explains the process of creating a new send connector and specifying the smart
  host details.
tags: null
title: Configuring Microsoft Exchange 2013 Outbound
---


## Use the EAC to create a Send connector to route outbound email through a
smart host

  1. In the EAC, navigate to **Mail flow** > **Send connectors** , and then click **Add** ![Add Icon](jj218640c1e75329-d6d7-4073-a27d-498590bbb55828exchg15029.gif).

  2. In the **New send connector** wizard, specify a name for the send connector such as MailRoute Outbound and then select **Custom** for the **Type**. You typically choose this selection when you want to route messages to computers not running Microsoft Exchange Server 2013. Click **Next**.

  3. Choose **Route mail through smart hosts** , and then click **Add** ![Add Icon](jj218640c1e75329-d6d7-4073-a27d-498590bbb55828exchg15029.gif). In the **Add smart host** window, specify the fully qualified domain name (FQDN), **outbound.mailroute.net**. Click **Save**.

For **Smart host authentication** , choose **None.**

  4. Under **Address space** , click **Add** ![Add Icon](jj218640c1e75329-d6d7-4073-a27d-498590bbb55828exchg15029.gif). In the **Add domain** window, make sure SMTP is listed as the **Type**. For **Fully Qualified Domain Name (FQDN)** , enter * to specify that this send connector applies to messages sent to any domain. Click **Save**.

  5. For **Source server** , click **Add** ![Add Icon](jj218640c1e75329-d6d7-4073-a27d-498590bbb55828exchg15029.gif). In the **Select a server** window, choose a server and click **Add** ![Add Icon](jj218640c1e75329-d6d7-4073-a27d-498590bbb55828exchg15029.gif). Click **OK**.

  6. Click **Finish**.

Once you have created the send connector, it appears in the Send connector
list.

## How do you know this worked?

To verify that you have successfully created a Send connector to route
outbound email through a smart host, send a message from a user in your
organization (you can use the Outlook Web App) to the domain you specified for
the **Address space**. If the recipient receives the message, you've
successfully configured the send connector.

This article was adapted from Microsoft's instructions
[here](https://docs.microsoft.com/en-us/exchange/create-a-send-connector-to-
route-outbound-email-through-a-smart-host-exchange-2013-help)

