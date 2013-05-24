## MX Record Configuration: Namecheap.com

  1. Log in to your account at NameCheap.com.
  2. Click **Manage Domains**.
  3. Click the domain that you'd like to use with MailRoute.
  4. On the left side, under **Host Management **click **All Host Records**
  5. Under **Mail Settings **choose the 3rd radio button which says **User (Mail Server's Host Name Required) **then click **Save Changes**
  6. Add the following MX Record: 
    * Hostname: **"@"**
    * Mailserver Host Name: **mail.mailroute.net**
    * Mail Type: **MX (Mail Record)**
    * MX Pref: **10**
