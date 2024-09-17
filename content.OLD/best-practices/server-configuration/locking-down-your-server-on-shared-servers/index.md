---
created_at: 2015-07-06 18:03:57
date: 2022-09-02 17:41:26
description: Learn how to lock down your email server on a shared hosting environment
  by setting up a filtering rule to redirect external emails without MailRoute headers
  to a spam folder, enhancing security.
draft: true
params:
  author: Unknown
summary: The article provides instructions for locking down a shared server by setting
  up a filtering rule to redirect emails that do not contain MailRoute headers into
  a spam folder. It covers identifying the specific header to look for and how to
  create the rule in email clients.
tags: null
title: 'Locking Down Your Server on Shared Servers '
---


**I'm on a shared server because my email is hosted for me through a third
party:**

_(If you run your own mail server,
click[here](https://support.mailroute.net/hc/en-us/articles/224059188) for
instructions.)_

Sometimes, if you're on a shared server, you can't configure your firewall as
you would if you ran your own mail server. If that’s the case, we suggest that
you set up a filtering rule on your server, or on your email client ******
software on your desktop, if you have this option. The rule will redirect any
email **from the outside** that doesn’t contain the MailRoute headers into a
new or existing folder in your mailbox (don't apply this rule to mail being
sent within your domain).

Every message we process will contain a number of headers. One that's good to
use for creating a rule looks like this:

X-Virus-Scanned: by MailRoute

If that header is not there, the email didn't come through us, or it's mail
being sent within your domain and therefore doesn't need to be scanned by
MailRoute. Given all the different email software and management tools, it's
difficult to provide a simple how-to, to help you create this filter, but the
general idea is:

If (email is from outside, and doesn't have the MailRoute header)

then (move it into a spam folder).

Optional: You may want to add an additional check for the presence of a
Resent-To header. This is added to all re-sent email. It will contain the
address of the recipient, like this: Resent-To: user(at)domain(dot)com. This
will pick up any released emails from the quarantine which do not include the
X-Virus-Scanned: by MailRoute.

Your email or webmail software documentation will provide further instructions
on how to set up a rule.

Still have questions? Contact us at
[support@mailroute.net](mailto:support@mailroute.net), 888.485.7726.

****What's an email client?** It is the email software you use to manage your
email (e.g. Outlook 2007, Outlook 2010, Apple mail, etc).

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

