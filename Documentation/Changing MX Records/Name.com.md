## MX Record Configuration: Name.com

  1. Log in to your account at http://www.name.com.  
  2. Click the **Account** icon in the top navigation bar.  
  3. Click the domain you're using with MailRoute.  
  4. At the right of the page, under **Control Panel**, click **Domain Management** to expand the menu.  
  5. Click **DNS Record Management**.  
  6. On the **DNS Management** page, note any existing MX records (in case you need to restore them later), and then delete them.  
  7. Select **MX** from the **Add a Record** drop-down to create an MX record for mailroute: 
    * Record Host: (leave blank)
    * MailServer: **mail.mailroute.net**
    * TTL: **300**
    * Priority: **10**
  8. Click **submit**.
