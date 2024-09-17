---
created_at: 2021-02-09 23:07:18
date: 2024-04-11 23:22:03
description: Learn how to implement DMARC for the MailRoute Outbound/SmartHost Service
  to help prevent email forgeries and spoofing. Get step-by-step instructions for
  creating the necessary DNS TXT record and understanding DMARC's role in email authentication.
draft: true
params:
  author: Unknown
summary: The article explains what DMARC is and how to implement it for the MailRoute
  Outbound/SmartHost Service by creating a DNS TXT record. It also discusses the importance
  of setting up SPF and DKIM first, and mentions ADSP as an additional security measure.
tags: null
title: Implementing DMARC for the MailRoute Outbound/SmartHost Service
---


### What is DMARC?

DMARC is an email authentication protocol used to help prevent forgeries and
spoofing. DMARC extends two other email authentication protocols, DKIM and
SPF, and allows an administrator to specify which of those protocols is used
for a given domain, allow spoofed, forged, and unauthorized emails to be
blocked or quarantined.

You can read all about DMARC here in this [Wikipedia
Article](https://en.wikipedia.org/wiki/DMARC).

### Another one? Aren't SPF and DKIM enough?

I'm afraid that they are not. They help with making sure emails aren't
modified in transit and that they come from servers with permission to send
for a domain, but neither of them is able to specify that those particular
types of authentication are **required**. So if one or both are missing, then
the receiving email filters cannot tell if that's on purpose or if it's
because of a forgery.

DMARC looks at the results of the SPF and DKIM checks.

DMARC validation succeeds when either SPF passes and the SMTP Envelope sender
aligns with the 'From:' header domain, or DKIM passes and the signing domain
matches the 'From:' header domain

### First, be sure you've set up SPF and DKIM!

[Implementing SPF for the MailRoute Outbound/SmartHost
Service](https://support.mailroute.net/hc/en-us/articles/360021568194-Setting-
Your-SPF)

[Implementing DKIM for the MailRoute Outbound/SmartHost
Service](https://support.mailroute.net/hc/en-
us/articles/115009100687-Implementing-DKIM-for-the-MailRoute-Outbound-
SmartHost-Service)

### Done doing SPF and DKIM? Here's what you need to do - another DNS record:

A DMARC record is a TXT record - just like DKIM and SPF use.

A very simple DMARC record might look as simple as this:

    
    
    _dmarc.<domain>  TXT   v=DMARC1; p=reject;

There's a lot more you can do with DMARC, if you want. The **p** (policy)
could be "quarantine" or "reject" or "none". You can apply the DMARC
restrictions to a percentage of your mail, with something like "pct=50" You
can have reports sent to a reporting address ("ruf=mailto:user@domain.com").

If you'd like pretty reports of failures and the like, you can use a service
like [Dmarcian](http://dmarcian.com). It's mostly used by large outbound
senders, and those with security needs, like banks and financial institutions.

## And while you're at it, why not set up an ADSP record too?

Since DMARC doesn't have any feature that specifies that every single message
from a particular domain MUST be signed with DKIM, MailRoute still supports
the older ADSP standard as well.

ADSP is very simple. You simply specify if your domain DKIM signs EVERY SINGLE
MESSAGE:

    
    
    _adsp._domainkey.domain.com. IN TXT "dkim=all"
    

You have to be sure that everyone who sends email on behalf of your domain is
doing DKIM signing. If all your mail goes through MailRoute, you're safe
there, as long as you've set up your DNS records for DKIM, of course.

If you have a record like this, then MailRoute can discard all mail for your
domain that claims to come from your domain, but which isn't properly signed
by your domain. So you can avoid all those forgeries and phishing attacks that
try to make you think the email is coming from inside the house.

So give it a try - it won't do much for your outbound mail, but it helps clean
up your inbound mail, and that's always a good thing.

## Related:

[Email Authentication - An Explanation and
Exploration](https://support.mailroute.net/hc/en-
us/articles/360061128614-Email-Authentication-An-Explanation-and-Exploration)

[Implementing SPF for the MailRoute Outbound/SmartHost
Service](https://support.mailroute.net/hc/en-us/articles/360021568194-Setting-
Your-SPF)

[ Implementing DKIM for the MailRoute Outbound/SmartHost
Service](https://support.mailroute.net/hc/en-
us/articles/115009100687-Implementing-DKIM-for-the-MailRoute-Outbound-
SmartHost-Service)

