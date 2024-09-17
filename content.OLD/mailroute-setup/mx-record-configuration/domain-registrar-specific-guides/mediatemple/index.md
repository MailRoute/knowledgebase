---
created_at: 2015-06-12 16:09:57
date: 2021-03-02 17:48:54
description: Detailed instructions on configuring MX records in the MediaTemple account
  manager to change your domain's email routing to MailRoute for improved email delivery.
draft: true
params:
  author: Unknown
summary: The article provides a step-by-step guide on how to configure MX records
  for MediaTemple's hosting service to route email through MailRoute's email service.
tags: null
title: MediaTemple
---


**Step 1**. **[Login](https://mediatemple.net)** to your **account manager**
at **MediaTemple.net**.  
 **Step 2**. Click on your domain that you want to change the DNS settings
for.  
 **Step 3**. Scroll to the bottom in the **DNS & Zone File** box and click on
**Edit DNS Zone File**.  
 **Step 4.** In the **Edit Zone File** page, scroll down and click on the
**delete checkbox** **for any preexisting MX records**.

**Step 5.** Click on **\+ Add a record**. Insert **_10_** **
_mail.mailroute.net._** Remember to **include the dot** at the end and make
sure the **type is set to MX** in the drop-down if this is still required).

**Step 6**. Verify all the wording (remember it takes 24-48 hours to be fully
functional) and click **Save**.

**Step 7.** **MediaTemple** will prompt you that since the MX record no longer
uses their internal server that they've disable email for your domain.

**Step 8.** Return to the **account manager** page by clicking your domain
near the top of the page.

**Step 9.** In the **Email box** and click on **Enable/Disable Mail**.

**Step 10.** Click the **Enable** radio button for your disabled domain.

**Step 11**. Click **Save**.  
  
 **NOTE:** If you have entered the records correctly, you should see the the
row has turned green.

*MailRoute thanks user **Mike M**. for giving us updated information to share with other MediaTemple users!

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

