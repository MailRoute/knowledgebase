## Outbound Email Quotas

There is a default outbound email quota on each account.  It's not meant to cause you trouble or limit you.  It's there to help in those cases where someone gets a virus or malware on their system that starts spewing out spam or viruses - and we like to catch those as quickly as we can.

The quota is on a per-user basis.  Every email sender has their own quota.

### The standard Outbound Quota 

* 1000 emails per hour  or
* 1000 recipient per hour or
* 1GB of data

Whatever comes first.

As you can imagine - the majority of typical email users will never approach these numbers.

### But I'm special!

But what if you're special?  What if you're sending out legitimate mailings to your customers, or you're a school that has to send notifications out to parents, or maybe you're just very prolific?

We can raise and adjust the quota for you.  Just drop us an email at support@mailroute.net, and let us know what you need, and we'll take care of it.

### What happens if I go over the quota?

We will refuse the message from your mailserver, and your mailserver should return it to you with a notification that you're over quota.  The exact bounce message and format will depend on your mailserver, but a typical one looks like this:


    From: Microsoft Outlook 
    Sent: Friday, May 24, 2013 9:57 AM
    To: Somebody Special
    Subject: Undeliverable: Your original subject here
    
    Delivery has failed to these recipients or groups:

    billie@holiday.com (billie@holiday.com) (mailto:billie@holiday.com)
    Your message wasn't delivered due to a permission or security issue. It may have been rejected by a moderator, the address may only accept e-mail from certain senders, or another restriction may be preventing delivery.

    The following organization rejected your message: gw18.lax01.mailroute.net.

    Diagnostic information for administrators:

    Generating server: YourMailserver.yourdomain.com

    billie@holiday.com
    gw18.lax01.mailroute.net #554 5.7.1 <billie@holiday.com>: Recipient address rejected: Policy Rejection- Quota Exceeded. ##

