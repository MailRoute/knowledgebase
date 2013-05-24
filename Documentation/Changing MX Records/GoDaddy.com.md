## MX Record Configuration: GoDaddy.com

  1. Log in to the administrative console for your domain.  
        To log in, go to http://www.godaddy.com, enter your customer number or login name, enter your password, and then click the **Secure Login** button.  
  2. Mouse over the **Domains** tab in the upper-left corner of the window (without clicking the tab), then click **My Domains**.   
  3. In the **Domain Name** column, click the link for the domain that you want to configure.   
  4. On the **Details** page, click the link for **Total DNS Control and MX Records**.   
  5. Scroll down to the "MX (Mail Exchanger)"ù section and click **Add New MX Record**.   
  6. Add an MX record for MailRoute: 
    * Host Name: **@**
    * Priority: **10**
    * Enter Goes To Address (Mail Server): **mail.mailroute.net**. Be sure to include the dot (".") at the end of the name!
    * For the **TTL **drop-down list, set the value to **1 Hour**.   
    * Click **OK**.
  7. Note any existing MX records in case you need them later, and then delete them.  
