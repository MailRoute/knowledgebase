## Active Directory and LDAP Synchronization

MailRoute can synchronize your Active Directory or LDAP servers with the MailRoute
Control Panel to ensure that any user changes (additions or deletions) on your primary
Directory Server are easily transferred over to MailRoute.  You can even set this to run
automatically several times a day, more hands-off administration.

### How it works

MailRoute will query your Active Directory or LDAP Server (manually or at specified intervals) to retrieve an active list of user accounts and aliases from the server.  This list of users will then be compared with our internal lists of users, and the necessary accounts will be added or deleted to bring our system into sync with yours.

### What is required

1.  Your Active Directory or LDAP server must be accessible to a server in our block of addresses.
            
  Be sure your firewall and/or server configuration will accept a connection from our block of addresses:
    * 199.89.0.0/21
    * 199.89.0.0 with a netmask of 255.255.248.0
    * 199.89.0.0 through 199.89.7.255

2.  A user account with **read only** access to your domain information


### Setting it all up

1.  Visit the **Email Accounts** tab for the domain, and then select the **Directory Sync (AD & LDAP)** subtab.

2.  Click the **Settings** link to display the form to configure the service
  - *Active Directory/LDAP Servers* 
     -   This is a comma separated list of servers to which we should attempt to connect.  They will be tried in order.
  - *User* 
     - The username that will be used to connect to the server.  **This requires only READ access to the server**.  Indeed, we recommend against using an account with any level of Write access.
  - *Password*
       - You can probably guess what this field is for.
  - *Base DN*
      - This is the base DN for your AD or LDAP configuration.  It's typically related to your domain name, but if you support multiple suborganizations or the like, it may be a bit different.  It's going to look something like
         - dc=testdomain,dc=com
  - *LDAP Search String*
     - If you leave this blank, we'll use a standard search string that will retrieve all the user accounts and aliases from the typical Microsoft Active Directory Server.  This is a fairly complex lookup:   
         
         (& (mailnickname=*)(!(mailnickname=discoverysearchmailbox*))(!(mailnickname=federatedemail*))(!(mailnickname=systemmailbox*))
    (| (objectClass=publicFolder)
    (&(objectCategory=person)
    (objectClass=user)
    (!(homeMDB=*))
    (!(msExchHomeServerName=*)))
    (&(objectCategory=person)
    (objectClass=user)
    (|(homeMDB=*)
    (msExchHomeServerName=*)))
    (objectCategory=person)
    (objectCategory=group)
    (objectClass=msExchDynamicDistributionList) )
    (!(objectClass=contact)) )  
    
         - You can change this to something else if necessary, and use the **Test Connection** button to see if the server is properly returning results based on your query.


   ![AD/LDAP Sync - Settings ](http://static.mailroute.net/kb/dir_sync_settings.png)

3. Save your configuration by clicking the **Save** button

4. Test the settings and our ability to connect with the **Test Configuration** button.  This will attempt a connection and retrieve a small number of accounts to test the connectivity and the retrieval settings.  If all goes well, you can then continue on to perform a **Manual Sync**.


### Manual Synchronization

Once you've configured the service, you can perform an on-demand, manual synchronization at any time with the **Manual Sync** button.

Performing a synchronization can take a little while, so it happens in the background.  When you run a **Manual Sync**, the process will be queued up and will run on our server.  When it's completed, you will receive an email with a link to a page showing the results of the process.

Click the "Apply These Changes" button to apply the changes, of course.

  ![AD/LDAP Sync - Results ](http://static.mailroute.net/kb/dir_sync_results.png)
  

Once you've done a few manual syncs, and you're comfortable that everything is working the way it should, you can set up **Automatic Synchronization**.

### Automatic Synchronization

- **Schedule**  
    You can have this run every 6, 8, 12, or 24 hours.
- **Sync notifications enabled**      
  Send an email notification after every sync attempt.
- **Notification Receipients**
    Enter a list of emails that should receive those notifications.  One email address per line, if you please.
     

  ![AD/LDAP Sync - Auto ](http://static.mailroute.net/kb/dir_sync_auto.png)



### Wrapping Up

Active Directory and LDAP Synchronization can be a little bit difficult to get working sometimes, if you have any non-standard settings in your directory servers.  Please feel free to contact us at support@mailroute.net with any questions - we're always here to help.  

You can also post your own comments, questions, experiences, and advice in the [MailRoute Community Forums](https://support.mailroute.net/categories/20078122)

















