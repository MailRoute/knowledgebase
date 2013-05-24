

###   Tips on Postini Migrations

#### MailRoute New Customers

Some MailRoute customers notice a significant difference in their mail volume after activating their MailRoute account. Some see much more mail that they consider to be spam, others see far less mail in their Quarantine. Why is this?

1.  MailRoute uses Greylisting and Adaptive Blacklisting

If you're seeing less mail in your Quarantine, congratulations! You're benefiting from MailRoute's first level of defense. We stop the most egregious spam at the very outer layer of filtering, which means you have less garbage to sift through in your Quarantine. Some other services pass this through to their customers, but MailRoute doesn't want to waste your time with mail from known, blacklisted spammers. 

2.  Ham vs Spam - MailRoute **hates hates hates** false positives

If you're seeing more mail volume in your inbox, these are probably opt-in marketing messages that you signed up for when you bought that widget online as birthday gift for your mom. Didn't uncheck that box that says "Yes, send me product news and updates"? Well, you're getting product news and updates.  And you know what?  MailRoute doesn't consider this spam!

At MailRoute, we talk about **Consent** vs **Content**. Blocking these messages from delivery to you would be a false-posiitve, in filtering parlance, and we don't like those. You can either unsubscribe to these messages or blacklist the domain that's sending them. 

You may have heard in the past that "clicking the *unsubscribe* link in an email just let's a spammer know someone is there, and that you'll get a flood of new spam as a result".  But MailRoute filters out those kinds of spammers - anything that's making it into your inbox with an unsubscribe link is almost certainly a company with legitimate and well-managed opt-in email policies.  If it makes it to your inbox, then you should be able to safely unsubscribe.  And if the company doesn't honor your wishes, let us know!  We'll have a talk with them and straighten them out.


#### If you have questions or would like more information about our proprietary filtering configuration, please contact info@mailroute.net
