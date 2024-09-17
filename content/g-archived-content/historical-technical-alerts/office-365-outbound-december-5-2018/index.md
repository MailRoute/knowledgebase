---
created_at: 2018-12-05 16:11:41
date: 2020-02-07 19:22:01
description: Temporary Office 365 outbound email relay issue resolved by updating
  script to detect new Microsoft servers and increasing frequency to every 5 minutes.
draft: true
params:
  author: Unknown
summary: The article discusses a temporary issue with outbound email relay for some
  Office 365 customers due to Microsoft adding new servers for outbound relay. The
  issue was resolved by updating the script that detects the new servers and increasing
  its frequency.
tags: null
title: Office 365 Outbound - December 5, 2018
---


Office 365 Outbound

  

There was a temporary issue with outbound email relay for some of our o365
customers. A small subset of our servers were affected as a result of
Microsoft, for the very first time in a long time, adding a new bank of
servers for outbound relay.

We autodetect this by pulling the list of records from their SPF records with
a small script, and that script runs twice a day, which has always been fine-
they haven't updated that list in several years, at least. And running it
twice a day seemed like a good setting, since the TTL on that SPF record used
to be over 12 hours long.  
  
The script ran on all of our servers, but on 007.lax and 011.lax it didn't run
until, apparently, shortly after they added those servers, leaving them out of
date for up to 12 hours.  
  
We've pushed the changes to those servers, and increased this script to run
every 5 minutes, since they've set the TTL for that record down to 600 seconds
now, to ensure we pick up changes very rapidly.

If outgoing mail was relayed from these two affected servers it would have
been refused and a bounce back message would have been generated. If mail was
relayed through our other servers, it was relayed successfully.

