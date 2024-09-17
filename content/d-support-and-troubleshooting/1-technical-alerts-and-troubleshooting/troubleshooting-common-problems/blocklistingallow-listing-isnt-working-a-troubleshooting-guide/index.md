---
created_at: 2019-02-19 17:31:53
date: 2024-08-07 19:29:56
description: Troubleshoot email blocklisting/allowlisting issues with this guide.
  Check headers, review settings, understand overrides, and seek support if needed
  for cases where unwanted emails get through or wanted emails are blocked.
draft: true
params:
  author: Unknown
summary: This article provides a troubleshooting guide for situations where email
  blocklisting/allowlisting isn't working as expected. It outlines several steps to
  check headers, review settings, and seek further assistance if needed.
tags: null
title: Blocklisting/Allow listing Isn't Working! A Troubleshooting Guide
---


If you're receiving emails from sources you have previously Blocklisted, or
not receiving emails from sources you've put in your Allow list, there may be
some factors to look into.

Here are some ways to troubleshoot Block/Allow list issues:

1\. Check the headers of the sent email and review the x-spam scoring for
block list/allow listing details. If you see this information, it can indicate
the reason the email came through/didn't come through MailRoute.

This is important for revealing who the sender is so you can edit your
Allow/Block listings. If you think your newsletter is coming from
[XYZ@domain](mailto:XYZ@domain) and you've put in an Allow/Block listings, the
header may show it's being sent by a third party mailing service like
amazonses or send grid and that could potentially be why it's not allowed or
blocked.

2\. Allow lists usually over-ride Block lists. So if you've blocklisted the
domain aol.com but you've got mom@aol.com in your domain-wide Allow list
settings, the email will come through to your inbox.

3\. Review all Block & Allow listings for your domain. Allow listing
'freemail' domains such as yahoo.com, aol.com, gmail.com is not recommended as
they can be a major source of spammy emails. That goes for major and popular
domains like banks, Intuit, Pay Pal, Docusign, also

4\. Remember more specific entries override more general entries. You can
blacklist aol.com but still have [mom@aol.com](mailto:mom@aol.com) whitelisted
in your individual settings.

5\. Use Allow Listings very sparingly. They allow all future mail from that
sender no matter how spammy they are. We recommend using a more secure Allow
List by IP/Server.

5\. If you're still unsure, send the original, unforwarded email as a .eml
attachment to [support@mailroute.net](mailto:support@mailroute.net) and we
will review the details.

