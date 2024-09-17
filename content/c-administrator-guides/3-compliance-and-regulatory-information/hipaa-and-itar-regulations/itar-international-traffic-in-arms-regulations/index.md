---
created_at: 2013-12-26 18:17:45
date: 2022-09-06 15:11:00
description: MailRoute provides email services that meet ITAR compliance requirements,
  ensuring data is handled and stored only by U.S. persons within the United States.
  FAQs cover email storage, access, and data handling practices.
draft: true
params:
  author: Unknown
summary: This article discusses MailRoute's compliance with the International Traffic
  in Arms Regulations (ITAR) and answers frequently asked questions from ITAR-compliant
  companies regarding email storage, access, and data handling practices.
tags: null
title: ITAR (International Traffic in Arms Regulations)
---


For information on ITAR Compliance, visit
[http://www.pmddtc.state.gov/regulations_laws/itar.html](https://www.pmddtc.state.gov/ddtc_public?id=ddtc_public_portal_itar_landing)

Due to rapid changes with government policies, additional documentation can be
found at [www.ecfr.gov](http://www.ecfr.gov/cgi-bin/ECFR?page=browse)

MailRoute’s wholly owned subsidiary MR Compliance Solutions deals specifically
in this area of customer compliance with regulatory bodies. For more
information, please contact
[marketing@mailroute.net](mailto:marketing@mailroute.net). MailRoute is
providing this information without opinion and notes that users must ensure
their own compliance.

MR Compliance Solutions has many customers who require ITAR compliance and use
MailRoute to assist with that need.

MailRoute meets the specifications set out by those who are required to meet
ITAR compliance. We are not required to register with the DDTC (Directorate of
Defense Trade Controls), the body that oversees ITAR compliance, since we are
not a manufacturer, broker, or freight-forwarder.

MailRoute service is an excellent way to isolate your mail servers from the
rest of the world. Once you're up and running with us, you can restrict your
servers to accept connections exclusively from our block of IP addresses, so
that nobody but MailRoute can connect to your servers.

MailRoute Compliance Solutions' services provided shall be performed only by
U.S. Person employees, as defined in the International Traffic in Arms
Regulations (22 CFR 120), Section 120.15, of MailRoute. Additionally, all
services, including accessing and storing services, will be within the United
States.

## **Frequently Asked Questions from ITAR-compliant Companies**

###  **When email is delivered to our hosts through your mail hops are any
copies of said communications retained on any of your servers for any
reason?**

MailRoute categorizes each message that comes in for our customers: clean,
spam, virus-infected, messages with bad headers in violation of the email
standards, or emails containing banned file types.

Clean messages are immediately relayed to your servers. The other categories
may be immediately delivered, with optional subject-line or header
modifications, or they may be quarantined. This is an option you may select
domain-wide, or each mailbox may have a different setting, if you so wish.
It's completely configurable.

When the message first arrives at one of our datacenters, it is queued on
disk, and held there until successful delivery, or optional quarantine is
complete. It is then erased.

If the message is to be quarantined, it may sit on our servers for
approximately 2-3 weeks so that you have the option to review them if you so
choose. At the end of that period, it expires and is automatically deleted.

If your email server is down, we will queue the email on our servers until
your server is back in operation, at which time the email will be relayed to
your server, and then removed from ours.

### **Where are the servers that said information is stored?**

All of MailRoute’s datacenters are currently in the United States: Los
Angeles, CA; Reston, VA, and Chicago, IL.

### **Do any non-US citizens have access to said information?**

No. All full-time employees and contractors who have access to any server in
production (any machine handling any customer data) are US citizens. Our
support staff are all in the US and are US citizens - they may access delivery
details, logging information, or customer settings, but have no access to
email content. Physical and root access to the servers is very tightly
controlled, and provided to just a handful of people - primarily myself, as
CEO and chief architect, and two other system administrators, with whom I have
worked for many years.

We do have contractors who handle some front-end web programming for our
control panel. They do not have any access to the servers that process email.
They write the code for our interface, which is reviewed by our internal
developers, and tested internally before deployment. Their code does not
modify, nor does it interface with clean or delivered email in any way. The
only access their code has to any email content at all is for email that is
quarantined, to allow a user to view said quarantined email via a web-based
interface. At some point, we may offer logging and reporting data through this
interface, but we do not do that at this time. Once again, these contractors
have no access to any of our production servers. They work on their own
development environment, submit their code for review, and after approval, our
US personnel deploy it on our production servers.

### **Do any of our forwarded emails pass through servers that are not in the
US?**

No. All incoming email will come to one of our US datacenters. Of course, if
the sender is from outside the US, it will, naturally, come from its point of
origin; but once it hits us, it stays entirely in the US. When we deliver the
email, we will relay it directly to your mail servers.

### **When our email is queued for later delivery if/when our email server is
unreachable are these queued messages stored outside of the US?**

No. We do anticipate opening up one or more international datacenters in the
next year or so. But our architecture allows us to specify which datacenters
will handle email for particular customers. Customers will be able to opt to
balance their traffic globally across all datacenters (preferentially
utilizing the datacenter closest to them, or closest to the email sender), or
they will be able to limit it to specific national regions. You would be able
to have all mail processed within the US, for example, and our EU customers
could opt to have all mail processed by the servers there.

Our customers currently change the MX records to "mail.mailroute.net". This
balances email processing across all our datacenters (which are all currently
in the US), based on geographical location, datacenter performance and health,
etc. When we do open non-US datacenters, customers will be able to opt to use
that global MX record, a US-only one (e.g., "mail-us(dot)mailroute(dot)net"),
or MX records for specific regions ("mail-eu(dot)mailroute(dot)net" or "mail-
asia(dot)mailroute(dot)net" and so on).

Even when we have these non-us datacenters, we will restrict access to the US
datacenters and servers to US citizens.

### **How does MailRoute store metadata or basic delivery information?**

We store basic delivery information for email that passes through us: the
equivalent of the outside of an envelope, along with information about the
classification and eventual delivery of the message. This is currently stored
indefinitely. Customers may have the option for this to be stored for a more
limited time, with only aggregated data stored long-term (for trend analysis,
etc.).

The type of information stored looks like this:

2013-12-20T06:38:53+0000 gw01.lax01(dot)mailroute(dot)net Q S
postmaster(dot)itei.cn tj(at)terramar(dot)net ""
<2f09adc3-1017-46d7-b611-3ef7ecaf4b38@dcmx(dot)instrnet(dot)com> 559.257 1702
3dm0fL3ggqz21rD

Breaking it down, that is the:

Date/Timestamp in GMT

The server that handled this email

Classification:

Q = Quarantine

D = Delivered

Classification:

C = Clean

S = Spam

V = Virus

H = bad Header

F = banned File

Sender

Recipient

Data about message (i.e., virus name, name of banned file, etc.)

Message-ID

SpamScore

Message size in bytes

Message Queue-id so that we can locate mail server relay info (which is only
kept for 7 days).

For shorter-term quarantine and diagnostic purposes, we also store the IP
address of the sending server as well as the subject of the message. These are
removed after 2-3 weeks, but we may offer an option to store that longer for
customers at some point in the future.

[**More FAQ's**](https://support.mailroute.net/entries/98533857-ITAR-
Compliance-FAQ-s)

MailRoute’s wholly owned subsidiary MailRoute Compliance Solutions deals
specifically in this area of customer compliance with regulatory bodies. For
more information, please contact
[marketing@mailroute.net](mailto:marketing@mailroute.net).

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

