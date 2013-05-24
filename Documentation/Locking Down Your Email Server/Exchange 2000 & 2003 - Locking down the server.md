Microsoft Exchange 2000 and 2003 can be locked down to only accept email from the MailRoute servers by following these steps:

1. Open **Exchange System Manager**
2. Go to **Servers -> [MailServer Name] -> SMTP**
3. Right click and go to **Properties for Default SMTP Virtual Server**
4. Click the **Access** tab
5. Click **Connections**
6. Choose **Only the List Below**
7. Click **Add -> Group of Computers** and enter our network block:
    * Subnet Address: **199.89.0.0**
    * Subnet Mask: **255.255.248.0**

Microsoft has an Administration Guide for Microsoft Exchange Server 2003 available at http://www.microsoft.com/downloads/en/confirmation.aspx?FamilyID=98e45481-1458-4809-97d6-50d8aeebd8a1&displaylang=en

