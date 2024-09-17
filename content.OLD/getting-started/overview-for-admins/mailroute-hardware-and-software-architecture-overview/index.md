---
created_at: 2022-05-25 11:59:59
date: 2024-08-28 15:06:28
description: MailRoute's proprietary network architecture with redundant data centers,
  load balancing, and layered email filtering offers 99.999% uptime and robust email
  security. Learn about their server setup, compliance certifications, and seamless
  Microsoft 365/Google Workspace integration.
draft: true
params:
  author: Unknown
summary: This article provides an overview of MailRoute's hardware and software architecture,
  including details about their data centers, server setup, email filtering process,
  and compliance certifications. It highlights their redundant and distributed system
  for high uptime and reliability.
tags: null
title: MailRoute Hardware and Software Architecture Overview
---


**MailRoute Hardware and Software Architecture**

MailRoute employs the same proprietary network configuration that Microsoft
purchased from us in 2005. Customers can utilize a proprietary API-level
integration that we have with both Microsoft 365 and Google Workspace to
populate and manage your account, reducing duplicated admin labor.

We continuously develop and upgrade our filtering, customer interface and
granular account controls, so the system is up to the minute in threat
assessment and elimination, and you have no hardware or software updates to
manage. Contact sales@mailroute.net for more information.

**Datacenters**

Three datacenters minimum, geo-distributed in the United States. Each data
center runs at 33% capacity maximum for 3x failover capability. This allows us
to provide 99.999% uptime guaranteed (26 seconds of downtime per week, in our
Service Level Agreement).

The overall architecture of each location is the same. Each runs the same
hardware and software, and can function fully in a stand-alone mode. We
balance traffic between the centers.

The datacenters are secure facilities with 24x7 monitoring and staff.
Biometric checks are required for entry. Within the datacenters, all of our
equipment is further segregated in locked racks and cages and inaccessible to
any other tenant of the datacenter.

**Global Load Balancing**

The datacenters are globally load-balanced. Incoming traffic is directed to
whichever datacenter is best able to handle the traffic, based on its
location, performance, network health, load, etc.

**Connectivity within the datacenter**

Our cages and racks in datacenters have Internet feeds coming from two
different providers, and each provider has a minimum of two fiber drops over
two disparate paths. There are two primary routers, and each feed from each
provider connects to each router for additional redundancy. Each router
connects to multiple switches, and every switch is connected to both routers.

There are multiple load balancers in each rack or cage, and each is connected
to a minimum of two switches. These load balancers direct incoming traffic to
a server cluster, which has the best health and performance at the given time.
The traffic is then directed to the optimal server in the cluster.

****

**Server Architecture**

We use a "Redundant Array of Independent Servers" model, as popularized (and
taken to the extreme) by Google. Each datacenter has racks of servers. Each
server has two network connections to two different switches, and each of the
servers can maintain connectivity in the event that a router, a switch, a data
path, or any other aspect of the network fails.

The servers are small but fast workhorses with 16GB of ram or more and SSD
drives for buffering mail. All configuration settings are stored in a fully
redundant database cluster. Any email delivered is immediately replicated to
two servers in the event that any server were to die while processing mail, to
ensure that nothing is lost.

**Software Architecture**

We use a multi-layered approach to email filtering. Incoming connections are
checked and denial of service attacks are blocked. IP addresses that have very
bad reputations (all spam, no ham) are logged and dropped. We use blacklists
(internal and those shared with other filtering companies, as well as some
from outside providers) to help determine if a connection is likely spam or
malicious.

Email that makes it past the IP checks goes into the content filters.
Attachments are parsed and recursively decoded, and all parts are run through
a minimum of two anti-virus engines. Email content is scored, URLs and links
in messages are checked, headers are verified, and the email ends up with an
overall "SpamScore". Depending on that score, the message can be delivered,
tagged and delivered, quarantined or dropped – all depending on the settings
of the mailbox.

Email that is quarantined is stored on our local database clusters for a
minimum of two weeks.

**Filtering and Quarantine**

By changing your MX records to point to MailRoute's block of 8 Class C IP
addresses, your mail is sent to us by the outside world. We sit between the
world and your mail servers. That mail is run through 40 different RBL's
(real-time blackhole lists) and through several AV engines. Egregious mail is
blocked outright and the remaining mail is sent through our wholly owned,
proprietary set of filters and rules. These rules are upgraded daily, if not
hourly. MailRoute has built our system from the ground up and has control over
every aspect of it, for the highest level of configurability. Filtered mail is
assigned a score and is deemed susptect, in which case it's quarantined for
you, or clean and delivered. Your quarantine is available in your dashboard,
via Quarantine Notifications that are sent on a customizable schedule, or
coming in 2025: a quarantine app. Outbound mail is sent through our system and
given a health-check. Any issues are raised immediately with the sender and
the account admin(s). Further, we use AI to detect regular sending/receiving
behaviors to adjust our scoring system and get your clean mail to you quickly.
The entire process described above happens in a fraction of second, typically.

Compliance:

NIST 800-171

CMMC

DFARS

FedRAMP

ITAR

HIPAA

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

