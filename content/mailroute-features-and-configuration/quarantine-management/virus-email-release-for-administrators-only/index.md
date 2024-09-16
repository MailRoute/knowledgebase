---
created_at: 2019-08-20 17:47:56
date: 2024-04-12 14:40:30
description: Learn how administrators can safely release emails flagged as potentially
  malicious from the virus quarantine queue, with detailed instructions and screenshots.
draft: true
params:
  author: Unknown
summary: The article explains a new feature that allows administrators to release
  emails from the virus quarantine queue, even if they are flagged as potentially
  malicious. It provides step-by-step instructions and screenshots for using this
  feature.
tags: null
title: Virus Email Release - For Administrators Only
---


Occasionally there are emails in the virus tab of the quarantine that users
want released, even though our AV filters have identified them as potentially
infected with malware.

Sometimes they are indeed infected and sometimes it's because of an overly
ambitious reach by one of our AV providers.

In cases where Administrators are confident the emails are safe and from
known, trusted senders, we have created a feature that allows Administrators
(and _only_ Administrators) to release an email from the virus tab of the
quarantine.

To begin the virus release the email must be selected from the virus tab of
the quarantine. When release is selected a warning pops up:

![Screen_Shot_2019-08-21_at_7.16.30_AM.png](screen_shot_2019-08-21_at_71630_am.png)

If you select Ok then the virus email is sent as in a password-protected zip
file as an attachment in an email that explains like this:

![Screen_Shot_2019-08-21_at_7.03.02_AM.png](screen_shot_2019-08-21_at_70302_am.png)

