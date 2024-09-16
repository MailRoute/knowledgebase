---
created_at: 2018-08-09 17:15:32
date: 2024-04-23 16:15:06
description: Learn how to troubleshoot website submission form issues where emails
  appear spammy due to incorrect sender address settings, and get recommendations
  for proper SMTP envelope and header configurations.
draft: true
params:
  author: Unknown
summary: The article discusses the issue of web submission forms incorrectly setting
  the sender email address, which can cause email delivery problems. It provides recommendations
  for web developers to fix the issue by setting the proper SMTP envelope and header
  addresses.
tags: null
title: Website Submission Form Troubleshooting
---


Unfortunately, it's very common for web developers who write scripts for
submission forms to send email with the SMTP envelope "MAIL FROM" address set
to the address provided by the user who submitted the form. They do this so
that the recipient of the email can simply hit "Reply" to send an email to the
submitter.

But I'm afraid that this is a bad idea on a number of levels.

By essentially forging the sender of the message, the emails will look spammy
to pretty much any spam filtering service or software. Emails sent this way
will violate SPF, DKIM, ADSP, and DMARC protocols.

There's no way to Allow the sender of the message, since it's being set
differently for every message.

**What you can do** :

Speak to your web developer and ask them to make a small change on the script:

1\. Have them set the SMTP Envelope MAIL FROM and the header "From:" addresses
to use a standard address that's within your own domain. You can then Allow
that address, so it will always arrive, no matter how spammy it might appear
to our filters.

2\. Ask them to set a "Reply-To:" header with the submitter's provided email
address. All mail clients will recognize this, and when the recipient replies
to the message, they will send to that specified address.

Another option, if you absolutely cannot change the form submission script, is
to have the emails sent to a special address on your end, and to disable spam
filtering for that account or to set it to a higher spam quarantine cutoff
number.

