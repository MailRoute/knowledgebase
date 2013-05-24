## MX Record Configuration: Registerfly.com

  1. Log in to your account at Registerfly.com.
  2. Click **Manage Domains**.
  3. Click the domain that you'd like to use with MailRoute.
  4. Expand **DNS Settings (Zone file)**.
  5. Click **Configure**.
  6. If asked to change name servers to registerfly nameservers, do so. If you have hosting that requires you to use other nameservers, these instructions may not work for you.
  7. Note your existing MX records, in case you need to revert to them later.
  8. Clear all existing MX Records by checking the box next to each record and clicking **Remove selection**.
  9. Add a new MX Record: 
    * HostName: **@**
    * Record Type: **MX**
    * IP Address/URL: **mail.mailroute.net**
    * Pref: **10**
