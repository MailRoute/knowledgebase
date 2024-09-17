---
created_at: 2024-07-31 00:06:44
date: 2024-09-04 20:05:41
description: Detailed guide on configuring Microsoft Outlook for Windows 11 to use
  SMTP Auth Relay for sending emails, including steps to gather server details from
  MailRoute Control Panel and set up Outlook.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring Microsoft
  Outlook for Windows 11 to use SMTP Auth Relay for outbound email relay. It covers
  gathering the necessary information from the MailRoute Control Panel and configuring
  Outlook with the appropriate server settings.
tags: null
title: Microsoft Outlook for Windows 11 - Outbound Configuration/SMTP Auth Relay
---


# **TL;DR (Too Long, Didn't Read)**

Gather the info from our Control Panel by clicking the **SMTP Auth Relay** tab
on the left menu. You'll have to click the eye
icon![IMG_9731.jpeg](31863513129235.jpeg) to view your passwords. If you don't
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
  
![smtp-auth-full-screenshot.png](31863513130259.png)  
  

  3. Gather your info! You can click the copy icon ![IMG_3754.jpeg](31863481160339.jpeg) to copy the values of any field.  
  
For the Gmail webmail interface, you will only need the info in the **Outbound
(SMTP) Server** configuration.  
  
![smtp-auth-passwords-hidden.png](31863513133587.png)  
 **Outbound (SMTP) Server Password:** Click the eye icon
![IMG_9731.jpeg](31863513129235.jpeg) to display your password. Accept the
Terms of Service:  
  
![smtp-auth-tos.png](31863481164563.png)  
  
By the way, you can generate a new password for your **Outbound (SMTP)
Server** at any time.

  
**Configure your email client**

  1. Launch the Outlook application.  
  

  2. Click the **Settings** icon in the top menu bar of the application.  
  

  3. Select **Accounts** from the left hand menu and then then click **+Add account.**  
  

  4. Enter your email account in the **Suggested Accounts** field and press **Continue.  
  
**

  5. In the **Select your email provider** window, scroll down and click on **IMAP.  
  
**

  6. Enter the following information in the **IMAP** window:  
  
 **Password** : <Your Inbound (IMAP) password>  
  
 **IMAP Incoming server** : <Your Inbound (IMAP) Server>  
  
 **Port:** 993 (Please note this is different than in the MailRoute Control
Panel) - Outlook only supports using this port and SSL/TLS encryption)  
  
 **Secure connection type:** SSL/TLS (Recommended)  
  
 **SMTP username:** <Your Outbound (SMTP) Login>  
  
 **SMTP password:** <Your Outbound (SMTP) Password>  
  
 **Port:** 587  
  
 **Secure connection type:** SSL/TLS (Recommended)  
  
Then click **Continue.  
  
**

  7. In the **Sync your IMAP account** window, click **Continue.** You should see a **Success** windows congratulating you for your hard work.

## Using your new account to send email

When you compose a new email, you'll have a menu where the **From** address is
displayed. Click it and choose your new account from the popup menu.  
  

