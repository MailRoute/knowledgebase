---
created_at: 2014-09-08 22:35:07
date: 2022-03-09 17:36:51
description: Detailed guide on configuring Microsoft Exchange 2013 to integrate with
  MailRoute's outbound smarthost service, covering necessary steps like receive connector
  setup, SPF, DKIM, and DMARC implementation.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions on how to configure Microsoft
  Exchange 2013 to work with the MailRoute outbound smarthost service, including setting
  up receive connectors, SPF, DKIM, and DMARC.
tags: null
title: Microsoft Exchange 2013
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

**NOTE** : add the address range: 199.89.0.0 - 199.89.7.255 in Step #5  
  
Use the EAC to Create a Receive Connector to Receive Secure Messages from a
Partner

  1. In the EAC, navigate to **Mail flow** > **Receive connectors**. Click **Add** to create a new Receive connector.
  2. On the **New receive connector** page, specify a name for the Receive connector and then select **Frontend Transport** for the **Role**. Since you are receiving mail from a partner in this case, we recommend that you initially route mail to your front end server to simplify and consolidate your mail flow.
  3. Choose **Partner** for the type. The Receive connector will receive mail from a trusted third party.
  4. For the **Network adapter bindings** , observe that **All available IPV4** is listed in the **IP addresses** list and the **Port** is 25. (Simple Mail Transfer Protocol uses port 25.) This indicates that the connector listens for connections on all IP addresses assigned to network adapters on the local server. Click **Next**.
  5. If the Remote network settings page lists 0.0.0.0-255.255.255.255, which means that the Receive connector receives connections from all IP addresses, click **Remove** to remove it. Click **Add** , add the IP address for your partner’s server, and click **Save**.
  6. Add the address range: 199.89.0.0 - 199.89.7.255
  7. Click **Finish** to create the connector.
  8. Once you have created the Receive connector, it appears in the Receive connector list. If you would like to see an example of how to create a Receive connector with a cmdlet, see [New-ReceiveConnector](http://technet.microsoft.com/en-us/library/bb125139%28v=exchg.150%29.aspx). <http://technet.microsoft.com/en-us/library/jj673037%28v=exchg.150%29.aspx>

* While logged in to the EAC, you must also select to allow "Anonymous users"

Go to: EAC > Mail Flow > Receive connectors > edit Client Frontend, the role
of FrontendTransport, "Exchange Receive Connector" window will pop up. In this
window: Security > Checkbox "Anonymous users" and Save

**NOTE** : Content Filters and Sender IDs need to be disabled on the Exchange
server. If the server's mail traffic is filtered by MailRoute, it is not
necessary to keep them enabled.

Please see our article on how to do this
[here](https://support.mailroute.net/hc/en-us/articles/225721448)

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

