# MailRoute Greylisting

MailRoute's optional GreyListing service is available to all MailRoute customers at no additional charge as an integral part of the standard spam filtering service.
 
This service has proven to be very effective at reducing spam - particularly the most egregious types.  Virtually every one of our customers have reported that the amount of spam that sneaks past MailRoute has dropped significantly, others have shown that as much as 90% of their spam volume is being caught by this new technique.
 
 
## The Marketing Pitch
 
GreyListing relies on the fact that most spam-sending software, "bots", "zombies" and "trojan-horses" do not behave in the same way as legitimate mail servers.   It requires no maintenance, and no interaction from either the sender or the recipient.  It is a fully automated service. "Bots", "zombies" and "trojan horses" infect as many as 60-80% of all consumer PCs (1), and which are responsible for the transmission of as much as 50% of all spam (2).
 
There is no charge for this new service. 
 
 
### How does it work?
 
GreyListing makes a sender's email server jump over a simple hurdle before MailRoute will accept it's email.  The first time somebody sends you an email, we check to see if that person has emailed you before using the same email server.  If not, we tell the sending server "back off and try again in a minute".   Regular mail servers are used to seeing this sort of message, and for all sorts of reasons.  For example, Microsoft Exchange will give this same temporary error message if it's running low on disk space, or the server is overwhelmed with mail processing.
 
Legitimate mail servers will take this "try again" message in stride, wait a minute or two, and then make a new connection attempt.  This time the mail will come right into the MailRoute servers, where it will run through the usual gamut of email processing that checks for viruses and spam, and if clean, it will be delivered right to your mail server.
 
But 'bots, zombies and trojan-horses, email viruses, and much of the mass-mailing software programs used by the typical spammer are designed to simply send out as many spams as possible as quickly as possible.  Not only can they not handle the error message, they also don't have the facilities to queue up and retry sending the emails.  So the MailRoute GreyListing service blocks these spams and viruses outright.
 
**Will this cause any delays?**
 
Yes - but only the first time somebody sends you an email.  Typically there is a one to two minute delay the very first time that somebody sends you an email.  All subsequent times there's no delay - email passes right on through.  And we've also built in a lot of smarts too - if we see a lot of legitimate mail coming from a particular mail server, we automatically allow all mail from them to come in without the delay.  Our adaptations eliminate even the initial delay about 40-50% of the time.


## The Technical Description
 
### What exactly is "GreyListing"?
 
Note: This section is adapted from the original whitepaper on greylisting by Evan Harris, 2003-08-21 [3]. This whitepaper originally inspired our use of GreyListing as a method to increase our spam capture rates.
 
GreyListing looks at three key pieces of information:

1. IP address of the host trying to send email
2. Envelope sender address
3. Envelope recipient address.
     
The first time the MailRoute GreyListing service sees this particular "triplet" of information, it is logged into a database, and the sending mail server receives a temporary deferral error code - in other words, it is politely told to 'try again in a minute".  Since Internet email transport isn't guaranteed, the possibility of temporary errors is built into the Internet specifications [4].  A well-behaved email server will try again to deliver the message.  When it does, we accept the message and pass it along to the rest of the MailRoute filters for further processing and delivery.  We also note the successful re-delivery attempt in our database, and we never bother delaying that triplet again.
 
However, much spam software is not based on a legitimate email server technology.  It is designed to send millions and millions of messages as quickly as possible.  It never retries to send a failed message.  And infected PCs, those with "bots", "zombies" and "trojan horses" on them that send out email on a spammers behalf don't either.  Email from these types of senders is blocked right away.
 
Greylisting has shown to be quite successful in blocking fast-moving email-borne viruses too, since they do not, in general, retry deliveries.
 
### MailRoute's adaptations to generic "greylisting"
 
We've made numerous adaptations to the generic type of greylisting to improve accuracy for corporate users.  These include:                         
 
**Adaptive Delay Requirements**: We vary the amount of time a server must wait before retrying by a variable amount.  We can't have spammers get past us by simply sending each email twice.  At the same time, we don't want to require an unacceptably long period to have to go through before an email is accepted after the first attempt (a minimum of 4 hours in the original reference implementation [5].
 
**Static Whitelisting**: Major ISPs and mail providers who are known to be "good citizens" are already whitelisted in our implementation.
 
**Automatic Whitelisting**: Based on patterns showing legitimate email traffic from servers, we automatically whitelist particular IP addresses, or even blocks of addresses to remove future delays entirely.
 
**User Overrides**: The GreyListing service can be enabled and disabled for entire domains or for individual users.  An individuals settings can override the domain settings, so that it's possible to GreyList for a customer, while disabling GreyListing for a particular address or set of addresses. 
 
 
 
Footnotes:
 
1. http://news.zdnet.com/2100-1009_22-6031108.html
2. http://www.pcworld.com/news/article/0,aid,121381,00.asp
3. http://projects.puremagic.com/greylisting/whitepaper.html - Evan Harris
4. ftp://ftp.rfc-editor.org/in-notes/rfc821.txt - in particular, Appendix E, the discussion of a "Transient Negative Completion reply".
5. Harris, ibid
