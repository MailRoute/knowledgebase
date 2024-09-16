---
created_at: 2020-02-28 17:29:19
date: 2024-04-12 14:40:30
description: Troubleshoot and resolve the issue of company web forms being routinely
  quarantined as spam by making adjustments to the email sending code and header configurations.
draft: true
params:
  author: Unknown
summary: The article provides troubleshooting steps for resolving an issue where company
  web forms are routinely quarantined as spam. It suggests modifying the code to use
  a standard email address and setting the sender's address in the "Reply-To" header.
tags: null
title: Quarantined Web Forms - Troubleshooting and Resolution
---


If you're finding your company web forms are routinely quarantined as spam,
there are few adjustments you can make to resolve this issue.

It's a common issue caused by web programmers who don't really understand
email, or the best way to handle these sorts of forms.

They want users to be able to just hit "reply" to forms submitted by a users
on a site. But when you put the user's name in the "From" header and/or set
the SMTP envelope MAIL FROM parameter to that address, then:

1\. You break SPF

2\. You break DMARC

3\. You cannot Allow (as you see)

4\. You may trigger off all sorts of spam filter issues, because they will see
the mail (properly) as being "forged".

The very best thing to do is to modify the code that sends the email. Use a
single, standard address that's in your control, in the "From" header and the
SMTP envelope MAIL FROM setting. Then you can Allow it. It won't look like
it's forged. It can pass SPF/DKIM/DMARC checks.

Then set the sender's email address in a "Reply-To:" header. Any email client
will respect that header, and hitting the "reply" button will properly compose
an email to the submitter's email address.

If you absolutely cannot do that, we can Allow a specific IP address of the
server sending the emails as well as the email address in the Allow by
Server/IP section of your dashboard.

A drawback of using Allow by IP/Server alone is that if you have any
compromise of that server, and it starts flooding you with spam, those emails
will all come through.

