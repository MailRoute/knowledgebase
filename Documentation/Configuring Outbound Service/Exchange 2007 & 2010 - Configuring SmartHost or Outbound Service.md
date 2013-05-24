Microsoft Exchange 2007 and 2010 can be configured to send all email out through MailRoute with the following settings.  


This article already assumes that your Exchange Server is able to send emails externally, and so it must have a **Send Connector** properly set up and configured correctly on the **Hub Transport Server**.  And so we only need to configure the settings on that **Send Connector**.

1. Be sure you've signed up for the MailRoute Outbound service!  We won't accept email from your mailserver otherwise!
2. Open **Exchange Management Console**
3. Click on the (**+**) next to **Organization Configuration**
4. Select **Hub Transport** and
5. Select the **Send Connectors** tab.
6. Right-click on the existing **Send Connector**, select **Properties**
7. Choose the **Network** tab
8. Select **Route mail through the following smart hosts:** and click **Add**
9. Choose the radio button labeled **Fully qualified domain name (FQDN):** and enter
    **outbound.mailroute.net**

10. Click **OK**

The changes you've made should take effect without having to restart any services.

  
Please feel free to contact us at [support@mailroute.net][1] if you have any questions. 

   [1]: mailto:support@mailroute.net
