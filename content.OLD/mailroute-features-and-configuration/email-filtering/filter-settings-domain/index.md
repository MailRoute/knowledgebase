---
created_at: 2016-12-21 18:27:06
date: 2024-04-12 14:40:30
description: Learn how to configure email content filtering settings for your domain,
  including spam, phishing, virus, message size, banned file types, and preferred
  language filters. Customize filters to suit your needs.
draft: true
params:
  author: Unknown
summary: The article discusses various email content filtering settings available
  to administrators, including spam, phishing, virus, message size, and banned file
  types filters, as well as preferred language settings. It provides an overview of
  the different options and customization possibilities for each filter.
tags: null
title: 'Filter Settings: Domain'
---


## Content Filter Settings Domain-wide

The Administrator can select default settings for the entire domain. If the
settings for a particular mailbox are not deliberately selected and modified,
it will use these settings.

### **Spam Filter Settings**

The **Anti-Spam** filter settings have the most options. You can choose from
various presets for filtering, or customize your own, with any level of
granularity.

Messages that are spammy can be delivered with their subject lines rewritten.
Spam messages can be quarantined. And you can choose the score at which each
of those happens. Our standard setting quarantines mail at a score of 7.0. But
you might want to make this number higher or smaller, or add the option to
rewrite the subject. It's entirely in your control. Adjust the score, but
remember: it's a balancing act between catching spam and false positives.

![Screen_Shot_2018-04-20_at_1.00.38_PM.png](screen_shot_2018-04-20_at_10038_pm.png)

### **Anti-Phishing Filter Settings**

Adjust filters to increase scoring rules of phishing emails. 'Normal' is our
standard weighted setting. 'High' and 'Extreme' increase the sensitivity of
the filters. Keep in mind, increasing the filter sensitivity will cause an
increase of false-positives.

To report any phishing emails that have come through the filters, attach a
copy of the original email body and header to
[phishing@mailroute.net](mailto:phishing@mailroute.net) or paste the original
email body and header in the space provided and click submit.

![anti-phishing.png](anti-phishing.png)

###

### **Anti-Virus Filter Settings**

Your options for virus-infected emails are much simpler: Do you want to be
notified when a virus-infected message is quarantined?

![Screen_Shot_2018-04-20_at_1.01.39_PM.png](screen_shot_2018-04-20_at_10139_pm.png)

### **Message-Size Filter Settings**

You can opt to reduce the maximum allowed message size for your email. Our
**maximum** is **150MB**.

![Screen_Shot_2018-04-20_at_1.02.00_PM.png](screen_shot_2018-04-20_at_10200_pm.png)

### **Banned File Types Filter Settings**

**Banned File Types** are messages that contain various types of dangerous
enclosures. The standard filetypes blocked by this filter include: .bat, .cmd,
.com, .cpl, .dll, .exe, .pif, .scr, .rar, and .vbs.

These restrictions apply to files embedded inside other files, like **zip** or
**tar** files too.

Besides quarantining these emails and deciding if you want a notification, you
can allow them to be delivered. You can even set a " **plus extension** " for
delivery, so you can have the message delivered to a variant of your email
address, like **user+banned** @domain.com Some people like to use this to
support client-side filtering.

![Screen_Shot_2018-04-20_at_1.02.16_PM.png](screen_shot_2018-04-20_at_10216_pm.png)

** Preferred Languages** ****

When a message comes in, we try to classify the language used in the body of
the message. This isn't always possible - it could be too short, or ambiguous,
or it might be encoded in some fashion. But we are able to identify it a good
portion of the time.

"Preferred Languages" lets you specify the languages you prefer to accept -
languages not in your list will have a penalty applied to them, causing the to
score higher, and to be more like to enter, or be guaranteed to enter the
quarantine.

The default setting is to allow All
languages:![preferred_language_1.png](preferred_language_1.png)

If you delete the "All" entry from the list by clicking the small x next to
it, then you can choose specific languages you prefer:

The default penalty for a message with an identified language that does not
match your personal list, is 5 points. You can increase or decrease this to
whatever you prefer. Picking a number substantially higher than your
quarantine cutoff point (default is 7.0) will make sure those messages go to
the quarantine, unless they are overridden by an allow list entry.

![preferred_language.png](preferred_language.png)

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

