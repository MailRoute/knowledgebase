---
created_at: 2018-05-30 18:10:49
date: 2018-05-31 17:55:12
description: Customers report outbound email being blocked by recipient domains due
  to blacklisting on SpamCannibal DNSBL, which was taken over and has "blacklisted
  the world," causing issues for mail servers using it.
draft: true
params:
  author: Unknown
summary: The article discusses reports of customers experiencing outbound email being
  blocked due to a blacklisting on SpamCannibal DNSBL. It explains that SpamCannibal
  has been taken over and has "blacklisted the world," causing issues for administrators
  who use this DNSBL in their mail server configuration.
tags: null
title: Outbound Email Blocked by SpamCannibal DNSBL
---


There are reports of customers receiving messages which indicate their
outbound email has been blocked by a recipient domain because of a
blacklisting on SpamCannibal DNSBL.

We have been made aware that SpamCannibal, which has been inactive since last
summer has been taken over and have "blacklisted the world" resulting in
admins blocking all mail if they use this DNSBL in their mail server
configuration.

According to El Reg, "In this case, the new 'owners' of the domain have set a
wildcard domain, so that any subdomain of spamcannibal.org returns an IP
address. This is interpreted as the domain being blacklisted."

