---
created_at: 2023-06-16 12:07:10
date: 2023-06-16 12:34:09
description: A detailed comparison between MailRoute and Barracuda email security
  services, covering security, reputation systems, data loss prevention, filtering
  philosophies, user configurability, and API integration, with a clear emphasis on
  MailRoute's superiority.
draft: true
params:
  author: Unknown
summary: This article compares the email security services of MailRoute and Barracuda.
  It discusses their differences in security features, reputation systems, data loss
  prevention, filtering methods, user configurability, and API support, highlighting
  MailRoute's advantages over Barracuda.
tags: null
title: MailRoute vs Barracuda
---


MailRoute vs. Barracuda

By Security Expert Boris Lukashev and MailRoute Founder Thomas A. Johnson

Created August 8, 2013 to address Barracuda's known security hole in their
appliance, which was exploited in June 2023 by hackers

Barracuda’s hosted protection and hardware are both subject to the myriad
security issues that have plagued Barracuda to date (the main issue being that
there is insecure, backdoor access into their hardware, and they cannot or
will not remove it.)

Not only are they opting out of the Compliance/DIB market, but their hosted
service by industry standards is not a complete service. It is missing major
features users need (your ability to limit emails for a specific subsets of
users), and it is crippled in areas like configurability, particularly at the
end-user level (you can't change filter settings for different users with
their service, which is critical).

1\. Security. Both MailRoute and Barracuda offer TLS encryption. Barracuda
does have a feature where you can force people to login to a Barracuda mailbox
to view a "secure" email. We don't offer that, because, frankly, we think it's
an annoying thing to make people do, and there's no actual guarantees of
security. MailRoute offers DKIM signatures for outbound mail -- something they
do not seem to support at all.

2\. Reputation. Barracuda uses their own reputation service. We use multiple
third-party reputation services, and our own as well. We do reputation checks
for IP addresses, mail servers, senders, URLs, relay hosts and other aspects
of the service, not just URLs in messages.

We also check the destinations that various URLs point to, and use that
information to determine if a URL in a message is a dangerous one.

3\. DLP. This is another service that we think is more problematic than
effective. Basically, Barracuda can block emails that contain social security
numbers, credit card numbers, phone numbers, etc. Here's the problem with it:
it's prone to false positives, and trivial to bypass. At best it offers a
false sense of security. Here's something from their own documentation:

◦ Credit Cards - Messages sent through the Barracuda Email Security Service
containing recognizable

Master Card, Visa, American Express, Diners Club or Discover card numbers will
be subject to the

action you choose.

◦ Social Security - Messages sent with valid social security numbers will be
subject to the action you

choose. U.S. Social Security Numbers (SSN) must be entered in the format nnn-
nn-nnnn.

◦ Privacy - Messages will be subject to the action you choose if they contain
two or more of the following data types, using common U.S. data patterns only:
credit cards (including Japanese Credit Bureau), expiration date, date of
birth, Social Security number, driver's license number, or phone number. Phone
numbers must be entered in the format nnn-nnn-nnnn or (nnn)nnn-nnnn or
nnn.nnn.nnnn .

◦ HIPAA - Messages will be subject to the action you choose if they contain
TWO of the types of items as described in Privacy above and ONE medical term.

Note that Social Security numbers have to be formatted as nnn-nn-nnnn. If you
send one through like this: 123-123-123, it will go through, because it's
formatted just a little bit differently. Same thing with phone numbers or
credit card numbers.

Items for consideration:

1\. RBLs:

They use the Barracuda RBL. If an IP address is on that list, it is blocked
outright. We looked at using this one, but decided not too -- because we don't
believe in blacklists that charge you for removal:

http://joystickjunkie.blogspot.com/2010/04/emailregorg-is-scam.html

They allow you to add your own RBLs, but you're responsible for them. You have
to keep them up to date, know the reputations and accuracy of each, etc., but
they will block a message if it's listed in an RBL you specify.

We use 39 different RBLs. Very few are used for outright blocking - instead,
we use them to add to the overall spamscore of a message. This reduces false
positives and allows us to use the presence of an address on a particular
blacklist in combination with other rules to give us much more accurate
filtering. We manage these all actively, and we go in and selectively override
RBLs or even individual entries as necessary if we perceive an inaccuracy in a
third-party RBL.

2\. Filtering philosophy:

They have different methods, which are rather binary - something is spam, or
it is not. If a message fails any of those, a message is blocked. RBL,
Reputation, Content - each just blocks the message. You can enable or disable
each, but that's it.

We believe that no filtering method is perfect, and certainly few are worthy
enough to be used to determine if a message is spam or clean by itself. We use
all the kinds of technologies they use, but we integrate them into a complete
system.

