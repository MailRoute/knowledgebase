---
created_at: 2024-05-17 18:36:49
date: 2024-09-04 20:07:55
description: Detailed guide on configuring Microsoft Outlook for Mac to use a separate
  SMTP Auth Relay account for outbound email relay, ensuring emails pass SPF, DKIM,
  and DMARC authentication checks.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring Microsoft
  Outlook for Mac to use a separate SMTP Auth Relay account for outbound email, allowing
  users to send emails that pass SPF, DKIM, and DMARC checks.
tags: null
title: 'Microsoft Outlook for Mac - Outbound Configuration/SMTP Auth Relay '
---


  
To simplify the use of your SMTP Auth Relay, we recommend creating a separate
account in your Mac Outlook email client. This separate account has both an
IMAP and SMTP server.  
  
If you are a user of the **MailRoute Managed Email Membership Service (MEMS)**
(such as a member of a professional organization or alumni group) and using
only the MEMS email forwarding service, the IMAP account will **not** store
any of your email - it will be forwarded appropriately.  
  
Users of the **MailRoute Hosted Email Service** have full IMAP mailbox and
storage capabilities.

#  **TLDR** **;** **(Too Long, Didn't Read)**

Gather the info from our Control Panel by clicking the **SMTP Auth Relay** tab
on the left menu. You'll have to click the eye
icon![IMG_9731.jpeg](29479479846035.jpeg) to view your passwords. If you don't
have a local password set up, you'll be asked to create one. The **Inbound
(IMAP)** and **Outbound (SMTP)** servers may have different logins and will
have different passwords. Go into your Outlook app, add a new account using
those settings.

When you send email, click the **From** address to choose your new account for
sending email. It'll pass SPF, DKIM, DMARC checks. Congratulations!

# **Long Version**

# Gather the info you need to configure your email client

To configure your email client to use the MailRoute SMTP Auth Relay service
for outbound email relay, you will need to gather some info from the MailRoute
Control Panel and then configure your email client.

  1. Login to admin.mailroute.net and click the My Settings link at the top of the page.  
  

  2. Click the SMTP Auth Relay tab in the Settings menu on the left side of the page.   
  
![smtp-auth-full-screenshot.png](29479491596179.png)  
  

  3. Gather your info! You can click the copy icon ![IMG_3754.jpeg](29479479855635.jpeg) to copy the values of any field.  
  
There are separate **Inbound (IMAP) Server** and **Outbound (SMTP) Server**
configurations. You'll need both:  
  
![smtp-auth-passwords-hidden.png](29479479859475.png)  
 **Inbound (IMAP) Server Password** : Click the eye icon
![IMG_9731.jpeg](29479479846035.jpeg) to display your password . If you
haven't set a local MailRoute password yet, you will be prompted to do so.
Your **Inbound (IMAP) Server** password may be the same as your Control Panel
login password. You'll be shown this, if this is the case.  
  
![smtp-auth-password.png](29479491602323.png)  
  
 **Outbound (SMTP) Server Password:** Click the eye icon
![IMG_9731.jpeg](29479479846035.jpeg) to display your password. Accept the
Terms of Service:  
  
![smtp-auth-tos.png](29479479865875.png)  
  
By the way, you can generate a new password for your **Outbound (SMTP)
Server** at any time.

  
**Configure your email client**

      1. Open the Outlook email client on your Macintosh.  
  

      2. Choose **Settings** from the **Outlook** menu in your menu bar. We're going to add a new mail account to your email client. 
      3. Choose **Accounts** from the icons at the top, and then press the **+** icon at the bottom left of the window to add a new account:![Image](29479491609619.png) 
      4. Choose **Add Email Account  
![Image](29479491610899.png)**

      5. Enter your email account in the **Email Address** field, and then click **Continue:**![Image](29479491612179.png) 
      6. In the **Choose Provider** dialog **,** select **IMAP:**![Image](29479479880595.png) 
      7. Now we're finally going to get to set all the final settings for your account!   
  
In the **Add Account** window, you can enter your **Email Address** , your
**IMAP Username** , **IMAP Password** , **IMAP Incoming Server** , **SMTP Auth
Username** , **SMTP Auth passwword**. Chose **StartTLS** for both IMAP and
SMTP servers, with the ports you saved from the MailRoute Control Panel:  
  
![Image](29479491618707.png)  
  
Then click **Add Account**. You'll see a window showing that it was
successful: **![Image](29479479884307.png)**  
  

      8. Now you can close your **Settings/Accounts** window and use your account!

## Using your new account to send email

When you compose a new email, you'll have a menu where the **From** address is
displayed. Click it and choose your new account from the popup menu:  
  
  

