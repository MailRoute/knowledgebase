## MX Record Configuration: myhosting.com

  1. Go to http://myhosting.com.
  2. Click the **Account** link at the top of the page.
  3. Log in with your Domain Name and Password.
  4. Click the **Domain Name** tab.
  5. Click **DNS Management** in the left-hand pane.
  6. Click the **Manage DNS** button.
  7. Delete the existing **MAIL (MX) RECORDS**.
  8. Add the following **MAIL (MX) RECORDS**: 
    * Zone: **@**
    * Server: **mail.mailroute.net. **(don't forget the trailing dot "."!)
    * Priority: **10**
