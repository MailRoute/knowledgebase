---
created_at: 2015-12-21 16:19:49
date: 2019-03-26 18:10:37
description: Detailed FAQ regarding MailRoute's ITAR compliance email security services,
  addressing data storage, encryption, redundancy, quality control processes and more.
draft: true
params:
  author: Unknown
summary: This article provides frequently asked questions and answers related to MailRoute's
  ITAR compliance services, covering topics like data security, logging, encryption,
  redundancy, and email handling.
tags: null
title: ITAR Compliance FAQ's
---


MR Compliance Solutions is a separate legal entity from MailRoute, Inc. that
holds all ITAR and HIPAA contracts. Using MailRoute's email protection service
assists you in meeting the specifications required for full ITAR compliance.
Since we are not a manufacturer, broker, or freight-forwarder, we are not
required to register with the DDTC (Directorate of Defense Trade Controls),
the body that oversees ITAR compliance.

MailRoute's service is an excellent method for isolating your mail servers
from the rest of the world. Once you're up and running with us, you can
restrict your servers to accept connections exclusively from our block of IP
addresses, so that nobody but MailRoute can connect to your servers.

MR Compliance Solutions' services provided are performed only by U.S. Person
employees, as defined in the International Traffic in Arms Regulations (22 CFR
120), Section 120.15, of MailRoute. Additionally, all services, including
accessing and storing services, are performed within the United States.

For information about MR Compliance Solutions and MailRoute, Inc., please
**contact sales@mailroute.net** and specify ITAR or HIPAA.

