
## MailRoute Control Panel - Change Log


2013-05-XX
* API - Added support for simplified URLs, providing access directly to specific domains and email accounts, reducing the number of API calls required to whitelist for a specific user, for example.  



2013-05-XX
* Feature - ActiveDirectory and LDAP Synchronization
* Quarantine Notification - made menu for time selection dynamic and based upon daylight savings time.
* Bug fix - fix case when whitelisting email from an empty sender
* Bug fix - fix error where user was unable to edit a blacklist entry.
* White/Blacklisting - allow white/blacklist to apply to both SMTP Envelope From sender as well as header From.




### 2013-04-11
* API - Add regenerate API key function to API.
* Fixed bug where whitelist email with empty domain could lead to incorrect whitelist entries.
* Quarantine whitelisting and blacklisting - made the "From" field displayed in Qtn grid and all notification dialogs consistent.  Previously, some showed the "From" contents from the header, while others showed the proper SMTP envelope email address.  Now we only display the SMTP envelope MAIL FROM address, since that is what actually needs to be white or blacklisted.
 
### 2013-04-09
* Quarantine - If subject is empty, user couldn't click on it to see the message!  We now set empty subjects to "<none>".

### 2013-04-08
* Quarantine Notifications - Allow users to set multiple quarantine notifications.  Now they can specify different times on different days, or multiple messages in the same day.

### 2013-04-03
* Branding - Added form entries for setting page body background color, and a "Contact US" url.  These have not yet been integrated into the HTML template - estimated to be done before 15 April.

### 2013-03-31
* API Change - added "use_domain_policy" flag to user policy settings to indicate when to override the end-user policy setting with the domain-wide setting.  This replaces the previous "priority" methodology, making this much more understandable to API programmers.

### 2013-03-28
* Resending welcome email - Added feature to allow the password to be reset, and for that reset password to be included in the new welcome email.

### 2013-03-27
* fix IE8 bug with angular.js that was preventing deleting of items
 
### 2013-03-26
* Quarantine grid - added a gmail-like "Select All Messages" option when the topmost checkbox in the grid is selected, allowing the user to delete/recover/whitelist every single thing in a multi-page quarantine at one time.

* Miscellaneous fixes to the branding interface.

### 2013-03-22
* Added ability for user or admin to whitelist or blacklist <EVERYTHING> with a checkbox at the top of the black/whitelist grid. This option is for locking or allowing all email.  One specialized use is to blacklist <EVERYTHING>, and then whitelist only specific addresses, so that only those users can email you.

### 2013-03-20
* User Import - added interactive column builder.  If we can't recognize the proper content of a column, allow the user to specify or skip it.

### 2013-03-19
* Prevent empty white or blacklist entries from being created via API or user file import

### 2013-03-18
* Domain MX Check - fallback to parent domain's nameservers if no nameserver found for specified domain.

### 2013-03-15
* User import files now support custom header lines

### 2013-03-14
* User Import
	* Option to replace existing user data or to add to existing.  For multi-value fields (alias, blacklist, whitelist), adding to existing appends new items in the import file to existing records.  Choosing to replace will 
* Cut off text we can't decode in a quarantined message - caused by either corrupt message or malicious content.


### 2013-03-13
* Added "breadcrumbs" to help administrators move more quickly from a detail page to a parent's settings.  For example, you can jump from a user page, directly to a sub-tab on the domain page.


### 2013-03-12  - Branding Release
* Provides branding capability for customers, resellers - Contact MailRoute Support for information on signing up to brand your MailRoute Control Panel - support@mailroute.net

### 2013-03-12 - Feature Upgrade
  * Quarantine 
    * Separate tab in quarantine for Blacklisted senders
    * Add blacklist button to quarantine - blacklist senders directly from   quarantine message
    * Show error when invalid header cannot be decoded  
  * Quarantine Notifications
    * Users can now choose when to send notifications - date, minute, timezone
    * Don't display messages from blacklisted senders
    * Add separate "Recover" link to quarantine notification emails
    * Redesign of quarantine notification to show long subjects and senders
  * General
    * Fix inconsistencies between 7 and 8 character passwords.
    * Greatly improved information in the MX record checks in the Domain Setup Checklist.  Now queries all authoritative nameservers directly and reports if any are inconsistent
    * Show "saved" indicator when the "save" button is clicked on the policy settings pages
    * Dynamically load content for selectors such as pull-down menus that contain lists of domains/customers/resellers, to lessen page size and make them more responsive.
  * Import/Export functionality
    * Complete redesign of import and export.  
    * Import now includes users, aliases, passwords, white and blacklists, and filter settings.  This requires old import files to be updated to the new structure.  
    * Export includes everything that import does, except for passwords.
    * Import large user lists in the background if list contains > 100 items.  Notify user of completion of upload via email
  * API
    * Add notification tasks to user and domain objects
    * Users and admins can access API key(s) via user profile pages
      

### 2012-12-27
  * Add resend welcome email to user_index and user_detail#info

### 2012-12-26
  * Force bind cache flush on domain_detail#info load to better capture the MX record settings of a domain

### 2012-12-19
  * Add progress dialog to import user

### 2012-12-18
  * Don't display delete button in the delete tab of quarantine

### 2012-12-17
  * User list import - allow all types of newlines (mac/unix/pc/messed up pc) 
  * Minor display updates to accomodate jquery-ui upgrade

### 2012-12-16
  * Additional error checking and explicit error display on user list import

### 2012-12-15
  * Hide policy settings for users when their domain doesn't have a complete user list

### 2012-12-11
  * Better parsing of imported user lists

### 2012-12-10
  * Prevent partial creates or updates in certain models

### 2012-12-08
  * Additional checks for duplicate emails in quarantine

### 2012-12-07
  * Exclude "spammy" messages from Quarantine

### 2012-12-06
  * Additional checks for validity in imported emails
  * Show explicit dialog when message has expired from quarantine

### 2012-12-04
  * Properly display notification settings when different from domain-wide default

### 2012-11-28
  * Fix for page number issues after switching page display size

### 2012-11-26
  * Update to new MailRoute logo in emails
  * Try to improve searching and caching of quarantine

### 2012-11-20
  * Optimize deleting of large numbers of messages

### 2012-11-19
  * Update to new MailRoute logo on webpages

### 2012-11-16
  * Add labels to login and new user dialogs since IE9 doesn't support placeholder text
  * Interface bug - disabel notification if nothing is selected
  * Remove old spamstore login and refer people instead to admin-orig.mailroute.net

### 2012-11-15
  * Bug fixes - whitelist fixes, permissions issues for imported email accounts

### 2012-11-09
  * Quarantine Notifications - formal release, removing "coming soon"

### 2012-11-01
  * bug fix - read-only quarantine links

### 2012-10-31
  * bug fix - quarantine notification whitelist

### 2012-10-30
  * fix quarantine notification time stamps and loojips

### 2012-10-29
  * Various small bug fixes - message queue logging
  * Truncate sender/subject in quarantine emails

### 2012-10-24
  * enable domain-wide quarantine view for ALL administrators

### 2012-10-22
  * tuning sql lookups for performance

### 2012-10-21
  * Use message queues for quarantine release, to increase responsiveness

### 2012-10-16
  * Load quarantine tab on demand
  * Domain-wide quarantine

### 2012-10-15
  * Bug #515 - Strip spaces in bulk user import
  * Enforce minimum password requirements

### 2012-10-10
   * Added one-click "Recover and Whitelist" to quarantine
   * Remove recovered messages from the main quarantine list
