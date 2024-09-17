---
created_at: 2018-07-02 17:34:55
date: 2024-02-20 20:41:34
description: Detailed guide on how to set up a new send connector in Microsoft Exchange
  2016 to route outbound emails through MailRoute's Smart Host service, with troubleshooting
  tips for common issues.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring the outbound
  email settings in Microsoft Exchange 2016 to route emails through the MailRoute
  Smart Host. It also includes basic troubleshooting tips related to SMTP connectors
  in Exchange.
tags: null
title: Microsoft Exchange 2016 Outbound Configuration
---


1\. Go to the Exchange Administration Center. Login as an Administrator.

2\. In the left-hand column select 'Mail Flow' and go to the 'Send Connectors'
tab.

3\. Enter a name for reference for the connection. This is entirely up to you
but something like MailRoute Outbound would be applicable.

4\. Under 'Type' select Partner

5\. In the New Send Connector section, select 'Route mail through smart hosts'
and then click Add.

6\. Enter the SMTP hostname in the Add Smart host page. Add
outbound.mailroute.net and click Save.

7\. You will now see the smart host listed. Click Next.

8\. You will see 'A send connector can route mail directly through DNS or
redirect it to a smart host'. Select 'Route mail through smart hosts'. Click
Next.

9\. Under Configure Smart host Authentication, select 'None' and then select
Next.

10\. Click 'Add' to add a new send connector that routes mail to a specified
list of domains. Click Next.

11\. Set the type to 'SMTP'

Add an asterisk (*) for Full Qualified Domain Name (FQDN)

*Cost - enter the number 1

Click Save

12\. Click Add to enter a list of permitted source servers

13\. Select the appropriate server (s) from the list provided and click add
for each. Click OK

14\. Click Finish to save the connector.

You will now see the SMTP connector has been created

You may need to restart the Exchange SMTP / Transport services for the changes
to take effect

The basic setup is now complete and you should be able to send emails from
your Exchange server / network

You may wish to change the SMTP port on which you connect to our service.
????????????

##

## Troubleshooting

  * The easiest method of troubleshooting issues with SMTP connectors in Microsoft Exchange is to enable protocol logging

  * The common errors that can happen when trying to configure our service will be logged to your account history in the Control panel -> Account Usage -> Error Log with the exception of incorrect username / password errors, so if you are having a problem please check those error logs.

  * If you have questions specifically about configuring or troubleshooting Exchange 2016 please use the [Official Microsoft Exchange 2016 Documentation](https://technet.microsoft.com/en-us/library/mt170645\(v=exchg.160\).aspx)\- due to the complexities of Microsoft Exchange we can only provide basic troubleshooting advice.

