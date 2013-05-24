## MailRoute Service Upgrade

We are pleased to announce the release of a number of useful new features in the [MailRoute Control Panel](https://admin.mailroute.net).


#### Branding

Our Reseller partners and our larger customers now have the ability to brand or private-label the MailRoute interface.  They can choose new colors, replace the MailRoute logo with their own, and have email notifications sent from their own address.  MailRoute is dedicated to providing our partners and customers with the options and tools that will best allow them to support their users.

#### Import and Export Features

We've also completely redesigned the way user list imports are done.  Large lists (of over 100 entries) are now processed in the background, with an email notification upon completion.  

Import files can now contain not only email addresses and aliases, but also passwords, whitelist and blacklist entries, and all of our policy settings as well.

Since we don't believe in holding our customers hostage, we've made the import function export all your user data too.  You can download a list with all accounts, aliases, whitelist and blacklists, and all policy settings.

#### Quarantine Improvements

You can now blacklist a sender right from the Quarantine or Quarantine Message display.

Emails from Blacklisted senders now appear under their own tab in the quarantine.

#### Quarantine Notification Improvements

Users can now choose the time of day for their quarantine notifications to be sent.

We've added a "recover" link to the quarantine notifications too, so you can recover a message to your inbox without even having to login to the MailRoute Control Panel.

Blacklisted senders are no longer listed in nightly quarantine notifications.

#### Miscellaneous Improvements

We've made the MX record checks for domains more robust, and now we directly query all authoritative nameservers for a domain, and report on each.

We added "breadcrumbs" to help administrators move more quickly from a detail page to a parent's settings.  For example, you can jump from a user page, directly to a sub-tab on the domain page.  Our own administrators love this a lot!

We fixed an inconsistency with 7 and 8 character passwords.

API Keys are now available from a user profile page.  The "settings" link at the top right of the page takes a user to a page where they can reset their password or get their API key.  API Documentation is available in the [MailRoute Knowledgebase](https://support.mailroute.net/forums/21682281-API)



---
### Change Log

A full Change Log is available in the [MailRoute Knowledge](https://mailroute.zendesk.com/entries/23333072-MailRoute-Control-Panel-Change-Log)