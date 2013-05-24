## Configuring Office 365 to use MailRoute

  1. Log in to your account [https://admin.messaging.microsoft.com](https://admin.messaging.microsoft.com)
  2. Click the **Administration** tab.
  3. Set up an inbound connector that tells Forefront not to do any filtering on your mail coming from MailRoute.  Microsoft calls this [Inbound Safe Listing Scenario] (http://technet.microsoft.com/en-us/library/gg430159.aspx).
  4. Click the **Domains** subtab.  Under **Enabled Domains**, click on your primary domain (not your *yourdomain.onmicrosoft.com* subdomain).
  5. Edit the inbound connector you just created: Next to **Inbound Connectors**, click **Select** and the connector you just defined, and then click **OK** to apply that connector to your domain.
  6.  Set **Name** to something descriptive like *MailRoute*.
  7.  Set the **Description** to something, well, descriptive, like *MailRoute - Inbound Safe Listing - do not apply filters*.
  8.  Set **Sender Domains** to "*.*".  This will match all incoming mail.
  9.  Set **Sender IP Addresses** to MailRoute's block of addresses.  Unfortunately, this field doesn't support CIDR address records larger than /24, so you have to enter 8 different values here for MailRoute:
      199.89.0.0/24, 199.89.1.0/24, 199.89.2.0/24, 199.89.3.0/24, 199.89.4.0/24, 199.89.5.0/24, 199.89.6.0/24, 199.89.7.0/24
  10.  Choose the radio button **Add these IP addresses to the safelist for the domains specified above**.
  11.  Under **Transport Layer Security (TLS) Settings**, choose the radio button **Opportunistic TLS**.
  12.  If you wish to disable the built-in filtering of Forefront (which we recommend), deselect all three checkboxes under **Filtering**.
  
  	![Forefront Admin Console - Add Inbound Connector](https://static.mailroute.net/kb/Office365InboundConnector.png "Forefront Admin Console - Add Inbound Connector")

  
It can take Microsoft 45-60 minutes to apply the changes you just made to your configuration.  After that time has passed, send yourself an email from an offsite account (like gmail or hotmail).  If you look at the headers, you should see a header in the email *X-FOPE-CONNECTOR*, which will list the connector you created, and you should see a MailRoute IP address (in the 199.89.0.0/21 block) in the *X-Safelisted-IP* header.
  
  