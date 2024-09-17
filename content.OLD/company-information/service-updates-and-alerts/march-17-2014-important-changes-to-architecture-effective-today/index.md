---
created_at: 2014-03-17 19:22:30
date: 2024-07-29 21:38:17
description: MailRoute announces important changes to their architecture, including
  opening a third data center, switching to Juniper routers, and implementing custom
  software-based load balancers to improve redundancy and reliability.
draft: true
params:
  author: Unknown
summary: MailRoute made significant changes to its architecture by opening a third
  data center and altering its infrastructure to improve redundancy and reliability.
  The changes include moving away from Cisco routers and Foundry load balancers to
  Juniper routers and custom software-based load balancers.
tags: null
title: March 17, 2014 - Important Changes to Architecture Effective Today
---


Thank you for your patience.

MailRoute has taken significant steps to manage our growth by having a
presence in two data centers, and we are opening a third data center today
while significantly altering our architecture to provide another level of
redundancy and to increase the reliability of our entire system.

In our old architecture, the balancing of traffic amongst datacenters and the
servers inside of them had shared component - the routers and loadbalancers
exchanged regular information about network and server health to determine the
optimal route and destination for all traffic. The idea is that the low-level
network statistics (speed, location, number of connections, etc) were adequate
to properly load-balance traffic amongst all our servers in our datacenters.
MailRoute’s configuration has included, for many years, a significant
investment in Cisco and Foundry hardware to implement this model.

In the past 72 hours, we have seen issues with that hardware, where an issue
in the Cisco routers is affecting the Foundry Load Balancers. This is not how
the hardware is meant to operate, but it is happening. Neither company seems
to be able to offer a reliable fix.

Fortunately, we were simply a few days away from moving to a new architecture.
We have been running a subset of our service on this new system for the last 6
months, and the latest trouble is making it clear that it's time for us to do
the final migration.

We’re moving off of Cisco routers onto Juniper. We are moving off Foundry load
balancers to custom software-based load balancers that can better evaluate the
email characteristics of our unique environment.

Yes, we're doing this a little ahead of schedule - but not by much, only by a
few days. This was scheduled to be happening this weekend, and instead we've
started rolling it out now. In short, we are moving away from a significant
investment in our existing hardware to create a permanent fix to this problem.

The change should be completely transparent to all our customers, except that
you should see improved speed and connectivity and any downtime issues should
go away. Inbound and outbound traffic, instead of sharing a central component,
will all be completely independent in each datacenter.

Sincerely,

Thomas A. Johnson

Founder, CEO

MailRoute, Inc.

