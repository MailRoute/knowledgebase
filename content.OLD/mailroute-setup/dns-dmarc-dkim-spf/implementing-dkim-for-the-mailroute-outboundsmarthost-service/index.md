---
created_at: 2017-06-19 19:27:55
date: 2024-02-20 20:41:34
description: Learn how to implement DKIM for the MailRoute Outbound/SmartHost Service
  to verify email authenticity and prevent spoofing. Step-by-step guide with DNS record
  configuration and additional DMARC/ADSP setup instructions.
draft: true
params:
  author: Unknown
summary: The article provides instructions on how to set up DKIM (DomainKeys Identified
  Mail) for the MailRoute Outbound/SmartHost Service, including the required DNS records
  and additional steps for setting up DMARC and ADSP to enhance email authentication
  and prevent spoofing.
tags: null
title: Implementing DKIM for the MailRoute Outbound/SmartHost Service
---


MailRoute requires the use of DKIM, a system designed to detect email
spoofing. DKIM verifies that an email sent from a domain is in fact sent by
the owner of that specific domain. The idea behind DKIM is to stop forged
sender addresses in emails - those emails we think of as phishing or spam.

### How it works:

Each email using DKIM contains a digital signature which verifies the signer's
public key published in the DNS. This valid digital signature assures that
some parts of the email have not been modified since the signature was
affixed.

### What you need to do:

If you're using MailRoute for outbound, set up the following DNS records for
each of your domains so that your email will pass DKIM checks:

**Hostname DNS Entry** | **Type** | **Value**  
---|---|---  
mr01._domainkey | CNAME | mr01.dkim.mailroute.net  
mr02._domainkey | CNAME | mr02.dkim.mailroute.net  
mr03._domainkey | CNAME | mr03.dkim.mailroute.net  
  
That's it! That's the most basic thing you need to do.

  
But while you're in there, why not set up DMARC and ADSP as well, and check
your SPF records?

You can read our [Knowledge Base article that covers DMARC and
ADSP](https://support.mailroute.net/hc/en-
us/articles/360062946093-Implementing-DMARC-for-the-MailRoute-Outbound-
SmartHost-Service), bu here's a brief primer on setting them up:

If all your email is DKIM signed, meaning it all goes through MailRoute, or
all your outbound servers and services are signing your email, set this record
too:

**DNS Entry** | **Type** | **Value**  
---|---|---  
_adsp._domainkey.<domain> | TXT | dkim=all  
  
If all your outbound mail goes through MailRoute, or if your other services
support DKIM and you have a proper SPF record, you can implement a simple
DMARC record like this:

**DNS Entry** | **Type** | **Value**  
---|---|---  
_dmarc.<domain> | TXT | v=DMARC1; p=reject;  
  
This is a very basic DMARC configuration. But DMARC has a lot of other
features as well. If you want to take advantage of the reporting and
management features of DMARC, we recommend that you check out a service like
dmarcian.com.

This combination of records gives your domain the best protection against
forgeries and spoofing of email that claims to come from your domain and
users.

### Do you use other services to send email that comes from your domain?

If you're using other services that may send email on your behalf, be sure to
check out their own DKIM implementations. Here is a list of some DKIM
supporting sites:

  * [Zendesk supports DKIM signing of outbound mail](https://support.zendesk.com/hc/en-us/articles/203663326-Digitally-signing-your-email-with-DKIM-or-DMARC)
  * [So does Office365](https://technet.microsoft.com/en-us/library/mt695945\(v=exchg.150\).aspx)
  * [Google Apps, Google Workspace, G Suite](https://support.google.com/a/answer/174124?hl=en)
  * [Salesforce](https://help.salesforce.com/articleView?id=000351388&language=en_US&mode=1&type=1)
  * [Dreamhost](https://help.dreamhost.com/hc/en-us/articles/215029758-What-are-DKIM-records-)
  * [Amazon Web Services](https://aws.amazon.com/blogs/aws/simple-email-service-easy-domainkeys-identified-mail-support/)
  * [SendGrid](https://sendgrid.com/docs/ui/account-and-settings/dkim-records/)
  * [Mailgun](https://www.mailgun.com/blog/understanding-dkim-how-it-works/)
  * [Host Gator](http://support.hostgator.com/articles/domainkeys-and-dkim)
  * [Mail Chimp](https://kb.mailchimp.com/accounts/email-authentication/set-up-custom-domain-authentication-dkim-and-spf)
  * [Constant Contact](https://knowledgebase.constantcontact.com/articles/KnowledgeBase/5932-self-publishing-for-authentication?lang=en_US)

## Related:

[Email Authentication - An Explanation and
Exploration](https://support.mailroute.net/hc/en-
us/articles/360061128614-Email-Authentication-An-Explanation-and-Exploration)

[Implementing SPF for the MailRoute Outbound/SmartHost
Service](https://support.mailroute.net/hc/en-us/articles/360021568194-Setting-
Your-SPF)

[Implementing DMARC for the MailRoute Outbound/SmartHost
Service](https://support.mailroute.net/hc/en-us/articles/360062946093)

