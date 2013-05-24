
# Migrating from Postini

Migrating from one service to another isn't always fun, but with MailRoute, at least it's easy.  We'll walk you through the steps you need to take to set up a MailRoute account and to export your data from Postini for submission to us.  Then we'll get everything all set up for you, and we'll get your new service up and running. 

### Step 1.  Set up your new account with MailRoute

Fill out our form at [http://mailroute.net/signup.html](http://mailroute.net/signup.html)  All we need is your contact information, your domain name and mailserver name or IP address.

### Step 2.  Export your data from Postini

We have to do this in two steps, because the Postini interface doesn't allow you to simultaneously download a list of user settings and the list of alias accounts.

1.  Download User List and Settings
	a.  Open the Administration Console and select the **Orgs and Users** tab.
	![Postini Admin Console - System Administration](https://static.mailroute.net/kb/postini_migration_step_1.jpg "Postini Admin Console - SysAdmin")
		a. Click the **Users** link and select your Account org from the **Choose Org** pull- down list.
	b. Type in the "%” character and then the domain name in the **Find User** field and click **Search**.
    This performs a search across all of your organizations for user addresses using that domain, returning the first 15,000 users.	
	c. Click Download Users/Settings.
	![Postini Admin Console - Users/Settings](https://static.mailroute.net/kb/postini_migration_step_2.jpg "Postini Admin Console - Downloading Users and Settings")		
	d. Select and copy all of the lines that have email addresses on them.o
	e. Open a text editor ()if using Microsoft Notepad, turn word-wrap off) and paste the text. Name the file "domain.com_users.csv"	
	
2.  Download Alias list

	a.  Open the Administration Console and select the **Orgs and Users** tab.
	![Postini Admin Console - System Administration](https://static.mailroute.net/kb/postini_migration_step_1.jpg "Postini Admin Console - SysAdmin")
	b.  Click the **Batch** link.
	![Postini Admin Console - System Administration](https://static.mailroute.net/kb/postini_migration_step_4.jpg "Postini Admin Console - Orgs and Users")

	c.  In Section 2.5, manual input, enter the following, replacing *<domain_name>* with the domain name of the domain you wish to download:

               listusers ALL, targetOrg=<domain_name>, childorgs=1, aliases=1, fields=ADDRESS|PRIMARY_ADD|U_ID, sort=u_id:na|primary_add:a

	d.  In Section 4, enter the **process code** (presented in red)
		
	e.  Click **Submit job**
	![Postini Admin Console - System Administration](https://static.mailroute.net/kb/postini_migration_step_5.jpg "Postini Admin Console - Batch")

	f.  Your browswer will download a file.  Rename this file "domain.com_aliases.csv"
		


### Step 3.  Send your info to us.

Email both "domain.com_users.csv" and "domain.com_aliases.csv" to us at **support@mailroute.net**

Our team of implementation specialists will validate the files, review the information, and upload all the user accounts, aliases, whitelists and blacklists to your account.  We will notify you as soon as everything is ready.

### Step 4.  Change your MX records to direct your email to MailRoute

We'll give you simple instructions on how to change the MX records for each of your domains to direct all email to MailRoute.  We'll then filter out the bad stuff and relay the good stuff on to your server.

### Step 5.  Remove or disable your Postini account

If you don't remove or disable your Postini account once you're up and running with MailRoute, you may find that other Postini customers may have trouble reaching you.  If Postini thinks it's supposed to be routing email for your domain, it will try to do so based on it's configuration settings - which may be different than what you set up at MailRoute.  And if you lock down your servers to only accept mail from us, per our recommendation, then they won't be able to deliver mail to your server any longer.
