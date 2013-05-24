You may choose to use the **MailRoute Outbound Filtering SmartHost/Relay Host Service** (tm, all rights reserved).

**Important**: this service may incur additional cost. Please check your MailRoute agreement for pricing information.


### Description

With MailRoute's outbound service, email from your users is routed to our servers for filtering before it is sent off to external users. This protects your partners and customers from receiving virus-infected emails, and makes sure that your users aren't sending out spam, whether it's inadvertent or on purpose.

If you're tired of finding yourself on blacklists, or having trouble delivering email to the intended recipients, MailRoute's outbound service can help. We'll help you set your mailserver to send all email to us first, and then we take responsibility for the delivery of the email, lightening the load on your server, isolating your server from the rest of the internet for added security, and simplifying administration and maintenance.

We do not offer outbound relay services to bulk email companies, or for the purposes of mass mailing, and it is not sold separately from our Inbound Filtering Services.

### Advantages

* Isolate your server from the rest of the internet for increased security
* Simplify your email server configuration and reduce management
* Improve the deliverability of your email
* Stop worrying about being added to email blackists
* Stop emails sent by viruses or trojans on your user's computers

### Requirements

We restrict access for our Outbound service by IP address.  Your mailserver must have a static IP address in order to use this service.

### Implementation

1. Enter the IP addresses of each of your email servers.
    ![Outbound Servers](http://static.mailroute.net/kb/servers_outbound.png)
    
2. Set the Smart/RelayHost setting of your mailserver to *outbound.mailroute.net*
    We have information on how to do this for various email servers such as MS Exchange in our [online knowledgebase](https://support.mailroute.net/forums/21682301-Configuring-Outbound-Service)
    
3. (Optional) Update your SPF record.
    Add "include:spf.mailroute.net" to your SPF record.
    If your record looks like this:

        "v=spf1 ip4:192.168.0/27 -all"

    Add our spf record to it so that it looks like this:

        "v=spf1 ip4:192.168.0/27 include:spf.mailroute.net -all"

    For more information, see our online knowledgebase article about [changing your SPF records](https://support.mailroute.net/entries/22949176-Setting-your-SPF-record)

