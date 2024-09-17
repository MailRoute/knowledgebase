---
created_at: 2021-02-25 19:20:27
date: 2024-02-20 20:41:34
description: Detailed guide on how to set up DKIM (DomainKeys Identified Mail) records
  as CName entries in CloudFlare's DNS manager, ensuring proper email authentication
  and reputation.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring DKIM records
  as CName entries on CloudFlare's DNS manager for a domain. It covers logging into
  CloudFlare, locating the domain, accessing DNS settings, and creating the necessary
  CNAME records for DKIM.
tags: null
title: CloudFlare CName DKIM Configuration
---


##### 1\. Login to CloudFlare

Navigate to [cloudflare.com](https://cloudflare.com/), enter your credentials
to login.

##### 2\. Locate your domain

On the CloudFlare dashboard's home page, find your domain you want to add the
DKIM record to, then click.

![dkim-cloudflare-home.png](dkim-cloudflare-home.png)

##### 3\. Manage DNS

Select the DNS button.

![dkim-cloudflare-domain.png](dkim-cloudflare-domain.png)

##### 4\. Create the record entry

Enter the settings for your DKIM record:

![add-dkim-record-cname-cloudflare.png](add-dkim-record-cname-cloudflare.png)

In the Type drop down menu select CNAME

In the 'Name' tab add: mr01._domainkey

In the Target tab add: mr01.dkim.mailroute.net

Set TTL to auto

Click the Save button and your records are now added!

Repeat Step 4 for mr02._domainkey and mr03._domainkey

If you have any questions regarding the instructions please contact
[support@mailroute.net](mailto:support@mailroute.net)

