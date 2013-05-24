## Setting your SPF Record

If you use the **MailRoute Outbound/SmartHost Service** and you have SPF records, there's an simple, but important change you need to make to your SPF records.

Add "include:spf.mailroute.net" to your SPF record.

If your record looks like this:

        "v=spf1 ip4:192.168.0/27 -all"


Add our spf record to it so that it looks like this:

        "v=spf1 ip4:192.168.0/27 include:spf.mailroute.net -all"
        
That's all there is to it!        


### How do I add or change my SPF record?

Well, that all depends on your DNS host.  You'll need to talk to them to work out all the details.  There are too many different possibilities for us to try to work them all out here.



### What is an SPF Record?

The SPF record is used by some systems to determine if an email is coming from a legitimate mailserver - one that is authorized to be sending email from a particular domain.

You can read all about SPF Records here: http://en.wikipedia.org/wiki/Sender_Policy_Framework

Please feel free to contact us at [support@mailroute.net][1] if you have any questions. 

   [1]: mailto:support@mailroute.net
