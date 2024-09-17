---
created_at: 2021-01-31 16:36:08
date: 2024-02-19 20:18:24
description: Spamcop, a popular spam reporting service and blacklist, experienced
  downtime due to a lapsed domain renewal, causing some email services to falsely
  identify all emails as spam. This article provides updates and clarifies that MailRoute's
  inbound service was unaffected.
draft: true
params:
  author: Unknown
summary: The article discusses the temporary downtime of the Spamcop spam reporting
  service and blacklist due to a lapsed domain renewal, which caused some email services
  falsely identifying all emails as spam. It clarifies that MailRoute's inbound service
  was not affected by this issue.
tags: null
title: Spamcop  - Down as of 31 January 2001
---


Sunday, January 31, 2021. The spam reporting service and blacklist Spamcop
have not renewed their domain name.

Email services using the Spamcop Blacklist (bl.spamcop.net) are falsely
identifying all emails as spam.

MailRoute does **not** use the Spamcop blacklists; our inbound service is not
facing this issue. But other companies and services who use Spamcop may be
refusing or quarantining all email that arrives.

![mceclip0.jpg](360103122433.jpeg)

For further articles please see here:

  * https://www.reddit.com/r/sysadmin/comments/l9asw7/spamcop_domain_expiredparked/
  * https://www.internetnews.me/2021/01/31/spamcop-offline-cos-the-domain-expired/

