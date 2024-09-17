---
created_at: 2017-02-15 18:36:08
date: 2023-08-04 18:18:08
description: Learn how to automatically add or block email addresses to your domain's
  Allow and Block lists using a simple script that interacts with the MailRoute API,
  eliminating manual admin panel access.
draft: true
params:
  author: Unknown
summary: The article provides a script that allows users to automatically add or block
  email addresses to their domain's Allow and Block lists using the MailRoute API,
  eliminating the need to log in to the admin panel. It also includes instructions
  on how to obtain the required API credentials.
tags: null
title: 'Allow / Block Script '
---


Automatically add to your domain's Allow and Block lists via our API with this
simple script.

This eliminates the need to login to admin.mailroute.net to add to Allow or
Block for your domain.

Remember that you can always use our API for account management. You can
perform any admin function either through our interface or directly through
the API. Contact [support@mailroute.net](mailto:support@mailroute.net) with
questions.

**Step 1**

Receive API Credentials

You'll only need to do this step one time.

Login to your MailRoute account via the admin.mailroute.net control panel.
Click your name at the top of the screen and choose "Settings". Under "API
Access", next to "API Key" click the link marked “Show”.

**Step 2**

Add the script via Terminal

Open Terminal and paste this code into the window:

    
    
    curl -s --dump-header - -X POST \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <api_user>:<api_key>' \
        --data ' {
    	  "email_account":"/api/v1/email_account/z4@usercase.com/",
    	  "wb" : "B",
    	  "email" : "block.me"
        }' \
        https://admin.mailroute.net/api/v1/wblist/
    

This query will add block.me domain to z4@usercase.com’s block list.

All admin functions can be performed either through our interface or directly
through the API. Contact [support@mailroute.net](mailto:support@mailroute.net)
for more information or view our API libraries at
[github.com/mailroute](https://github.com/mailroute).

Thanks for using MailRoute! We value your business.

888.485.7726

