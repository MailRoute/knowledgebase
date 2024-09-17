---
created_at: 2022-05-05 13:44:39
date: 2024-09-04 20:08:41
description: Detailed guide on configuring the Windows 10 Mail app to use MailRoute's
  SMTP Auth Relay service for outbound email, including retrieving credentials and
  step-by-step setup instructions.
draft: true
params:
  author: Unknown
summary: This article provides step-by-step instructions for configuring the outbound
  (SMTP) email settings in the Windows 10 Mail app to use MailRoute's SMTP Auth Relay
  service for sending emails. It explains how to gather the necessary credentials
  from the MailRoute Control Panel and enter them in the Mail app's settings.
tags: null
title: 'Microsoft Windows 10 Mail App Outbound Configuration/SMTP Auth Relay '
---


_*this configuration only apply if you are using the **default Mail App**
included with Windows **10 and later**_

# **TLDR; (Too Long, Didn't Read)**

Gather the info from our Control Panel by clicking the **SMTP Auth Relay** tab
on the left menu. You'll have to click the eye
icon![IMG_9731.jpeg](23865407037843.jpeg) to view your passwords. If you don't
have a local password set up, you'll be asked to create one. The **Inbound
(IMAP)** and **Outbound (SMTP)** servers may have different logins and will
have different passwords. Go into your **Mail** app and add a new account
email account using this info.

When you send email, click the **From** address to choose your new account for
sending email. It'll pass SPF, DKIM, DMARC checks. Congratulations!

# **Long Version**

# Gather the info you need to configure your email client

To configure your email client to use the MailRoute SMTP Auth Relay service
for outbound email relay, you will need to gather some info from the MailRoute
Control Panel and then configure your email client.

  1. Login to admin.mailroute.net and click the My Settings link at the top of the page.  
  

  2. Click the SMTP Auth Relay tab in the Settings menu on the left side of the page.   
  
![smtp-auth-full-screenshot.png](27082714874515.png)  
  

  3. Gather your info! You can click the copy icon ![IMG_3754.jpeg](23865415715475.jpeg) to copy the values of any field.  
  
For the Gmail webmail interface, you will only need the info in the **Outbound
(SMTP) Server** configuration.  
  
![smtp-auth-passwords-hidden.png](27082714904339.png)  
 **Outbound (SMTP) Server Password:** Click the eye icon
![IMG_9731.jpeg](23865407037843.jpeg) to display your password. Accept the
Terms of Service:  
  
![smtp-auth-tos.png](27082714912659.png)  
  
By the way, you can generate a new password for your **Outbound (SMTP)
Server** at any time.

  
**Configure your email client**

  1. Select **Start** , enter **Mail** , and choose the app from the results  

  2. If this is the first time you've opened the Mail app, you’ll see a Welcome page. Select **Add account** to get started.

If you've used the Mail app before, at the bottom of the left navigation pane,
select **Settings** icon, and then choose **Manage Accounts  
  
**

  3. Select **Advanced setup** from the **Choose an account** window in Step 2 above. The Advanced setup option is the last option on the list, and you may have to scroll to see it.  
  

  4. Enter the following information in the **Advanced setup window**.  
  
 **Email address:** This is the email address you're adding for SMTP Auth
services

  
**User name** : <Your Inbound (IMAP) login>  
  
 **Password** : <Your Inbound (IMAP) password>  
  
 **Account Name** : This is the name you'll see in the left pane of the Mail
app and in the Manage Accounts pane. You can choose any name you want.  
  
 **Send your messages using this name:** Enter the name you want recipients to
see when they receive your message.  
 **  
Inbound Account type:** IMAP4  
 **  
Incoming email server** : <Your Inbound (IMAP) Server>  
 **  
IMAP Encryption** : TLS

**Outgoing (SMTP) email server** : This is your server name, a colon, and the
port.  
So you'e going to enter:  
<Your Outbound (SMTP) Server> **:** <Your Outbound (SMTP) Port>  
That's going to be something like **smtpauth.mailroute.net:587  
** Don't forget the colon between the two parts! **  
  
Outgoing server requires authentication** : selected  
  
 **User name:** <Your Outbound (SMTP) Login>  
  
 **Password:** <Your Outbound (SMTP) Password>  
  
 **SMTP Encryption:** STARTTLS

