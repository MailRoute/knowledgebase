---
created_at: 2022-01-19 21:54:20
date: 2024-03-08 00:05:51
description: Comprehensive guide on configuring Microsoft 365/Office 365 to properly
  route outbound email through MailRoute's email filtering service for enhanced security
  and spam protection.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring Microsoft
  365/Office 365/O365 to route outbound email through MailRoute, a third-party email
  filtering service. It covers setting up inbound and outbound transports, configuring
  DNS records, and advanced filtering to improve security and reduce false positives.
tags: null
title: 'Configuring Microsoft 365/Office 365/o365 Outbound '
---


Configure Outbound email flow so that outbound mail is properly protected by
MailRoute.

MailRoute **will automatically recognize** that you are using Office 365 for
your outbound service, so **you do not need to enter an outbound mailserver in
the MailRoute Control Panel.**

Configuring Microsoft Office 365 for MailRoute takes a few steps. But it's
important that they be done in order. This article makes it look like it's a
lot, but we've tried to be very complete and show you each and every step
along the way. It's not really that difficult.

The first step is to configure MailRoute for your inbound email flow. If
you're a new customer, we may have already done this for you. If you are
changing from another service or an in-house server, you may need to do this
yourself (or ask us to help!)

Then we will set up Transports to handle inbound and outbound email flow, and
a rule that prevents anyone from bypassing MailRoute and sending email
directly to Microsoft.

Microsoft talks about some of this stuff in their article [Managing mail flow
using a third-party cloud service with Exchange
Online](https://learn.microsoft.com/en-us/exchange/mail-flow-best-
practices/manage-mail-flow-using-third-party-cloud)

We're going to do these things in order:

  1. Configure MailRoute with your **Inbound Email Server**
  2. Change your MX record to **mail.mailroute.net**
  3. Add your **SPF, DKIM, DMARC, and ADSP** records to your DNS server
  4. Configure an **Inbound Transport** in Exchange online to allow Office 365 to identify that your mail is coming from a trusted partner who is doing email filtering for you
  5. Configure an **Outbound Transport** to tell Office 365 to send your outbound mail out through MailRoute
  6. Configure **Advanced Filtering for Connectors in Exchange Online** to improve your filtering and reduce false-positives on the Microsoft side

# Step 1. (Which we may have already done for you!) - Configure Inbound Email
Server in MailRoute Control Panel

  * Locate your Office 365 mailserver hostname in the Microsoft 365 Admin Center: <https://admin.microsoft.com/#/Domains>
    * Select your domain, and then click **DNS records**. You'll find your inbound Office 365 mailserver listed in the **MX** record under **Microsoft Exchange**. It will look something like this: **example-com02c.mail.protection.outlook.com  
  
**

    * Visit the MailRoute Admin center at <https://admin.mailroute.net,> and select **Domains** at the top, and then click on your domain in the list  
![Image](17543574974227.png)  
  

    * Then Choose **Inbound Servers** from the menu at the left, and then click the **Add** button:  
![Image](17543574981907.png)  
  

    * Enter in the Office 365 Mailserver, and set the priority to **10** , and click **Save** :  
![Image](17543583233555.png)  
  

    * Set your **Server Type** by clicking the edit button, and then setting the **Type** to **Office 365** and then clicking **Save.**  
![Image](17543583235731.png)![Image](17543583236883.png)

**Note:** MailRoute will automatically recognize that you are relaying email
out from Microsoft, so there is no need to set up an Outbound server in the
MailRoute Control Panel for your outbound mail.

  
  
  
  

# Step 2. Change your MX Record to **mail.mailroute.net**

This will start the flow of email through MailRoute!

We have articles on how to do this for many common DNS providers at
<https://support.mailroute.net/hc/en-us/sections/205311968-Changing-MX-
Records>

  
  

# Step 3. Add SPF, DKIM, DMARC, and ADSP records

To properly protect your outbound mail, add your SPF, DKIM, DMARC, and ADSP
records while you're in there changing your MX record.

We have a primer on what all these are for, if you're interested here:
<https://support.mailroute.net/hc/en-us/articles/360061128614-Email-
Authentication-An-Explanation-and-Exploration>

We have a Knowledge Base articles for each of these:

  * <https://support.mailroute.net/hc/en-us/articles/360021568194-Setting-Your-SPF>
  * <https://support.mailroute.net/hc/en-us/articles/115009100687-Implementing-DKIM>
  * <https://support.mailroute.net/hc/en-us/articles/360062946093-Implementing-DMARC-for-the-MailRoute-Outbound-SmartHost-Service>

##  
  

# Step 4. Configure Inbound Transport

