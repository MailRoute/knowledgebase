MailRoute supports full "opportunistic" TLS - it's automatic and it requires no configuration on our end.

### What is "TLS"?

TLS stands for "Transport Layer Security".  It's a way of encrypting data over the internet to provide for secure end-to-end communications.  If you really want to get into the details, check out [Wikipedia's article on TLS](http://en.wikipedia.org/wiki/Transport_Layer_Security).


### What is TLS for email?

TLS provides certificate-based authentication and encryption between any two email servers that are so configured.  All communications between the two servers are secure, preventing eavesdropping and tampering.

### How does MailRoute support TLS?

MailRoute uses "opportunistic" TLS.  This means that we advertise that we support it, and we turn it on whenever an email server we are talking to advertises it's availability as well.  Here's a simplistic explanation:

When a sending mailserver connects to us, we tell it that we support TLS.  Our two servers then exchange encryption keys, and switch to a secure form of communication.

When we connect to an outside mailserver to relay an outbound message, we look for TLS support on that server, and if it's there, we use that.

The end result is that any communication between MailRoute and any other server that supports TLS will be secure.  And there's no additional configuration required on the MailRoute end.

### Do I need to do something on my email server to support TLS?

Yes, you do.  You need to acquire the appropriate certificates, install them on your email server, and configure it to use TLS.  How you do this depends on your email server.  Here are some links to help you configure it on your end:

* [Microsoft Exchange](http://support.microsoft.com/kb/829721)
* [Postfix](http://www.postfix.org/TLS_README.html)
* [Communigate](http://www.communigate.com/cgatepro/PKI.html)
* [Sendmail](http://www.sendmail.org/~ca/email/starttls.html)
* [MDaemon](http://www.redline-software.com/eng/support/docs/mdaemon/c9s3.php)
