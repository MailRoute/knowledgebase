---
created_at: 2022-03-22 12:56:21
date: 2024-02-19 20:16:54
description: MailRoute advises customers using Okta for authentication to take precautions
  after a security breach at Okta, including collecting logs, rotating passwords,
  and disabling Okta support access.
draft: true
params:
  author: Unknown
summary: The article provides advice for customers of MailRoute who use Okta for authentication
  after a security breach at Okta. It recommends steps to mitigate potential risks,
  such as collecting logs, rotating passwords, and disabling Okta support access.
tags: null
title: 'MailRoute Advice for Okta Customers '
---


March 22, 2022

There has been news today of a major security breach with Okta, the
authentication and identity provider.  
  
<https://www.theverge.com/2022/3/22/22990637/okta-breach-single-sign-on-
lapsus-hacker-group>  
  
**MailRoute itself, is neither a customer nor partner with Okta and does not
use any of their services. We do not have any direct exposure in this
breach.**  
  
We do support SAML2 authentication methods, and have notified all our
customers who use Okta, and have disabled Okta authentication pending further
review of this breach.  
  
  
We recommend that any customer using Okta:  
  
1\. Collect and preserve all Okta logs, especially the "system log" that is
the main audit trail for Okta events:
<https://developer.okta.com/docs/reference/api/system-log/>  
  
2\. Search the audit logs for suspicious data, focusing especially on
superuser and admin accounts.  
  
3\. Rotate passwords for any superuser and admin accounts. It's too early to
know if this needs to be recommended for all user accounts.  
  
4\. If you have Okta support access enabled, it's a good idea to disable that,
since Okta internal credentials may have been compromised.
<https://help.okta.com/oie/en-us/Content/Topics/Settings/settings-support-
access.htm>  
  
5\. Check for accounts (especially privileged accounts) created after the
apparent time of the original breach - circa Jan 21, 2022