Microsoft uses an inbound **Transport** to identify email that comes in via
MailRoute to prevent false-positives from their own email filtering.

  * Visit <https://admin.exchange.microsoft.com/#/connectors> to manage your connectors.
  * Click **Add a connector**  
![Image](17543583239059.png)  
  

  * Choose **Partner organization** and click **Next:  
**  
![Image](17543574999571.png)

  * Give your connector a name like **MailRoute Inbound** , be sure **Turn it on** is selected, and then click **Next:**  
  
![Image](17543575001491.png)  
  

  * In **Authenticating sent email** , choose the option **By verifying that the sender domain matches one of the following domains** , enter ***.mailroute.net** and click the **+** (plus) icon to add this sender domain. After it's added, click **Next:  
![Image](17543583246611.png)  
**

  * In **Security restrictions** , choose the checkboxes **Reject email messages if they aren't sent over TLS** and **And require that the subject name on the certificate that the partner uses to authenticate with Office 365 matches this domain name** and enter ***.mailroute.net** into the text field, and then click **Next:  
  
** **![Image](17543583249683.png)  
  
**

  * In **Review connector** , verify that everything looks good, and then click **Create connector** :  
  
![Image](17543583251859.png)

  
  
  
  

# Step 5. Configure Outbound Transport

Microsoft uses an outbound **Transport** to identify route outbound email out
through MailRoute, so that we can improve our filtering accuracy and give your
domain even more protection.

  * If you're not still there, visit <https://admin.exchange.microsoft.com/#/connectors> to manage your connectors.
  * Click **Add a connector**  
![Image](17543583239059.png)  
  

  * In the **New connector** window, choose **Connection from Office 365** and **Connection to Partner organization** , and click **Next** :  
  
![Image](17543583255955.png)  
  

  * Give your connector a name like **MailRoute Outbound** , be sure **Turn it on** is selected, and then click **Next:**  
  
![Image](17543583258771.png)  
  

  * In **Use of connector** , choose **Only when email messages are sent to these domains.** Then enter ***** in the text field and click the **+** (plus) icon to add this sender domain: **  
![Image](17543575019283.png)  
  
**

  * After it's added, click **Next:  
  
![Image](17543575022227.png)  
  
**

  * On the **Routing** window, choose **Route email through these smart hosts** , enter **outbound.mailroute.net** into the text field and click the **+** (plus) icon to add this SmartHost:  
  
![Image](17543583265043.png)  
  
  
  

  * Now that it's been added, click **Next** :  
  
![Image](17543583266707.png)

  * Under **Security restrictions** , choose **Always use Transport Layer Security...,** and then **Issued by a trusted certificate authority (CA)** and **Add the subject name or subject alternative name (SAN) matches the domain name** and enter ***.mailroute.net** into the text field, and click **Next:**  
  
![Image](17543583268371.png)  
  

  * in **Validation email** , enter the email address **test@mailroute.net**. (Please note, that because of spam problems coming from Microsoft (yes, seriously), we don't allow relay to other addresses for this test, so only **test@mailroute.net** will work for this verification test. Enter the email address into the text field, and then click **+** (the plus symbol) to add the address:  
  
![Image](17543583271187.png)  
  
  

  * Then click **Validate** and wait a bit for the test to run.  
  
![Image](17543583274003.png)  
  

  * Once it's done, and it shows that it's successful, click **Next** :  
  
![Image](17543575043475.png)

  * In **Review connector,** make sure it all looks good, and hit **Create connector,** and then press **Next** to finish this up! **  
  
![Image](17543583279251.png)  
**

# Step 6. Configure Advanced Filtering for Connectors in Exchange Online

(Note: you may have already done this when setting up your Inbound connector
for MailRoute - if so, you don't need to do it again. But we're putting this
here because it does end up affecting outbound mail relays, and it's
important.)

This will reduce false-positives on Microsoft's side and improve filtering
effectiveness. It also prevents people from bypassing MailRoute and sending
email directly to you without filtering.

Microsoft has an article explaining how it all works at
<https://learn.microsoft.com/en-us/exchange/mail-flow-best-practices/use-
connectors-to-configure-mail-flow/enhanced-filtering-for-connectors#what-
happens-when-you-enable-enhanced-filtering-for-connectors>

  * Jump right to the configuration page at <https://security.microsoft.com/skiplisting>
  * Click on your **MailRoute Inbound** connector  
  
![Image](17543583281683.png)

  * Choose **Skip these IP addresses**... **,** enter **199.89.0.0/21** into the text area, and then choose **Apply to the entire organization** , and click **Save:**  
  
![Image](17543583283091.png)  
  

And you're done!

