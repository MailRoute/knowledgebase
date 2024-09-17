---
created_at: 2020-05-12 17:55:07
date: 2024-02-20 20:41:34
description: Detailed guide on how to configure Microsoft Exchange 2016 to send outbound
  email through MailRoute's outbound smart host service by creating a send connector.
  Covers prerequisites and verification steps.
draft: true
params:
  author: Unknown
summary: This article provides step-by-step instructions for configuring a Microsoft
  Exchange 2016 server to route outbound email through the MailRoute smart host service.
  It covers prerequisites, creating a send connector, and verifying the setup.
tags: null
title: Configuring Microsoft Exchange 2016 Outbound
---


##

## Before you configure the connectors:

## 1\. Make sure that under the Delivery in the MailRoute Control Panel,
select Outbound Servers. Enter the IP addresses of each of your email servers.

2\. Set your [SPF For Outbound](https://support.mailroute.net/hc/en-
us/articles/360021568194-Implementing-SPF-for-the-MailRoute-Outbound-
SmartHost-Service).

3\. Set up [DKIM](https://support.mailroute.net/hc/en-
us/articles/115009100687-Implementing-DKIM-for-the-MailRoute-Outbound-
SmartHost-Service), [ADSP and DMARC](https://support.mailroute.net/hc/en-
us/articles/360062946093-Implementing-DMARC-for-the-MailRoute-Outbound-
SmartHost-Service).

## Use the EAC to create a Send connector to route outbound email through a
smart host

  1. In the EAC, navigate to **Mail flow** > **Send connectors** , and then click **Add** ![Add Icon](jj218640c1e75329-d6d7-4073-a27d-498590bbb55828exchg15029.gif).

  2. In the **New send connector** wizard, specify a name for the send connector such as MailRoute Outbound and then select **Custom** for the **Type**. You typically choose this selection when you want to route messages to computers not running Microsoft Exchange Server 2013. Click **Next**.

  3. Choose **Route mail through smart hosts** , and then click **Add** ![Add Icon](jj218640c1e75329-d6d7-4073-a27d-498590bbb55828exchg15029.gif). In the **Add smart host** window, specify the fully qualified domain name (FQDN), **outbound.mailroute.net**. Click **Save**.

For **Smart host authentication** , choose **None.**

  4. Under **Address space** , click **Add** ![Add Icon](jj218640c1e75329-d6d7-4073-a27d-498590bbb55828exchg15029.gif). In the **Add domain** window, make sure SMTP is listed as the **Type**. For **Fully Qualified Domain Name (FQDN)** , enter * to specify that this send connector applies to messages sent to any domain. Click **Save**.

  * Cost: Verify 1 is entered. A lower value indicates a more preferred route for the domains you specified.

* Back on the previous page, the Scoped send connector setting is important if your organization has Exchange servers installed in multiple Active Directory sites:

    * If you don't select Scoped send connector, the connector is usable by all transport servers (Exchange 2013 or later Mailbox servers and Exchange 2010 Hub Transport servers) in the entire Active Directory forest. This is the default value.

    * If you select Scoped send connector, the connector is only usable by other transport servers in the same Active Directory site.

When you're finished, click Next.

5\. For **Source server** , click **Add** ![Add
Icon](jj218640c1e75329-d6d7-4073-a27d-498590bbb55828exchg15029.gif). In the
**Select a server** window, choose a server and click **Add** ![Add
Icon](jj218640c1e75329-d6d7-4073-a27d-498590bbb55828exchg15029.gif). Click
**OK**.

Click **Finish**.

Once you have created the send connector, it appears in the Send connector
list.

## How do you know this worked?

To verify that you have successfully created a Send connector to route
outbound email through a smart host, send a message from a user in your
organization (you can use the Outlook Web App) to the domain you specified for
the **Address space**. If the recipient receives the message, you've
successfully configured the send connector.

For the original documentation from Microsoft please see here:

<https://docs.microsoft.com/en-us/exchange/mail-flow/connectors/outbound-
smart-host-routing?view=exchserver-2016>

