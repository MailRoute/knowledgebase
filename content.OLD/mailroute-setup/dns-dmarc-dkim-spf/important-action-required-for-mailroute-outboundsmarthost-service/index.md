---
created_at: 2021-02-10 01:17:04
date: 2022-03-26 01:46:07
description: Important notice requiring MailRoute users to add specific DNS records
  for DKIM signing of outbound emails to combat phishing and improve email deliverability.
  Also promotes MailRoute's outbound/SmartHost service.
draft: true
params:
  author: Unknown
summary: The article informs users about the need to add specific DNS records for
  each domain that sends email through MailRoute's outbound/SmartHost service to enable
  DKIM signing of outbound emails. It also encourages users to utilize MailRoute's
  outbound/SmartHost service and provides relevant knowledge base articles for further
  information.
tags: null
title: Important Action Required for MailRoute Outbound/SmartHost Service
---


I'm sure you've all noticed that there's been a tremendous increase in
phishing, spoofing, and forgeries. To help combat this issue, MailRoute is now
DKIM signing all outbound email for our users. But we need you to do something
to make it all work.

**Here's what you must do:**

Don't worry, it's simple. Just add three records to the DNS for each domain
that sends mail out through MailRoute:

mr01._domainkey.<domain>. CNAME
[mr01.dkim.mailroute.net](http://mr01.dkim.mailroute.net/).

mr02._domainkey.<domain>. CNAME
[mr02.dkim.mailroute.net](http://mr02.dkim.mailroute.net/).

mr03._domainkey.<domain>. CNAME
[mr03.dkim.mailroute.net](http://mr03.dkim.mailroute.net/).

That's it! Just substitute your own domain name where it says "<domain>" of
course. Once those records are in place, recipients can validate the email
that you're relaying through MailRoute, which will increase your
deliverability, and generally make the world a better place.

For GoDaddy DNS instructions please see
[here](https://support.mailroute.net/hc/en-us/articles/360061270214)

**What if you already have MailRoute DKIM DNS records?**

If you already have other DKIM records from us, those will continue to be
supported at least through the end of 2021. But we urge you to add these
records as well, so that the transition to the new signing system will be
transparent to you, and we can start using our advanced automated DKIM key
management systems to your full benefit.

**What? You say you don't use MailRoute for Outbound/SmartHost relay?**

What??!? Why aren't you? The service is included with your inbound filtering
service, and using our Outbound/SmartHost relay service will not only increase
the deliverability of your email, but it helps us better filter your inbound
mail, and reduce any potential false positives. We can use info about who you
correspond with to adjust the scores of messages from those people. It's sort
of like a "soft allow-list" that we can dynamically adjust to give you the
lowest false-positive rates and best email filtering possible.

All you need to do is add your servers to the "Outbound Servers" tab in our
Control Panel at [http://admin.mailroute.net](http://admin.mailroute.net/).
And then set your mailserver up to relay outbound mail through MailRoute. We
have a whole set of articles about this on our KB at
<https://support.mailroute.net/hc/en-us/sections/205311868-Configuring-
Outbound-Service>

**Want more information?**

Here's our KB article about properly setting up your DKIM records that gives
more detail on setting this up, if you need it:

**Implementing DKIM:** <https://support.mailroute.net/hc/en-
us/articles/115009100687-Implementing-DKIM-for-the-MailRoute-Outbound-
SmartHost-Service>

We've got new articles on our KB about this stuff, about email Authentication
in general, DMARC, and SPF. Check them out:

**Email Authentication:** <https://support.mailroute.net/hc/en-
us/articles/360061128614-Email-Authentication-An-Explanation-and-Exploration>

**Implementing SPF: **<https://support.mailroute.net/hc/en-
us/articles/360021568194-Implementing-SPF-for-the-MailRoute-Outbound-
SmartHost-Service>

**Implementing DMARC:** <https://support.mailroute.net/hc/en-
us/articles/360062946093-Implementing-DMARC-for-the-MailRoute-Outbound-
SmartHost-Service>

Thank you for using MailRoute!

