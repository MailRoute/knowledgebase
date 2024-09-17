---
created_at: 2023-08-07 18:57:45
date: 2023-08-07 19:01:02
description: Learn how to properly configure Amazon WorkMail for MailRoute's Inbound
  Filtering Service by disabling additional DMARC checks and allowing only approved
  IP addresses.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring Amazon WorkMail
  to work with MailRoute's Inbound Filtering Service by disabling additional DMARC
  checks and locking down the server to allow only MailRoute's IP addresses for inbound
  email.
tags: null
title: Configuring Amazon WorkMail for Inbound Services
---


To configure Amazon WorkMail for the MailRoute Inbound Filtering Service,
there are two things you need to do - prevent WorkMail from blocking mail that
violates their own DMARC checks, and allowing all mail traffic from MailRoute
while blocking email that comes from other servers (ie "locking down your
server").

These are the steps from this Amazon article:

### <https://aws.amazon.com/blogs/security/how-to-configure-an-incoming-email-
security-gateway-with-amazon-workmail/>

###

Disabling Additional WorkMail DMARC Checks:

From the [WorkMail console](https://console.aws.amazon.com/workmail/v2/home),
select your organization, navigate to Organization settings, and select
Advanced. Edit the Inbound DMARC Settings and set Enforcement enabled to Off.
This ensures that WorkMail does not re-evaluate DMARC.

![Figure 3. Picture of the AWS WorkMail console showing the advanced
configuration depicting Inbound DMARC enforcement
disabled.jpeg](19313295415699.jpeg)

Locking Down Your Server:

1\. From the [Amazon SES console](https://console.aws.amazon.com/sesv2/home),
navigate to Email receiving and [create IP address
filters](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/receiving-
email-ip-filters.html) to allow the IP address or IP address range of the
gateway(s).

![PastedGraphic-4.png](19313273618451.png)

2\. Add another rule to block 0.0.0.0/0. This prevents malicious actors from
bypassing your email security gateway

![PastedGraphic-5.png](19313322458003.png)

This should do it! Now Amazon WorkMail will not perform additional DMARC
checks on incoming email, and it will allow mail to come in from MailRoute and
block other servers trying to send email directly to your WorkMail servers.