Each component not only contributes to the overall score of a message, a part
of one component can be tied to another unrelated one, if we find that it
statistically increases the chance of recognizing that something is clean or
something is spam. For example, a listing of an IP address in a range of
dynamic IP addresses is not enough to block a message, but it will contribute
to an overall score. But if we find that the IP address is in a dynamic
address range, and we see that the date formatting of the message is off, or
that the sending mailserver is a windows XP machine, then that combination of
three things adds another larger score to the overall message, because it's a
pattern we've discerned by analyzing billions of email messages.

3\. User configurability

User settings on the Barracuda ESS are limited to enabling disable quarantine
notifications, and black/whitelists.

Messages may be passed along or quarantined.

Our system is completely configurable for each and every end user. Individual
filters can be enabled or disabled, spam quarantine cutoffs can be adjusted,
etc. We give the end-user account settings as much control as the default
account settings.

We allow messages to be quarantined, or delivered with subject lines
rewritten, delivered with a "plus address extension" (if you want spam
delivered to user+spam@domain.com, you can do that), and we allow the
recipient to optionally receive notifications when particular types of
messages are blocked and/or quarantined.

4\. Integrated Sender and Recipient Filtering

We're able to use the information in your outbound mail to improve the
accuracy of your inbound filtering, for reduced false positives.

5\. API

They don't have one. We do. Ours can control every aspect of our service. It's
how we implemented your custom feature - the one that allows a subset of your
users to only receive email from specific senders.

By the way - here's something I, Thomas Johnson, sent a colleague about
emailreg.org a while back:

EmailReg.org – another of those paid whitelist companies – is actually
Barracuda. They charge you to get on their whitelist! We will not use their
blacklists if this is their policy; we don't use any blacklist that charges
for removal, or whitelist that charges for being listed. That's not how we do
business.

How do I know it's Barracuda?

new-host:~ tj$ dig +short a emailreg.org

64.235.146.64

new-host:~ tj$ whois 64.235.146.64

#

# ARIN WHOIS data and services are subject to the Terms of Use

# available at: https://www.arin.net/whois_tou.html

#

#

# Query terms are ambiguous. The query is assumed to be:

# "n 64.235.146.64"

#

# Use "?" to get help.

#

#

# The following results may also be obtained via:

#
http://whois.arin.net/rest/nets;q=64.235.146.64?showDetails=true&showARIN=false&ext=netref2

#

NetRange: 64.235.144.0 - 64.235.159.255

CIDR: 64.235.144.0/20

OriginAS: AS15324

NetName: BARRAUCDA

NetHandle: NET-64-235-144-0-1

Parent: NET-64-0-0-0-0

NetType: Direct Assignment

Comment: http://www.barracuda.com/

RegDate: 2006-10-31

Updated: 2012-02-24

Ref: http://whois.arin.net/rest/net/NET-64-235-144-0-1

OrgName: Barracuda Networks, Inc.

OrgId: BARRA-7

Address: 3175 S. Winchester Blvd

City: Campbell

StateProv: CA

PostalCode: 95008

Country: US

RegDate: 2005-08-29

Updated: 2011-09-24

Ref: http://whois.arin.net/rest/org/BARRA-7

OrgAbuseHandle: BARRA1-ARIN

OrgAbuseName: Barracuda Hostmaster

OrgAbusePhone: +1-408-342-5405

OrgAbuseEmail: [hostmaster@barracuda.com](mailto:hostmaster@barracuda.com)

OrgAbuseRef: http://whois.arin.net/rest/poc/BARRA1-ARIN

OrgTechHandle: BARRA1-ARIN

OrgTechName: Barracuda Hostmaster

OrgTechPhone: +1-408-342-5405

OrgTechEmail: hostmaster@barracuda.com

OrgTechRef: http://whois.arin.net/rest/poc/BARRA1-ARIN

RTechHandle: BARRA1-ARIN

RTechName: Barracuda Hostmaster

RTechPhone: +1-408-342-5405

RTechEmail: hostmaster@barracuda.com

RTechRef: http://whois.arin.net/rest/poc/BARRA1-ARIN

RAbuseHandle: BARRA1-ARIN

RAbuseName: Barracuda Hostmaster

RAbusePhone: +1-408-342-5405

RAbuseEmail: hostmaster@barracuda.com

RAbuseRef: http://whois.arin.net/rest/poc/BARRA1-ARIN

RNOCHandle: BARRA1-ARIN

RNOCName: Barracuda Hostmaster

RNOCPhone: +1-408-342-5405

RNOCEmail: hostmaster@barracuda.com

RNOCRef: http://whois.arin.net/rest/poc/BARRA1-ARIN

