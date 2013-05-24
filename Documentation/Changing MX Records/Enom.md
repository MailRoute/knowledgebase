## MX Record Configuration: Enom

  1. Log in to your account at www.enom.com.
  2. Open the **Domains** tab and select **My Domain Names**. You'll be directed to the **Manage Domains** page.
  3. Click the domain that you'd like to use with MailRoute.
  4. From the **Domain Details** panel along the right, select the **+** icon under the Total DNS Control list item. A sub-list will appear.
  5. Click the entry titled **Total DNS Control And MX Records**. The **Manage MX Records, and DNS Zone File** panel will appear.
  6. Click **Launch Total DNS Control Manager**. The **DNS Manager** window will appear.
  7. Note the existing MX records in case you need them later.
  8. Clear all existing MX Records by clicking **Delete**.
  9. Click **OK** in the confirmation dialogue box.
  10. Once you've deleted all existing records, click **Add New MX Record**. The **MX (Mail Exchangers) Record Wizard** will appear.
  11. Enter the MailRoute record: 
    * **Select the Priority Value** drop-down menu: **10**
    * **Enter a Host Name**, leave the default setting to **@**.
    * **Enter Goes To Address** enter **mail.mailroute.net. **(be sure to include the trailing dot "."!)
    * **Select TTL Value** drop-down menu: **1 Hour**
  12. Click **Continue**.
  13. Click **Add** to confirm the entry. The **DNS Manager** main page will reappear when you've finished.
