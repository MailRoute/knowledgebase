## MX Record Configuration: cPanel

Many different hosts use cPanel as their control panel.  Here are some generic instructions that should apply to all (or at least most) of them.

  1. Log in to your cPanel account.  
  2. In the **Mail** section, click **MX Entry**.  
  3. If you have more than one domain, select the domain you’re using with MailRoute - look for this under the **Domain** heading.   
  4. Under **Email Routing**, select **Local Mail Exchanger**.  
  5. Click the **Change** button.  
  6. In the **Add New Record** section, create an MX record for MailRoute: 
    * Priority: **1**
    * Destination: **mail.mailroute.net**
  7. Under **MX Records**, note any old MX records, in case you need them later.
  8. Under **MX Records**, delete any original MX records.
