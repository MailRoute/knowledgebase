---
created_at: 2022-04-15 20:45:12
date: 2024-09-04 20:08:15
description: Learn about MailRoute's SMTPAuth Relay service, which enables email clients
  to authenticate and relay outbound email through MailRoute's servers, ensuring proper
  email authentication and delivery.
draft: true
params:
  author: Unknown
summary: The article provides information about MailRoute's SMTPAuth Relay service,
  which allows email clients to relay outbound email through MailRoute's servers.
  It explains the features, configurations, and terms of use for this service.
tags: null
title: MailRoute SMTP Auth Relay for Outbound Email - General Information
---


The MailRoute SMTPAuth Relay service is a optional service that allows SMTP-
Auth based relay from email clients through the MailRoute outbound email
servers. Authentication to the MailRoute SMTPAuth Relay service is via a login
and password combination, rather than based on an IP address, like our
standard Outbound Email Relay Service.

Our typical customer relays email out through their own server. Their server
connects to the MailRoute outbound service and is authenticated by its IP
address. The server can then relay email for all the users in their domain, as
long as they are listed in the MailRoute Control Panel.

Email Clients using the SMTPAuth Relay service will have their outbound mail
relay out through MailRoute rather than through their corporate email server.
This is intended for very specific uses. Most of the time you'll want your own
mailserver to process your own email, so that email local to your company
stays within your own mailserver. But in some special cases, the ability for a
client to relay email directly out through MailRoute is important.

## SMTPAuth Relay Features

Outbound email relays directly from an email client to MailRoute servers for
delivery, and those emails will pass SPF, DKIM, and DMARC checks.

Authentication is not restricted by IP, but by Login and Password.

Users of our Managed Email Membership Service, who benefit from MailRoute
filtering and forwarding to their other email accounts may use the SMTPAuth
Relay service to send email out from their affiliate domain. For example, a
user@acm.org can now send email that comes directly from their
[a](mailto:user@acm.com,)cm.org[ ](mailto:user@acm.com)address, and it will
pass all SPF, DKIM, and DMARC checks.

## What Addresses May Relay Email?

User's may only relay email that purports to come from their own email
account. The email's SMTP Envelope must match their SMTP Auth Login, or one of
their own aliases to be permitted to relay.

For example, imagine that you have a domain, "example.org", and it has a
domain alias "example.net". And imagine you have a user "alice" who has an
alias "alias_lastname". The user could send email from

  * [alice@example.org](mailto:alice@example.org)
  * [alice@example.net](mailto:alice@example.net)
  * [alice_lastname@example.org](mailto:alice_lastname@example.org)
  * [alice_lastname@example.net](mailto:alice_lastname@example.net)

The user could not use the MailRoute SMTP Auth Relay to send email for their
personal "alice_lastname@gmail.com" address.

#### **Why is this?**

Well, we can't have users who impersonate other users.
[alice@example.org](mailto:alice@example.org) shouldn't be able to send email
that claims to be from [bob@example.org](mailto:bob@example.org).

And we can't be sending email from other domains - it will violate SPF checks,
DMARC will fail. Not only will it harm the sending domain's reputation, but
any reliable email provider will block the email because of those failures.

## End-User Responsibilities

Users of the SMTPAuth Relay Service must agree to the MailRoute Terms and
Conditions as posted at <https://mailroute.net/pages/legal>

Users must also acknowledge agreement with the following terms for usage of
the SMTPAuth Relay Service:

  * I understand that outbound services are for general corporate, business, and personal email only
  * I agree to not use this outbound email service for bulk or transactional email, or to send any sort of spam or unsolicited email.
  * I understand that outbound email is subject to a per-user sending quota to prevent abuse and to minimize accidental misuse of the systems.
  * I agree that outbound email services may be temporarily or permanently blocked or disabled without notice in the event that sending quotas are exceeded or misuse of the service is detected.
  * I agree to abide by the general [MailRoute Terms and Conditions](https://mailroute.net/pages/legal)

Information on configuring the SMTPAuth Relay service for different email
accounts may be found [here](https://support.mailroute.net/hc/en-
us/sections/5551581660819-Configuring-Email-Client-Software-for-the-MailRoute-
SMTP-Auth-Service)

