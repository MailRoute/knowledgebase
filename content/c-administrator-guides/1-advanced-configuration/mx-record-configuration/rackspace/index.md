---
created_at: 2015-12-21 17:24:49
date: 2021-03-02 17:48:54
description: Learn how to add an MX record for your domain to set up email addresses
  and enable email delivery through Rackspace Cloud DNS. Step-by-step guide with instructions.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions on how to add an MX record
  for your domain to enable email delivery and reception using the Rackspace Cloud
  Control Panel. It explains the purpose of an MX record and the required fields to
  configure it correctly.
tags: null
title: Rackspace
---


## Add an MX Record

Use the Mail Exchange (MX) is a DNS record that points to the server that
handles your domain-related email delivery. You create an MX record for your
domain that allows you to set up an email address. For example, you can create
an MX record to create the email address user@yourdomain.com. You can send
email without setting up the MX record for your domain name, but you cannot
receive emails without it.

  1. [Log in](https://www.rackspace.com) to the **Cloud Control Panel at[Rackspace.com](https://www.rackspace.com).**
  2. Select **Networking** > **Cloud DNS**.
  3. Click the gear icon next to your domain and select **Add DNS Record.**
  4. In the popup dialog box, select **MX Record** as the record type.
  5. Enter the following information;

  * The hostname for your domain (optional).
  * **Mailserver Domai:** Add **_mail.mailroute.net_**.
  * **Priority:** The MX record priority is a setting you will use when your domain name uses more than one mail server. The priority that you set for your MX record affects the load sharing and the order in which multiple mail servers are used, and also allows the use of primary and backup mail servers.
  * **Time to live (TTL):** TTL refers to the time it will take for your computer to refresh DNS information. It is referred to in seconds of time.

6\. Click **Add Record**.

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

