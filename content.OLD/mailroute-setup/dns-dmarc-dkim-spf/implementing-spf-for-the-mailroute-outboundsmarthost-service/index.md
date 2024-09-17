---
created_at: 2019-04-16 15:13:44
date: 2024-02-20 20:41:34
description: Implement SPF (Sender Policy Framework) for MailRoute Outbound/SmartHost
  Service. Detailed instructions on how to set up or modify SPF records to include
  spf.mailroute.net for email authentication.
draft: true
params:
  author: Unknown
summary: The article provides guidance on setting up an SPF record for domains using
  the MailRoute Outbound/SmartHost Service. It explains what an SPF record is, why
  it's important, and the specific syntax required to include MailRoute's SPF record
  in the domain's SPF record.
tags: null
title: Implementing SPF for the MailRoute Outbound/SmartHost Service
---


## Setting Your SPF Record

If you use the **MailRoute Outbound/SmartHost Service,** you need to be sure
you have an proper SPF record for your domains.

### What's an SPF record?

SPF defines a list of the servers, services, and IP addresses that are allowed
to be relaying or sending email from your domain. It's a DNS TXT record for
domain itself. If it's missing, many email providers will penalize or even
reject your email. Its presence helps them to know that an email is coming
from an approved source. Along with DKIM signing of messages, it's a key part
of DMARC authentication as well.

You can read all about SPF Records here:
<https://en.wikipedia.org/wiki/Sender_Policy_Framework>

So you need to have one, and it needs to be correct.

### Here's what we need you to do:

The SPF records for any **MailRoute Outbound/SmartHost Service** customer must
include the following in their SPF record:

    
    
     include:spf.mailroute.net

### But I don't have an SPF record!

Then add one! If MailRoute is the sole outbound relay for your email, your SPF
record can be as simple as

    
    
    v=spf1 include:spf.mailroute.net -all

### I have an SPF record. What do I need to change?

Simply add "include:spf.mailroute.net" to your SPF record.

If your record looks like this:

    
    
        "v=spf1 ip4: **192.168.0/27** -all"  ** <** **this IP range is ONLY an example**

Add our spf record to it so that it looks like this:

    
    
        "v=spf1 ip4:192.168.0/27 include:spf.mailroute.net -all"

That's all there is to it!

### How do I add or change my SPF record?

Well, that all depends on your DNS host - what you need to do is "add a TXT
record to the domain's primary record". In some systems, it might look
something like this, using "domain.com" as an example:

    
    
    domain.com  IN TXT "v=spf1 include:spf.mailroute.net ~all"

In some systems, "@" is used as a shortcut for domain name:

    
    
    @  IN TXT "v=spf1 include:spf.mailroute.net ~all"

Every DNS provider has a different interface for their DNS. If you need
assistance with yours, please feel free to reach out to us via an email to
[MailRoute Support](mailto:support@mailroute.net)

## Related:

[Email Authentication - An Explanation and
Exploration](https://support.mailroute.net/hc/en-
us/articles/360061128614-Email-Authentication-An-Explanation-and-Exploration)

[Implementing DKIM for the MailRoute Outbound/SmartHost
Service](https://support.mailroute.net/hc/en-
us/articles/115009100687-Implementing-DKIM)

[ Implementing DMARC for the MailRoute Outbound SmartHost
Service](https://support.mailroute.net/hc/en-
us/articles/360062946093-Implementing-DMARC-for-the-MailRoute-Outbound-
SmartHost-Service)

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

