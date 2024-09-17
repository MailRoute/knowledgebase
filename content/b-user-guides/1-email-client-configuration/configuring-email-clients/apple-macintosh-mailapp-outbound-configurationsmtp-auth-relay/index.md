---
created_at: 2022-04-11 21:32:30
date: 2024-09-04 20:05:15
description: Detailed guide on configuring Apple Mail app to use MailRoute SMTP Auth
  Relay for outbound email, including steps to gather server info from Control Panel
  and set up a new email account with proper IMAP and SMTP server details.
draft: true
params:
  author: Unknown
summary: This article provides step-by-step instructions for configuring the Apple
  Mail app to use the MailRoute SMTP Auth Relay service for outbound email relay.
  It covers gathering the necessary information from the MailRoute Control Panel and
  setting up a new email account in Mail with the correct server settings.
tags: null
title: 'Apple Macintosh Mail.app Outbound Configuration/SMTP Auth Relay '
---


  
To simplify the use of your SMTP Auth Relay, we recommend creating a separate
account in your Mac Mail.app email client. This separate account has both an
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
icon![IMG_9731.jpeg](23490085152915.jpeg) to view your passwords. If you don't
have a local password set up, you'll be asked to create one. The **Inbound
(IMAP)** and **Outbound (SMTP)** servers may have different logins and will
have different passwords. Go into your Mail.app, add a new account using those
settings.

When you send email, click the **From** address to choose your new account for
sending email. It'll pass SPF, DKIM, DMARC checks. Congratulations!

# **Long Version**

# Gather the info you need to configure your email client

To configure your email client to use the MailRoute SMTP Auth Relay service
for outbound email relay, you will need to gather some info from the MailRoute
Control Panel and then configure your email client.

  1. Login to admin.mailroute.net and click the My Settings link at the top of the page.  
  

  2. Click the SMTP Auth Relay tab in the Settings menu on the left side of the page.   
  
![smtp-auth-full-screenshot.png](27024643009939.png)  
  

  3. Gather your info! You can click the copy icon ![IMG_3754.jpeg](23490046731923.jpeg) to copy the values of any field.  
  
There are separate **Inbound (IMAP) Server** and **Outbound (SMTP) Server**
configurations. You'll need both:  
  
![smtp-auth-passwords-hidden.png](27045061038355.png)  
 **Inbound (IMAP) Server Password** : Click the eye icon
![IMG_9731.jpeg](23490085152915.jpeg) to display your password . If you
haven't set a local MailRoute password yet, you will be prompted to do so.
Your **Inbound (IMAP) Server** password may be the same as your Control Panel
login password. You'll be shown this, if this is the case.  
  
![smtp-auth-password.png](27045045287699.png)  
  
 **Outbound (SMTP) Server Password:** Click the eye icon
![IMG_9731.jpeg](23490085152915.jpeg) to display your password. Accept the
Terms of Service:  
  
![smtp-auth-tos.png](27045061096339.png)  
  
By the way, you can generate a new password for your **Outbound (SMTP)
Server** at any time.

  
**Configure your email client**

      1. Open the Mail.app email client on your Macintosh.  
  

      2. Choose **Settings** from the **Mail** menu in your menu bar. We're going to add a new mail account to your email client. This is going to feel a little more complicated than it should be. The Apple Mail client tries to guess your settings, and warns you when it can't, so you have to go through a few windows to get to the screen where you're going to actually configure everything properly.  
  

      3. Choose **Accounts** from the icons at the top, and then press the **+** icon at the bottom left of the window to add a new account:![smtp-auth-mail-accounts-main-1.PNG](27045045314067.png) 
      4. Choose **Other Mail Account...** and click **Continue** from the dialog box:  
![smtp-auth-mail-accounts-choose-provider-2.PNG](27045045322771.png)

      5. In the **Add a Mail Account** dialog **,** pick a descriptive name for this new mail account. I used **ACM Outbound Email** Account. **** Enter your ACM email account, and your **Inbound (IMAP) Server** password.  
 **![smtp-auth-mail-add-mailaccount-3.PNG](27045061134227.png)**  
Click **Sign In** and be ready for it to open a new dialog with a warning at
the bottom of **Unable to verify account name or password**. This is expected.  
  

      6. The email address you entered in the previous window should be displayed. Make sure the **Account Type** is set to **IMAP** , and set the **Incoming Mail Server** and **Outgoing Mail Server** to the values you noted before. Click the **Sign In** button. You'll see the dialog refresh with another **Unable to verify account name or password**. This is expected. Click **Next:** **  
![smtp-auth-mail-add-mailaccount-4.PNG](27045061147411.png)  
**

      7. Another dialog pops up, just click **Done:  
  
![smtp-auth-mail-select-apps.png](27045045416595.png)  
  
**

      8. Now we're finally going to get to set all the final settings for your account!   
  
Select your new account from the list of accounts, and choose **Server
Settings** from the tabs at the top. Here's where you'll enter all the proper
information to configure your account.  
  
 **Incoming Mail Server (IMAP)  
** **User Name:** enter your **Inbound (IMAP) Login**  
 **Password:** enter your **Inbound (IMAP) Password  
** **Host Name:** enter your **Inbound (IMAP) Server Name**  
 **  
Outbound Mail Server (SMTP)  
** **User Name:** enter your **Outbound (SMTP) Login**  
 **Password:** enter your **Outbound (SMTP) Password  
** **Host Name:** enter your **Outbound (SMTP) Server Name**  
  
Then click **Save**  
![smtp-auth-mail-add-mailaccount-5.PNG](27045061159315.png)  
  

      9. Now you can close your **Settings/Accounts** window and use your account!

## Using your new account to send email

When you compose a new email, you'll have a menu where the **From** address is
displayed. Click it and choose your new account from the popup menu:  
  
![smtp-auth-mail-from.png](27045352947859.png)

