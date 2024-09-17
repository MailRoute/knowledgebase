---
created_at: 2014-07-22 21:26:45
date: 2021-03-02 17:48:54
description: Learn how to update your MX records in the HostMonster control panel
  to route emails through Mailroute's secure mail servers, with clear steps for DNS
  Zone Editor and cPanel configuration.
draft: true
params:
  author: Unknown
summary: This article provides step-by-step instructions for modifying MX records
  in the HostMonster control panel to point to Mailroute's mail servers, ensuring
  proper email delivery.
tags: null
title: HostMonster
---


**Note:** These changes may take up to 4-8 hours to apply.

### Modifying an MX Entry:

  1. Login to your [HostMonster](http://www.HostMonster.com/cgi-bin/cplogin) Control Panel.

  2. Select the **"DNS Zone Editor"** icon in the **Domains** section.

  3. Select the domain you're modifying from the drop-down box.

  4. Scroll down to the heading named **"Add DNS Record" (Be sure to copy and save your existing mx records for your record prior to changing them)  
**

    * In the **"Host Record"** field, enter the domain you're modifying. In most cases, you'll simply type your domain name here, without www.

    * Leave the **"TTL"** field at it's default setting

    * Select **"MX"** from the drop-down box labelled **"Type"**

    * In the **"Points To"** field, enter **mail.mailroute.net**

    * The **"Priority"** field dictates the order in which the MX entries are applied. Set to **10**.

  5. Select **"Add Record"** to finish the process.

**Update Your Mail Exchanger:**

    1. From your cPanel, go to the **MX entry** icon.
    2. Choose your domain from the drop down box that you are wanting to change the MX settings on
    3. Scroll down to **MX (Mail Exchanger)** and click the **more** link to expand the section.
    4. Choose **Local Mail Exchanger**.
    5. Click **Change**

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

