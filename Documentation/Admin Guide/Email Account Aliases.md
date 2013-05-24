An **Email Account* may have one or more **Aliases**.  An **Email Account Alias** inherits all the settings and user accounts of it's parent account.  It will share the same filter settings, the same white and blacklists, and share a common quarantine with it's parent and other aliases. 

For example, suppose you have a user "admin@mailroutedemo.com", and that user also uses the several aliases: "sales@mailroutedemo.com", "postmaster@mailroutedemo.com", "fred@mailroutedemo.com".  You can list each of these additional email addresses as alias of admin@mailroutedemo.com.  Then when you change the settings for one, or whitelist a sender, it will affect all the different addresses.  And quarantined email for each will end up one shared quarantine for easy viewing.

Edit an **Email Account Alias** by clicking on it's name.  Delete it with the red **X** (**Important:** this will delete all associated settings).

You can also Activate or Deactivate a **Domain Alias** on **hold**.  We will not accept or relay email for it when it has been deactivated.  Click in the "Status" column to change.

![Email Account Alias List](http://static.mailroute.net/kb/emailaccount_alias_list.png)


Click the **Add  Alias** button to add a new **Email Account Alias**.  Enter only the "localpart" of the email address - part to the left of the "@" symbol.

![Email Account Alias Add](http://static.mailroute.net/kb/emailaccount_alias_add.png)
