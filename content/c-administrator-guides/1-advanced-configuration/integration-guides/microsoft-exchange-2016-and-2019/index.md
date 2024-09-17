---
created_at: 2017-10-13 18:14:54
date: 2022-03-09 17:35:48
description: Detailed guide on configuring Microsoft Exchange 2016 and 2019 servers
  to relay outbound emails through MailRoute's SmartHost service. Covers prerequisites
  like SPF, DKIM, DMARC setup and creating a receive connector.
draft: true
params:
  author: Unknown
summary: This article provides step-by-step instructions for configuring Microsoft
  Exchange 2016 and 2019 servers to work with the MailRoute outbound SmartHost service.
  It covers important prerequisites like setting up SPF, DKIM, and DMARC, as well
  as creating a receive connector in the Exchange Admin Center.
tags:
- image-missing
title: Microsoft Exchange 2016 and 2019
---


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

For Configuring Exchange with MailRoute, login to your Exchange Admin Center:

  1. In the EAC, go to **Mail flow** > **Receive connectors** , and then click **Add** ().

  2. The **New receive connector** wizard opens. On the first page, configure these settings:

    * **Name** Type something descriptive. For example, Email Relayed Through MailRoute.

    * **Role** Select **Frontend Transport**.

    * **Type** Select **Partner**. (The Receive connector will receive mail from a trusted third party)

When you're finished, click **Next**.

  3. On the second page of the wizard, do one of these steps in the **Network adapter bindings** section:

    * Leave the default values of **IP addresses** : **(All available IPv4)** and **Port** : **25**.

    * If it's required for your scenario, you can restrict the Receive connector to a valid local IP address on the server:

      1. Select the default entry **IP addresses** : **(All available IPv4)** and **Port** : **25** , and then click **Edit** ().(Simple Mail Transfer Protocol uses port 25.) This indicates that the connector listens for connections on all IP addresses assigned to network adapters on the local server.

      2. In the **Edit IP address** dialog that opens, configure these settings:

        * **Address** Select **Specify an IPv4 address or an IPv6 address** , and type in a valid local IP address to use for the connector.

        * **Port** Leave the default value **25** selected.

When you're finished, click **Save**.

When you're finished, click **Next**.

    1. On the last page of the wizard, configure these settings in the **Remote network settings** section:

a. Select the default entry **0.0.0.0-255.255.255.255** , and then click
**Edit** ().

b. In the **Edit IP address** dialog that opens, enter the IP address or IP
address range of Partner

c. Add the Partner (MailRoute) address range: 199.89.0.0 - 199.89.7.255.

When you're finished, click **Save**

When you're finished, click **Finish.**

**. Please note that when you are logged in to the EAC you must Check the box
for allowing "Anonymous users".

EAC > Mail Flow > Receive connectors > edit Client Frontend, the role of
FrontendTransport, "Exchange Receive Connector" window will pop up. In this
window: Security > Checkbox "Anonymous users" and Save

Information curtesy of and for full information please go to:
<https://docs.microsoft.com/en-us/exchange/mail-flow/connectors/custom-
receive-connectors?view=exchserver-2019>

**NOTE** : Content Filters and Sender IDs need to be disabled on the Exchange
server. If the server's mail traffic is filtered by MailRoute, it is not
necessary to keep them enabled.

Please see our article on how to do this
[here](https://support.mailroute.net/hc/en-us/articles/225721448)

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

