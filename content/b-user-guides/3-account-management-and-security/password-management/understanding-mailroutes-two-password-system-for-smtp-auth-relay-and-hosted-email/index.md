---
created_at: 2024-07-12 18:06:47
date: 2024-09-04 20:06:43
description: Understand MailRoute's two-password approach for enhanced security -
  one for outbound email (SMTP) and another for inbound email (IMAP) servers. Learn
  how to access and reset these passwords.
draft: true
params:
  author: Unknown
summary: This article explains MailRoute's two-password system for SMTP Auth Relay
  and Hosted Email, detailing the security benefits and providing instructions for
  accessing and resetting the two separate passwords.
tags: null
title: Understanding MailRoute's Two-Password System for SMTP Auth Relay and Hosted
  Email
---


MailRoute uses separate passwords for Inbound and Outbound email servers.
While this may seem confusing at first, there are important security reasons
behind this approach.

## **Why Two Passwords?**

  1. **Enhanced Security** : Our Inbound (IMAP) and Outbound (SMTP) servers operate independently, running in separate clusters with passwords stored in different database tables and formats.
  2. **Future-Proofing** : The Inbound (IMAP) server password is identical to your MailRoute Control Panel login. This setup allows us to easily implement new authentication technologies like OAUTH, Multi-factor authentication, or Passkeys as email clients evolve.
  3. **Diverse Device Support** : Outbound servers often interact with devices having varied security requirements, such as scanners and fax machines, not just email clients.
  4. **Improved Security Management** : Separate passwords make it easier to prevent mail flow from compromised accounts without affecting your access to the MailRoute Control Panel.

By understanding and properly using these two passwords, you can ensure secure
and efficient email management through MailRoute.

## **Accessing Your Passwords**

###  **Outbound/SMTP Server Password** :

  1.     1.       1. Log in to the MailRoute Control Panel
      2. Click on **SMTP Auth Relay** in the left-side menu  
  
![Screenshot 2024-07-12 at 10.46.14.png](31286190335251.png)  
  

      3. Find your password in the **Outbound (SMTP) Server Configuration** section  
  
![Screenshot 2024-07-12 at 10.46.33.png](31286190335891.png)

      4. Click the "eye" icon to reveal the password ![Screenshot 2024-07-12 at 10.58.11.png](31286228382355.png) 
      5. Use the "copy" icon to copy it to your clipboard ![Screenshot 2024-07-12 at 10.57.46.png](31286228383891.png) 
      6. Enter that password into your email client to configure your Outbound/ (SMTP) Server Configuration

### **Inbound/IMAP Server Password:**

This is the same as your MailRoute Control Panel login password

If you've only accessed our Control Panel through a partner site, you may need
to set up a local password:

  1.     1.       1. Log in to the MailRoute Control Panel
      2. Click on **SMTP Auth Relay** in the left-side menu  
  
![Screenshot 2024-07-12 at 10.46.14.png](31286190335251.png)

      3. Find the **Outbound (SMTP) Server Configuration** section  
  
![Screenshot 2024-07-12 at 10.46.29.png](31286228384787.png)

      4. Click "Create your password"
      5. Follow the prompts to set up your password

### **Resetting your MailRoute Control Panel/Inbound (IMAP) Password:**

If you need to completely reset your MailRoute Control Panel and Inbound
(IMAP) Server Configuration password, you can do so

  1.     1. Visit <https://admin.mailroute.net/accounts/password_setup/#/>
    2. Enter your email address to receive an email with instructions to reset your password
    3. Use this new password for your Inbound/IMAP Server when configuring your email client

