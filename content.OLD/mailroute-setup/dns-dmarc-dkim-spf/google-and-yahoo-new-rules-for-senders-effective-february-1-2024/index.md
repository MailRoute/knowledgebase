---
created_at: 2024-02-19 20:32:37
date: 2024-02-20 17:57:29
description: Important alert on new rules by Google and Yahoo for senders from Feb
  1, 2024, requiring SPF, DKIM, and DMARC configuration to prevent emails going to
  spam or getting rejected. Provides guidance on implementing these through MailRoute's
  outbound relay service.
draft: true
params:
  author: Unknown
summary: The article alerts customers about new email authentication requirements
  set by Google and Yahoo, effective February 1, 2024, to combat spam and spoofing.
  It recommends configuring SPF, DKIM, and DMARC records through MailRoute's outbound
  relay service to ensure email deliverability.
tags: null
title: Google and Yahoo New Rules for Senders, Effective February 1, 2024
---


## Important Alert

Google and Yahoo New Rules for Senders, Effective February 1, 2024

**What's Changed**

New rules have been implemented by Google and Yahoo to protect against spam,
phishing, and spoofing for senders to these addresses. This may affect you, if
you are sending to users of those email services.

**How can I prevent this problem?**

To ensure that your emails make it to your intended recipients for these
companies (and most companies), you should do the following:

  * SPF and DKIM need to be configured. Ensure your domain is properly authenticated.
  * We highly recommend implementing a DMARC policy, even if set to "none”

**What will happen to my mail if I don't meet the requirements?**  
If you do not meet the sending criteria, your emails may be sent to the spam
folder or rejected.  
If mail is rejected, we will return a specific error code with information
about the rejection.

**What exactly do I need to do?**

  1. Make sure you're using the MailRoute Outbound Relay Service.   
  
Here are some articles on how to configure your mail server to relay email out
through MailRoute:  
  
[Configuring Outbound Services on
MailRoute](https://support.mailroute.net/hc/en-
us/sections/205311868-Configuring-Outbound-Email-Services)  
  

  2. Configure your SPF, DKIM, and DMARC records.   
  
Here are some articles on configuring these for your domain:  
  
[Implementing SPF for the MailRoute Outbound/SmartHost
Service](https://support.mailroute.net/hc/en-us/articles/360021568194)  
  
[Implementing DKIM for the MailRoute Outbound/SmartHost
Service](https://support.mailroute.net/hc/en-us/articles/115009100687)  
  
[Implementing DMARC for the MailRoute Outbound/SmartHost
Service](https://support.mailroute.net/hc/en-us/articles/360062946093)  
  
  

  3. Verify your configuration.   
  
After you make the changes to your DNS for SPF, DKIM, and DMARC, you can visit
the Diagnostics menu for your domain in the MailRoute Control Panel. Login to
the Control Panel with your admin account, select your domain, and click
**Diagnostics** on the menu on the left.  
  
You can also send an email to
[check@mailroute.net](mailto:check@mailroute.net) and we will send an email
back to you with a review of those settings.  
  
(Note: DNS changes can take some time to propagate)

**For more details:**

To view Google and Yahoo's documentation of the new rules, please see here:

  * <https://support.google.com/a/answer/174124?hl=en>
  * <https://senders.yahooinc.com/faqs/>

