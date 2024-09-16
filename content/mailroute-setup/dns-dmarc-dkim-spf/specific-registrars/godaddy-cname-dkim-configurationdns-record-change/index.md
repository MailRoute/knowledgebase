---
created_at: 2021-02-15 21:38:42
date: 2024-07-24 18:11:31
description: A comprehensive guide on configuring DKIM CName DNS records in GoDaddy
  to enhance email security and authentication for your domain. Follow the easy steps
  with visuals.
draft: true
params:
  author: Unknown
summary: This article provides step-by-step instructions on how to configure DKIM
  CName DNS records in GoDaddy for email authentication and security purposes.
tags: null
title: GoDaddy CName DKIM Configuration/DNS Record Change
---


Login to your GoDaddy account

1\. Go to My Products>Domains>DNS.

2\. Select Add

3\. Your page will look like this (below)

Select:

Type: CName

Host: mr01._domainkey

Points to: mr01.dkim.mailroute.net

TTL: 1 Hour

![mceclip0.png](mceclip0.png)

Click Save.

Repeat steps for mr02._domainkey and mr03_domainkey. Your CName records should
look like this when finished.

![mceclip1.png](mceclip1.png)

