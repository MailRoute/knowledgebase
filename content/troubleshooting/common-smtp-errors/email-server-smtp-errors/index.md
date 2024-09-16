---
created_at: 2021-01-21 17:57:08
date: 2024-07-15 21:40:28
description: A detailed guide covering common SMTP error codes, their meanings, and
  step-by-step solutions to fix email delivery issues, from server errors to policy
  rejections and authentication problems.
draft: true
params:
  author: Unknown
summary: This article provides a comprehensive list of common SMTP error codes encountered
  when sending emails, along with explanations and solutions for troubleshooting each
  error. It serves as a handy reference for diagnosing and resolving email delivery
  issues.
tags: null
title: Email Server SMTP Errors
---


To assist in troubleshooting commonly seen email server errors we have created
a list of error codes and next steps to fix the issue.

421 Unexpected failure, please try later:

Error on the email server's side. We typically will hold mail to try to relay
it to the server, but it can't go through because every attempt receives this
error.

Solution: check your mailserver logs for errors indicating the cause

450 4.7.1 <[user@domain.com](mailto:hollidays@slmclaw.com)<mailto:
user[@domain.com](mailto:hollidays@slmclaw.com)>>: Recipient address rejected:
Policy Rejection- Greylisting challenge offered:

Legitimate and well-configured mailservers will automatically retry shortly,
and mail will go through.

Solution: It’s a “450” error - that’s a temporary deferral. The server
shouldn’t be returning the email to the sender. It should be retrying.

450\. Requested mail action not taken: mailbox unavailable. SMTP server could
not access a mailbox to deliver your message:

This could be caused by a process on the remote server tidying up the mailbox,
or the remote mailbox could be corrupt, or the remote mailbox may be stored on
another server which is currently offline, or the network connection went down
while sending, or the remote mail server does not want to accept mail from
your server for some reason (IP address, blocklisting, etc..). The next
attempt to send by your server may prove successful.

452 4.3.1 Insufficient system resources:

This is usually indicative of insufficient diskspace - if not on the volume
that actually holds the mailstore (mail partition), then on a different volume
that holds logging data (partition on which logs are kept).

Solution: Clear diskspace. Check out this blog posting - it talks about
backpressure settings on MS Exchange servers:

<http://exchangepedia.com/2007/03/exchange-
server-2007-transport-452-4-3-1-insufficient-system-resources.html>

550 Error - SMTP Authentication error:

If you're using Cpanel you need to click the check box for your server to
accept the mail for your domain.

Solution: If you're using cPanel, take a look at Step 4 in this article in our
KB. [https://support.mailroute.net/hc/en-us/articles/224059348-cPanel
](https://support.mailroute.net/hc/en-us/articles/224059348-cPanel)

You will be looking for the Mail Exchanger section which will give you the
options of Auto-Detect, Remote and Local. You need to select **Local** then
click Change. Once that is done, log out of the DNS cPanel and log back in to
make sure that Local is still selected.

And be sure to check your cpanel settings on the server as well, of course.

If you're not using cPanel, take a look at your email server configuration. It
needs to know that it's the authoritative server for your domain.

550-not permitted to relay through this server.

Solution: Please turn on SMTP Authentication in your mail client, or login to
the 550-IMAP/POP3 server before sending your message.

550-5-7-1 in o365:

This error occurs when the recipient's domain has security or policy settings
that reject the sender's message. However, we were unable to determine the
specific setting that's causing this rejection. Usually the error is reported
by an email server outside of Office 365. Common issues include the following:
the receiving server suspects the message is malicious or spam; the Sender
Policy Framework (SPF) record for the domain is incorrectly configured or
doesn't exist; or the message includes an attachment larger than the receiving
server will accept. Try one or more of the following:

Solution: Review the reported error - Check the Reported error shown below to
help determine what the issue might be. For example, if the issue is related
to an SPF failure, the reported error will usually include the acronym "SPF"
or the phrase "Sender Policy Framework."

Correctly configure your SPF records - If you're the sender's email admin,
make sure your domain's SPF records at your domain registrar are properly
configured. Office 365 supports only one SPF record (a TXT record that defines
SPF) for your domain. Include the following domain name:
[spf.protection.outlook.com](http://spf.protection.outlook.com/). If you have
a hybrid configuration (some mailboxes in the cloud and some mailboxes on
premises) or if you're an Exchange Online Protection standalone customer, add
the outbound IP address of your on-premises servers to the TXT record. To
learn how, see Customize an SPF record to validate outbound email sent from
your domain (<https://technet.microsoft.com/en-
us/library/dn789058(v=exchg.150).aspx>) and External Domain Name System
records for Office 365 (<https://support.office.com/en-us/article/External-
Domain-Name-System-records-for-
Office-365-c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0#BKMK_SPFrecords>) .

[https://support.office.com/en-us/article/fix-email-delivery-issues-for-error-
code-550-5-7-1-in-office-365-da1ff375-f88f-4a3e-b81f-06cdb6ecae3c?ui=en-
US&rs=en-US&ad=US](https://support.office.com/en-us/article/fix-email-
delivery-issues-for-error-code-550-5-7-1-in-
office-365-da1ff375-f88f-4a3e-b81f-06cdb6ecae3c?ui=en-US&rs=en-US&ad=US)

550 5.7.1. Unable to relay:

If the Reported error indicates a problem with relaying (e.g. "unable to
relay"), then the email server that reported the error likely isn't set up
correctly to receive and relay messages from the sender's domain. This server
will usually be one of your on-premises servers in a hybrid environment, a
smart host email service that you're trying to route messages through, or
possibly even an email hosting service you used in the past yet still have
mail flow settings pointing to (e.g. your MX record at your domain registrar
still points to your previous email service provider). Check Error reported by
shown below to determine what domain, service, or server is reporting the
error. The email server needs to be configured to either accept messages from
anonymous users or to include the sending domain or IP in its list of
authenticated senders. On an Exchange server, you can set this up in the
server's receive connector. If it's a smart host managed by another service or
partner, contact the service or partner to configure their servers to accept
and relay messages from your senders. Also, work with your domain registrar to
make sure your MX records are properly configured.

Contact the recipient's email admin - For some scenarios, you can fix the
issue by contacting the email admin at the recipient domain to ask them to add
the sender's email address or your domain to their allowed senders list, or to
relax the setting that's causing the rejection.

For more information and tips for fixing this issue, see Fix email delivery
issues for error code 5.7.1 in Office 365
(<http://go.microsoft.com/fwlink/?LinkId=389365>) .

550 5.1. User Unknown error message:

All users need to be authenticated with Exchange

Solution: <https://bobcares.com/blog/how-to-fix-550-5-1-1-user-unknown-email-
error-in-exchange/2/>

General Information about SMTP Error Codes:

  * 250 – This SMTP server response simply means everything went well and your message was delivered to the recipient server.
  * 400XX– Are temporary errors
  * 500XX –Are generally bounce errors

