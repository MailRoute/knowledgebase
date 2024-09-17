---
created_at: 2022-11-30 17:16:39
date: 2023-03-20 20:38:32
description: Learn how to change MX records for your Google Workspace account to route
  email through Mailroute's mail.mailroute.net server instead of Google's servers.
draft: true
params:
  author: Unknown
summary: The article provides instructions for changing MX records with Google Workspace,
  specifically directing email through Mailroute by adding the mail.mailroute.net
  server instead of Google's servers.
tags: null
title: Google Workspace/GSuite/Google Apps
---


To change MX records with Google Workspace please click on the link below and
follow the steps.

When you get to Step 4, instead of adding the Google servers to the MX, add
mail.mailroute.net.

Step 4: Add new MX records

To direct your email to your Google Workspace account, you have to add new MX
records to your domain.

  1. Under **Host Name** , enter **@**.
  2. Under **Mail Server** , enter mail.mailroute.net
  3. Under **Priority** , enter the priority level value for 
  4. Set any TTL values to 1 Hour (value=3600).
  5. Review your new MX records and save your changes.

<https://support.google.com/a/answer/33915?hl=en#zippy=%2Cstep-sign-in-to-
your-domain-host-account%2Cstep-verify-the-change-in-your-google-admin-
console>

