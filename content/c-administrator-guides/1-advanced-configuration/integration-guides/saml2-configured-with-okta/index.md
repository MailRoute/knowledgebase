---
created_at: 2017-09-19 17:03:34
date: 2024-04-12 14:40:30
description: Detailed guide on setting up SAML2 authentication with OKTA identity
  provider for MailRoute, allowing seamless single sign-on for enhanced security and
  user convenience.
draft: true
params:
  author: Unknown
summary: The article provides step-by-step instructions for configuring SAML2 authentication
  with OKTA for the MailRoute service, enabling single sign-on (SSO) capabilities
  for users.
tags: null
title: 'SAML2 Configured with OKTA '
---


SAML2 or Security Assertion Markup Language 2.0 is a standard for exchanging
authentication and authorization data between security domains. It enables
cross-domain single sign-on (SSO) by distributing authentication tokens to
users.

For the security and convenience of our customers, MailRoute supports SAML2
compatible providers as external authentication for single sign-on capability.

There are two separate sites to set up single sign-on: the service provider
configuration, done in the MailRoute Control Panel, and the identity provider
configuration done within your SSO system.

### To setup with Okta

1\. Login to Okta and select **Applications** menu.

2\. Click " **Create App Integration** ".

![Screenshot_2021-05-14_at_17.10.36.png](screenshot_2021-05-14_at_171036.png)

3\. Select **SAML 2.0**.

![Screenshot_2021-05-14_at_17.11.21.png](screenshot_2021-05-14_at_171121.png)

4\. Enter the name for you application. Click Next.

![Screenshot_2021-05-14_at_17.11.44.png](screenshot_2021-05-14_at_171144.png)

5\. Fill in the following settings:

  * **Single sign on URL** : https://admin.mailroute.net/saml2/acs/
  * **Audience URI (Entity ID)** : https://admin.mailroute.net/saml2/metadata/
  * **Application username** : choose "Email" 

![Screenshot_2021-05-14_at_17.13.30.png](screenshot_2021-05-14_at_171330.png)

Click next.

6\. Choose " **I'm an Okta customer adding an internal app** " and click
**Finish.** Do not close this page, we will need to copy some of these
settings in the following steps.

### Configuring SAML in MailRoute's Control Panel

1\. Login to your Admin account in MailRoute's Control Panel.

2\. Select **External Authentication** from the left-hand side tab

3\. Select the toggle, **Choose External Auth Type** and switch to **SAML2**

In **filling in your Provider Settings** , please do the following:

![Screenshot_2021-05-14_at_16.51.53.png](screenshot_2021-05-14_at_165153.png)

1\. Click the **Enabled** box

2\. **Entity ID:** Please enter the **Identity Provider Issuer** from your
Okta app page.

3\. **Metadata URL:** Copy **Identity Provider metadata** from your Okta app
page.

![Screenshot_2021-05-14_at_17.16.32.png](screenshot_2021-05-14_at_171632.png)

To obtain **Identity Provider Issuer** click on **View Setup Instructions** in
your Okta application:

![Screenshot_2021-05-14_at_17.18.03.png](screenshot_2021-05-14_at_171803.png)

