---
created_at: 2020-05-13 17:38:30
date: 2021-03-02 17:43:50
description: Learn how to configure your cPanel host to bypass SpamAssassin and handle
  emails that bypassed MailRoute, an email security service, by disabling filters
  and creating rules.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring a cPanel host
  to bypass the internal SpamAssassin filter and discard, reject, or file emails that
  did not pass through MailRoute, a popular email security service.
tags: null
title: 'cPanel  - Locking Down the Server '
---


To configure your cPanel host to bypass the internal SpamAssassin filter and
to discard, reject, or file email that did not pass through MailRoute, simply
follow these steps:

1\. Login to your cPanel account.

2\. Click "Email" in the left menu to scroll to the Email Features:

![PastedGraphic-3_2.png](pastedgraphic-3_2.png)

3\. Click 'Apache SpamAssassin"

4\. Click 'Disable SpamAssassin"

![PastedGraphic-4.png](pastedgraphic-4.png)

5\. Click "Go Back":

6\. Click "Email" in the left-hand column again to return to the email
settings.

7\. Click "Global Email Filters":

![PastedGraphic-6.png](pastedgraphic-6.png)

8\. Click "Create Filter":

![PastedGraphic-7.png](pastedgraphic-7.png)

9\. Name the new filter "Bypassed MailRoute", and add two rules -

"Any Header" "does not contain" "X-Virus-Scanned: by MailRoute"

AND

"Any Header" "does not contain" "Resent-To:"

Choose "Deliver to Folder" or "Discard Message" or "Fail with Message" per
your preferences:

And then click "Save"

![PastedGraphic-8_2.png](pastedgraphic-8_2.png)

That's it! That will disable the additional SpamAssassin filtering built into
cPanel, and remove any email that came directly into your server, bypassing
MailRoute

