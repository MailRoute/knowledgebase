---
created_at: 2021-02-05 15:49:33
date: 2021-02-10 00:44:40
description: An informative article about UCEProtect, a controversial DNS blacklisting
  service notorious for aggressively blocking IP subnets without proper justification
  or communication, charging high fees for delisting, and posing challenges for email
  senders.
draft: true
params:
  author: Unknown
summary: The article discusses UCEProtect, a DNS blacklisting service known for its
  aggressive listing policies and blocking of entire IP subnets, often without justification.
  It advises against using UCEProtect due to its questionable practices and lack of
  transparency.
tags: null
title: UCEProtect Blacklists
---


At some point you may have received an error message that an email has been
blocked from going to recipient with the following message:

554 5.7.1 Service unavailable; Client host [199.89.1.15] blocked using
dnsbl-1.uceprotect.net

Who They Are

UCEProtect is a DNS blacklisting service that is made up of three distinct
levels (1, 2 and 3). They have aggressive listing policies and can frequently
blocks entire subnets or any associated IPs.

Issues Arising from UCE Protect

\- do not publish why IPs are on their blacklist.

\- do not reply or communicate.

\- they have listed thousands of our IPs on their blacklist that have never
relayed mail.

\- charge a large fee to remove IPs from their blacklist.

\- it can take up to 30 days for the blacklisting to drop off if you don't pay

\- they like to block entire subnets of IPs and have been known to block most
of Amazon, ISPs, telecoms providers and governments.

What to Do

MailRoute does not condone the pay-to-delist model blacklists. This is not a
well respected practice in the email industry.

We can't control what other people use but we recommend that if you have
someone in regular contact who is affected by this blacklist we ask that you
reach out and ask them to not sure UCEProtect.

For More Information

<http://www.uceprotect.net/>

Other Sources Regarding UCE

<https://success.trendmicro.com/solution/000236583-Emails-being-rejected-by-
RBL-UCEPROTECL-in-Hosted-Email-Security-and-Email-Security>

<https://community.spiceworks.com/topic/2170592-uceprotect-blacklist-scam>

