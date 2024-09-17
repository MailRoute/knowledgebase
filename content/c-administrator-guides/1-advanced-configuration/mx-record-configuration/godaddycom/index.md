---
created_at: 2013-05-30 01:23:45
date: 2021-03-02 17:48:54
description: Detailed guide on how to change MX records in GoDaddy control panel to
  use MailRoute email services. Covers both card and list view interfaces with screenshots.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for updating the MX records
  on GoDaddy to point to the mail.mailroute.net mail server. It covers the process
  for both the card view and list view interfaces.
tags: null
title: GoDaddy.com
---


## MX Records: GoDaddy.com

  1. [Log in](https://www.godaddy.com) to your [GoDaddy](https://www.godaddy.com) account.
  2. Next to **Domains** , click **Manage**.

How you access the DNS manager will depend on the view of your account:

**_A. Card View:_**

**_![cardviewmaster.jpg](.jpeg)_**

1\. Select the domain name you want to use, click the **Settings icon** and
select **Manage DNS**.

2\. On the **Records** list, next to **MX** , click the **Pencil icon** and
edit any of the following fields:

  * **Host:** Enter the domain name or subdomain for the MX record. For example, type **@** to map the record directly to your domain name, or enter the subdomain of your host name, such as **www** or **ftp**.
  * **Value** : Enter the mail server's address; **_mail.mailroute.net_**
  * **Priority _:_** Enter, or select the priority you want to assign to the mail server.
  * **TTL _—_** set the value to 1 Hour.

3\. Click **Save** when finished.

**_B. List View:_**

**_![listviewmaster.jpg](.jpeg)_**

  1. Click on the domain name you want to use.
  2. Select the **DNS Zone File** tab.
  3. Click **Edit** : 

![editicon.jpg](.jpeg)

4\. On the **Records** list, next to MX, click the **Pencil icon** and edit
any of the following fields:

    * **Host:** Enter the domain name or subdomain for the MX record. For example, type **@** to map the record directly to your domain name, or enter the subdomain of your host name, such as **www** or **ftp**.
    * **Points to:** Enter the mail server's address; **_mail.mailroute.net_**
    * **Priority:** Enter, or select the priority you want to assign to the mail server.
    * **TTL:** — set the value to 1 Hour.

5\. Click **Save** when finished.

**[Source](Source%20Link%20from%20GoDaddy):
<https://www.godaddy.com/help/change-an-mx-record-19235>

[Start a free 30-day trial today. ](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

