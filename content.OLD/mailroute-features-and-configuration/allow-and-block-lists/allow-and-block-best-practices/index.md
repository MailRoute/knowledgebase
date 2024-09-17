---
created_at: 2020-02-29 00:04:14
date: 2024-04-12 14:40:30
description: Comprehensive guide on using allow and block email filtering tools effectively.
  Covers best practices, security considerations, tips for safe allowing and blocking,
  and managing allow/block lists.
draft: true
params:
  author: Unknown
summary: The article provides best practices and tips for allowing and blocking emails,
  highlighting the importance of using these tools judiciously to avoid unintended
  consequences. It also covers security considerations when allowing or blocking specific
  domains or email addresses.
tags: null
title: Allow and Block Best Practices
---


An important tool in controlling incoming emails is the Allow and Block
setting in your dashboard.

You can prevent future emails from spammers (Block) or you can ensure that
important and valued email arrives in your inbox (Allow).

Allow and Block are considered heavy handed tools which should be used
sparingly. Incorrect blocking can inadvertently block important emails. Allow
can permit forged emails to bypass our filters, no matter how spammy the email
looks.

How They Work

Allow Lists

Tells us that you would like all future emails to **_bypass_** our spam
filters (we still will check for viruses and malware). By choosing Allow you
are trusting that this sending domain or address is safe for the foreseeable
future. If that domain becomes compromised in the future your domain will also
be vulnerable to these emails.

It's important to note that spammers count on major and popular domains being
on the Allow list.

Block

Tells us you no longer want to receive any mail from a domain or email
address. All future emails will be blocked and emails from that sender will be
quarantined.

Tips for safe Allow Settings

\- Do not Allow entire domains. Instead Allow specific email addresses rather
than the entire domain

\- A domain-based Allow list isn't as secure as an IP address-based list,
because domains can be spoofed.

\- Do not Allow major or popular domains. No banks, merchants, credit card
companies, mobile carriers, Amazon or Microsoft (the two most often
impersonated in the world)

\- Ideally, Allow by sending IP/Server AND the email address for a more secure
method.

\- If you wish to Allow a major and/or popular domain, you can Allow the
combination of IP/Server and domain in the Allow by IP/Server tab. That will
ensure email from that domain only comes from the block of servers.

\- Review your Allow list regularly and update/edit. When they pile up they
can build gaps in email security.

\- Review your user's Allow lists to ensure they're following safe practices

\- If your domain or user has hundreds or thousands of Allow lists, they
should all be reviewed and edited. This causes a major conflict with safe and
efficient mail flow for the user or domain by not allowing our filters to do
their job.

Tips for effective Blocking

\- Add a domain/IP/Server to your domain-wide or user Block setting.

\- In the case of bulk, opt-in marketing emails, which we consider 'ham',
Block will largely be ineffective. In most cases blocking sending domains such
as Amazonses or Mail Chimp will block other important emails from other
services you regularly subscribe to.

  * The sending email address changes with each opt-in marketing email making it impossible to Block
  * Best method to no longer receive emails is to unsubscribe. Many opt-in mailings have safe and rigorous unsubscribe policies.

\- Review your Block lists regularly and update/edit. When they pile up they
can build gaps in email security.

\- Review your user's Block lists to ensure they haven't inadvertently blocked
an valid sender

\- If your domain or user has hundreds or thousands of Block lists, they
should all be reviewed and edited. This causes a major conflict with safe and
efficient mail flow for the user or domain.

Additional Allow List Security

As a result of the large volume of phishing emails and forgeries received from
these domains, we no longer Allow lists of freemail domains such yahoo.com,
gmail.com, hotmail.com.

You can still Allow [user@freemail.com](mailto:user@freemail.com) but you will
not be able to Allow freemail.com

Tips

  * For false-positives in quarantine the best method is to 'Recover' rather than just Allow the sender. This will provide feedback for our Bayesian filters telling us it's not spam but legitimate mail.
  * If your domain has hundreds or thousands of Allow and Block lists and you're experiencing high volumes of false-positives and/or forgeries, it might be wise to delete all entries and start over. This will allow our filters to work as they were intended. 

*Ask our Support team if you would like a review of your current listings and make any security recommendations. Contact [support@mailroute.net](mailto:support@mailroute.net).

