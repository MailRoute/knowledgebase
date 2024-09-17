---
created_at: 2018-11-23 21:56:46
date: 2024-04-23 16:14:47
description: Learn about MailRoute's advanced email filtering process, including adaptive
  blocklisting, content analysis, reputation monitoring, and URL scanning to protect
  against spam, malware, and phishing attacks.
draft: true
params:
  author: Unknown
summary: The article outlines MailRoute's multi-layered approach to email filtering,
  which includes adaptive blocklisting, content filtering, reputation monitoring,
  and URL checks. It also briefly mentions their Continuity service, which provides
  disaster recovery for email.
tags: null
title: 'The Filtering Process '
---


MailRoute uses a multi-layered approach to email filtering. Our process looks
like this:

**Adaptive Blocklisting**

This is our first layer of defense. Incoming connections are checked and
denial of service attacks are blocked. IP addresses that have very bad
reputations (all spam, no ham) are logged and dropped. We use roughly 40 RBL’s
(internal and those shared with other filtering companies, as well as some
from outside providers). Whatever is best of breed that day.

**Content Filtering**

Mail that’s passed the first layer enters our proprietary Content Filtering.
We take a message apart and look at the route it took to get to us (how many
hops around the internet), message header, MIME, content, attachments, URL’s,
etc. Attachments are parsed and recursively decoded, and all parts are run
through a minimum of two anti-virus engines.

This layer also happens in a few seconds or less.

Content-filtered mail is scored by our hundreds of thousands of rules. Mail
deemed clean (based on a score set by the customer) is delivered to the
customer’s server; mail deemed questionable (again, based on the filter
settings of the customer) will be quarantined.

Quarantined mail is held for 15 days and expires naturally. Customers receive
Quarantine Notifications alerting them to new mail in their quarantine. From
within this notification, customers can allow, block, recover to their
mailbox, or allow and recover, with a single click.

**Reputation Monitoring**

Our cutting-edge filtering service enhances your email security by conducting
thorough reputation checks on both senders and their IP addresses. This
process ensures that only trustworthy emails reach your inbox, effectively
safeguarding against spam and phishing attacks. By evaluating the credibility
of each sender and their corresponding IP, we provide an extra layer of
protection

**URL Checks**

We also examine every URL within every email. We cross-reference each link
against an extensive database of known malicious URLs to ensure your safety.
Additionally, for URLs leading to redirect domains (such as bit.ly, t.co and
hundreds of others), we don't just stop there. We diligently follow the trail
to inspect the final destination, ensuring it's free from any digital threats.
This thorough approach guarantees that every click within your emails is
secure, protecting you from the risks of phishing and malware.

* Additional protection *

MailRoute has created a secure, reliable disaster-recovery email solution
called Continuity, an add-on service to your filtering account. Continuity
makes your email available even when your mailserver is not. For further
details please see [here](https://support.mailroute.net/hc/en-
us/articles/225722708-Continuity-and-Archiving-Lite) or contact
support@mailroute.net.