Start a free [30-day trial](http://mailroute.net/signup.html) today with promo
code "ITAR" or "HIPAA".

## FAQ's

**Q:** Do your non-US web developers have access to any customer data,
especially ITAR?

**A:** Non-US developers do not have access to our production servers. They do
their work locally, submit code to us (we use git), and we review, before
testing on development servers.

They do not have access to our ITAR customer lists or any sort of data.

The same is true for our offshore support. It is not possible for non-US
employees to see our ITAR customers in our interface, nor do they see any
support tickets submitted by ITAR customers.

**Q:** How are logs stored? What are the security controls?

**A:** Logs are stored on a central log server (and temporarily cached on each
production server for 7 days). That server is directly accessible only to
superusers. Only our US-based employees have access to the tools we use to
diagnose mail flow problems or issues.

The logs are kept in clear text for 30 days. At that point they are encrypted
and archived.

**Q:** If I should off-board, what happens to log data?

**A:** We can provide it to you.

The type of data we keep includes all the typical log entries for mail
reception and processing, and a log entry that shows the result of the
filtering process.

Here's a typical message's delivery log entries:

    
    
    2018-11-21T15:18:43+0000 007.lax postfix-inbound/smtpd[7514]: 430R6q29CSzTgvf: client=[sm1.email.bmwusa.com](http://sm1.email.bmwusa.com/)[50.57.212.101]  
    2018-11-21T15:18:43+0000 007.lax postfix-inbound/cleanup[7488]: 430R6q29CSzTgvf: message-id=<[17000127.314095@email.bmwusa.com](mailto:17000127.314095@email.bmwusa.com)>  
    2018-11-21T15:18:43+0000 007.lax postfix-inbound/qmgr[3320]: 430R6q29CSzTgvf: from=<[bounce@bounce.email.bmwusa.com](mailto:bounce@bounce.email.bmwusa.com)>, size=57417, nrcpt=1 (queue active)  
    2018-11-21T15:18:44+0000 007.lax postfix-inbound/smtpd[7519]: 430R6r67h7zTgyH: client=[007.lax.mailroute.net](http://007.lax.mailroute.net/)[127.0.0.1], orig_queue_id=430R6q29CSzTgvf, orig_client=[sm1.email.bmwusa.com](http://sm1.email.bmwusa.com/)[50.57.212.101]  
    2018-11-21T15:18:44+0000 007.lax postfix-inbound/lmtp[7383]: 430R6q29CSzTgvf: to=<[user@domain.com](mailto:user@domain.com)>, relay=127.0.0.1[127.0.0.1]:10024, delay=1.7, delays=0.46/0/0/1.2, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 430R6r67h7zTgyH)  
    2018-11-21T15:18:44+0000 007.lax postfix-inbound/qmgr[3320]: 430R6q29CSzTgvf: removed  
    2018-11-21T15:18:44+0000 007.lax postfix-inbound/smtpd[7519]: 430R6r67h7zTgyH: client=[007.lax.mailroute.net](http://007.lax.mailroute.net/)[127.0.0.1], orig_queue_id=430R6q29CSzTgvf, orig_client=[sm1.email.bmwusa.com](http://sm1.email.bmwusa.com/)[50.57.212.101]  
    2018-11-21T15:18:44+0000 007.lax postfix-inbound/cleanup[7520]: 430R6r67h7zTgyH: message-id=<[17000127.314095@email.bmwusa.com](mailto:17000127.314095@email.bmwusa.com)>  
    2018-11-21T15:18:44+0000 007.lax postfix-inbound/qmgr[3320]: 430R6r67h7zTgyH: from=<[bounce@bounce.email.bmwusa.com](mailto:bounce@bounce.email.bmwusa.com)>, size=58362, nrcpt=3 (queue active)  
    2018-11-21T15:18:44+0000 007.lax postfix-inbound/lmtp[7383]: 430R6q29CSzTgvf: to=<[user@domain.com](mailto:user@domain.com)>, relay=127.0.0.1[127.0.0.1]:10024, delay=1.7, delays=0.46/0/0/1.2, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 430R6r67h7zTgyH)  
    2018-11-21T15:18:45+0000 007.lax postfix-inbound/smtp[7237]: 430R6r67h7zTgyH: to=<[user@domain.com](mailto:user@domain.com)>, relay=[mail.domain.com](http://mail.domain.com/)[192.168.1.99]:25, delay=0.21, delays=0.04/0.01/0.01/0.16, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as D12F4FEF41)  
    2018-11-21T15:18:45+0000 007.lax postfix-inbound/qmgr[3320]: 430R6r67h7zTgyH: removed

And here's a log entry for the filtering:

    
    
    2018-11-21T15:18:44+0000 007.lax D C [bounce@bounce.email.bmwusa.com](mailto:bounce@bounce.email.bmwusa.com) [user@domain.com](mailto:user@domain.com) "" <[17000127.314095@email.bmwusa.com](mailto:17000127.314095@email.bmwusa.com)> -1.167 57286 430R6q29CSzTgvf

**Q:** What is the retention period for logs?

**A:** MR Compliance Solutions confirms that personal data is processed and
stored for these time periods:

  * Data center physical access logs, system infrastructure logs, and application logs will be kept for a minimum of 90 days.
  * Email processing logs are kept for a minimum of 180 days.
  * Statistical data of end-user service usage is kept indefinitely.
  * Passwords are not logged.
  * Certain administrative changes to the Covered Services (such as password changes, adding or modifying user accounts and settings ) are tracked in an area known as the “Audit” and are available fo viewing by MailRoute administrators only. This information may be provided to Customers on request.

**Q:** Does the Store & Forward feature mean that you're storing my mail for
15 days?

**A:** Our Store & Forward feature for disaster recovery is set to a 15-day
lifecycle and is only activated by a server outage on your end. We only store
mail for reattempted delivery if your server is down. As soon as it's back up
and we can deliver the queued mail, we erase it on our side.

**Q:** What type of control over permissions do admins have, relating to each
mailbox?

**A:** Currently there are two levels of permissions, admin and mailbox.
Admins have granular control over mailbox functions (login, view quarantine,
recover messages, change filter settings, etc).

**Q:** Do you use system level or mailbox level S/Mime and who provides this?

**A:** We believe that this is best handled at the client side.

**Q:** Is encryption at rest relevant? And if so, is it provided?

**A:** We don't store any email in any permanent storage while it's being
filtered or once it is delivered to the customer's mailserver. If a mailserver
is down, we do hold the mail and queue it for up to 15 days for redelivery.
It's not encrypted, but it's also not directly accessible to any of our
administrators.

**Q:** Do you have a regression suite of tests that would allow for
standardization?

**A:** We do have suites of tests for our control panel and API, and separate
tests for our processing services. When we make a rule change, we have a large
corpus of Spam and Ham that are used for testing. Rules that pass the tests
are pushed out to production and then later used in a mass re-scoring process
that fine-tunes our rules.

**Q:** Is it possible to disable TLS1? And only have TLS1.2 and TLS1.1?

**A:** Possibly. We're working on DANE support and, at this time, disabling
TLS1 causes many issue with other servers. Since we fallback to plain-text to
ensure that mail is passed through, we believe it's better to fallback first
to TLS1 than not at all.

We always start with the higher level encryption protocols and fallback to the
lesser ones.

Please note that we use opportunistic TLS. One obstacle with forcing TLS for
specific domains is that you don't know who is (allegedly) sending a message
until you see the MAIL FROM SMTP command, and at that point, if TLS isn't
already in use, then the potentially sensitive information is already in the
clear (and even more can be leaked if SMTP pipelining is being used).

Also, there are forwarded messages and bounce messages, which can only be
identified by the IP address of the server and possibly the HELO name of the
client. Keeping this up to date in a way that doesn't end up causing lost mail
is problematic.

Thus, TLS security for mail is almost entirely the client's responsibility. We
are an enabler of the security, and we ensure its passage in such a fashion,
but it's really the sending system's responsibility to enforce TLS policy.

Now, that being said, we can do a few additional things, as long as the
"gotcha's" are understood. We can provide you with an MX record for your
inbound, and an outbound relayhost/smarthost that forces TLS - you just have
to understand the potential for mail to be blocked and accept that. And of
course, we can force all connections to your servers to be TLS encrypted. As
long as it's understood that if you disable TLS or have a certificate issue,
mail WILL bounce.

**Q:** For the certificates, what org/company is your RA and CA for the
certificates you are using?

**A:** GlobalSign Root. AlphaSSL CA - SHA256 - G2L.

**Q:** What org/company is your DNS provider?

**A:** We host our own DNS in multiple datacenters. And we use dnsmadeeasy.com
as a third-party secondary for our DNS hosting.

**Q:** Is the load balancing controlled in conjunction with DNS configurations
(round-robin) or through a specific capability at one of your datacenters that
would then reroute to the other DC?

**A:** We return multiple A records, with the order based on datacenter
traffic loads and patterns. It changes very rapidly. Then traffic is directed
to the best cluster. It's possible for traffic to even be directed from Los
Angeles to a Las Vegas datacenter (and vice versa) after the initial
connection to our load balancers, if conditions warrant.

**Q:** What happens when a datacenter goes down/offline. Does the load
balancing stop or is there a peer server at the other data center?

**A:** Load balancing happens at the datacenter, cluster, and server levels.
If any part goes down, traffic is redirected to the next best destination. Our
service is distributed across three datacenters. Failure of a datacenter does
not mean we would lose our load balancing capabilities.

**Q:** What happens to the mail that is not yet delivered but still in your
environment when an incident occurs such as a server going down?

**A:** Email is replicated between at least two server clusters, which may or
may not be in the same datacenter. If they are in the same datacenter, they
are on different power sources and have different internet feeds.

**Q:** What are your quality control or quality assurance process in various
areas, such that one person is not making changes to multiple parts of the
environment without tracking, review or approval?

**A:** Any changes made to code for our interface, configuration changes, spam
rule updates ect are all done on a set of development systems. When
development is happy with their work, it's released to testing. That's a small
cluster of servers identical to our production systems. There changes are
tested and verified before being released to the production servers.

**Q:** Do you use version control, team review and approval before changes,
logging of changes, etc.?

**A:** Yes, every configuration file, every piece of source code is under
version control (we use git), and subject to multiple checks before anything
is ever released to production.

All of our server configuration and management is handled using infrastructure
automation systems (such as puppet and ansible). Changes are never made to
servers directly, and all changes are carefully planned and scripted.

**Q:** Do you have periodic review of the environment to determine if
something is not fully in line with known and approved specs?

**A:** It's an ongoing process with us. Every few months we step back and look
at everything from the ground up to see if we've drifted away from our core
intention or process in any area. Our standard procedures keep us from
drifting, but we do diligently check ourselves regularly.

**Q:** What version of protocols for TLS are you using?

**A:** We do **not** use SSLv3.

In our nginx configurations (for our web control panel and our API), we don't
allow sslv3, and we disable the weak ciphers like md5 and DSS:

ssl_protocols TLSv1.2 TLSv1.1 TLSv1;  
ssl_ciphers
ECDH+AESGCM:DH+AESGCM:ECDH+AES256:DH+AES256:ECDH+AES128:DH+AES:ECDH+3DES:DH+3DES:RSA+AESGCM:RSA+AES:RSA+3DES:!aNULL:!MD5:!DSS;

**Q:** Do you have a plan for BCDR in case one gateway or site went down?
Where do you relocate/reroute data to? In short, how do you perform your
guaranteed level of 3x redundancy?

**A:** We run fully redundant systems (separate switches, power sources, ISP
connections) in each of our three datacenters, which are geographically
distributed across the United States. Because of the high level of DevOps
automation in our systems, we're able not only to add capacity within a
datacenter very rapidly, but adding additional datacenters is a quick and easy
operation.

Each individual datacenter is capable of handling all MailRoute traffic at
peak periods. Each is capable of running in a completely stand-alone fashion.

Traffic is dynamically load-balanced between datacenters (and then further
load balanced to server clusters within each datacenter). This is based not so
much on the specific geography of the sender of traffic (like most websites or
CDNs would balance traffic), but more so based upon the load and performance
of the server clusters in each datacenter. This way we're able to give the
highest overall performance and give our 5-nines (99.999%) uptime guarantee.

**Q:** Do you quarantine email?

**A:** As with many pieces of our service, we can customize our features to
best fit your environment. Our standard is to quarantine mail for 15 days.
This can be completely disabled for your domain(s). Indeed, content filtering
can be disabled entirely, making MailRoute the ITAR-compliant pass-through for
your email, so no mail sent to your domain(s) would ever be quarantined.

We can disable all content-based and greylisting-based filters for your
system. We do have a low-level denial of service protection (based on things
like traffic pattern analysis of known egregious spammers and attackers) and
certain blacklists that we typically do not disable (and which have an
astronomically low false-positive rate).

**Q:** How difficult -- or simple -- is to activate or setup a MailRoute
account?

**A:** To enable our service, all you need to do is set things up in our
control panel so we know where to relay email, add your list of mailboxes, and
then change the MX record to point to our systems.

We'll accept mail and then forward it to your server. We don't touch the body;
we do add the necessary headers (Received headers, and our information X-
headers that show the mail processing flow).

Adding the list of mailboxes is something where we can help you, and we make
it simple for you to do this manually, import CSV files, sync LDAP or
ActiveDirectory servers, or use our API. We're happy to help you get it set up
in the best possible way for you.

**Q:** Would our email domain would be assigned in DNS to your mail system?
Does this make handling S/MIME more complicated?

**A:** S/MIME would be handled by your own servers and/or clients.

When a message is encrypted like that, we obviously cannot scan the contents
of the message, so our default is to pass it along with "UNCHECKED" added to
the header. Of course, we can turn off that warning for you, if you'd like.

[Start a free 30-day trial today.](http://mailroute.net/signup.html) Use promo
code "ITAR" or "HIPAA".

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

