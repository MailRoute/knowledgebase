## MX Record Configuration: DynDNS

  1. Log in to your account at DynDNS.com.
  2. Click **My Services** below your username.
  3. Under **Zone Level Services**, Click **Custom DNS** next to the domain you will be using with MailRoute.
  4. Under **Mail eXchanger (MX) Records**, note your existing MX records, in case you need them later.
  5. Then select all existing domains, and click **Delete MX**. (If you currently have no MX records created, you won't see an option to Delete MX, in that case, skip this step).
  6. Next to **Mail eXchanger (MX) Records**, click **Add New MX**.
  7. For **Preference**, select **5 -- Highest**.
  8. For **Mail Exchanger**, enter **mail.mailroute.net. **(don't forget the trailing dot "."!)
  9. Click **Modify MX**.
