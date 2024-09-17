---
created_at: 2021-02-09 23:17:02
date: 2024-04-12 14:40:30
description: Comprehensive guide on email authentication protocols SPF, DKIM, DMARC,
  and ADSP, explaining how they prevent email forgery, phishing, and spoofing attacks,
  with details on MailRoute's implementation.
draft: true
params:
  author: Unknown
summary: The article explains the importance of email authentication protocols like
  SPF, DKIM, DMARC, and ADSP in preventing email forgery, phishing, and spoofing attacks.
  It provides an overview of how each protocol works and how MailRoute implements
  them to secure email communications.
tags: null
title: Email Authentication and Phishing Protection - An Explanation and Exploration
---


Email authentication and phishing protection are not simple processes. There's
no one methodology baked into the internet specifications for email,
unfortunately. But there are a number of technologies out there that help with
this process. In order to prevent forgeries, phishing, and email spoofing we
use them all to help identify malicious messages.

  
But don't worry - MailRoute will take care of your Email Authentication needs.
We just need you to set up some stuff in your DNS so that we can manage it
afterwards.

### Here's what you need to know

First, a little bit of background info:

Every email has two different "from" addresses. One is in the header, and one
is in the SMTP envelope. Think of them as being analogous to the return
address on an envelope, and one on the letterhead of the note inside.

The envelope MAIL FROM header is a return address. It tells the email servers
where to return a failed message, or where to send bounce or other delivery
status notifications.

The other header is the "From:" header in the email header. This is what email
users see. It's typically set by the sender's email client.

Email authentication attempts to validate these "from" addresses and ensure
that they are coming from servers that are authorized to be sending email on
those senders' behalf.

We have three three email authentication protocols to help fight forgeries,
spoofing, and impersonation attacks: SPF, DKIM, and DMARC.

## What is SPF?

SPF (Sender Policy Framework) helps to detect sender forgeries in email. SPF
allows the receiving mailserver to check that email claiming to come from a
particular domain does indeed come from an authorized IP address. The list of
authorized sending IP addresses is published in the DNS of the sending domain.

SPF is documented in [RFC 7208, ](https://tools.ietf.org/html/rfc7208)and a
more human explanation can be found at
[Wikipedia.](https://en.wikipedia.org/wiki/Sender_Policy_Framework)

But here's a quick summary.

SPF uses the email address provided in the SMTP Envelope sender (MAIL FROM).
The recipient's email server looks up a TXT or SPF record in the DNS of the
sender's domain, and is able to use that information to determine if the
sending mailserver is allowed to send email for that domain.

SPF isn't perfect. It breaks many types of email forwarding. That's why we
don't blindly reject email that violates SPF. But we do use any SPF violations
to contribute to a higher overall SpamScore for a message, and we use that
information in conjunction with DMARC and DKIM records, as available, to
determine if a message may be a forgery.

And SPF, being based on the envelope from address, does nothing to prevent
forging of the "From:" header that users typically see in their email clients.
It just makes sure that the SMTP envelope "MAIL FROM" sender is sending from a
server that is allowed to send mail for that domain.\

See our KnowledgeBase article on [Implementing SPF for the MailRoute
Outbound/SmartHost Service](https://support.mailroute.net/hc/en-
us/articles/360021568194-Setting-Your-SPF)

##

## What is DKIM?

DKIM (Domain Keys Identified Mail) is a way for an organization to digitally
sign an email. This DKIM "signature" proves

  1. That the contents of the email have not been modified.
  2. That certain important headers, including the Subject, From, and various Received headers have not been been modified and no new important headers (like Subject or From) have been added.
  3. That the sender of the email is authorized by the owner of their domain.

DKIM is documented in [RFC 6376](https://tools.ietf.org/html/rfc6376) and
[Wikipedia comes through again with a great
article](https://en.wikipedia.org/wiki/DomainKeys_Identified_Mail). But we
will summarize here:

DKIM uses an encryption algorigthm to create a digital signature of the body
of the message and key headers. This signature is made by the sending
mailserver, using a stored private key. This signature can be verified with
the corresponding public key, which is published in the DNS records of the
domain by the domain's owner.

This prevents someone from being able to intercept your email, alter it, and
send it along with new (and potentially fraudulent) information. And it
ensures that the email came from someone who, along with the domain owner,
controls the published keys for the domain.

Here's an example of a digital signature for mailroute.net - you can see the
various headers that are signed, along with the body of the message:

    
    
    DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/simple; d=domain.com; h=x-mailer:date:date:message-id:subject:subject:mime-version:content-transfer-encoding:content-type:content-type:from:from:received:received; s=01; t=1544226411; bh=g3zLYH4xKxcPrHOD18z9YfpQcnk/GaJedfustWU5uGs=; b=tEsR3mOyyUWXmg1iOU75oTHZhpwLCwxPtOfJxE+7Dwxz1cP7YwiErj68sBcH6C2nfi8fiX3nY89AQdYBqe1VXj3TGS+9aRjET9h565y6GSgsb0O/3lbSpu0ZVFwgWG3dN0u49e/dsxpnJgWqLk6eeRsJg1jj8lOgx2Rlp2E0ajg=  
      
      
    

And the public keys published in a DNS record might look something like this:

    
    
    dkimkey._domainkey.domain.com.  3600  IN TXT "v=DKIM1\; p=" "MIGfMA0GCSqGSIb3DQEBAQUAA4GNIDJEKSLIgQDADOGoDBzA2ZAOCW7gtmnvCsr/" "tnpLrsDJo8Tm4v0KNRxhVxm75Jj/1oNY/zGqvmNh+nfn+mWJSOIENCksGo67xxom1" "qVZ7U3P3zwAt0vPMrPh96j/fnwUtGcxvfRasfGFkRRAx32HQ1dvXt+JO5b10RMUs" "gr1MGrgUtfJsskLQbwIDAQAB"

We make this easier for our customers - they don't have to create and manage
and rotate keys to keep things secure. We do it all for them, they just need
three entries in their DNS:

    
    
    mr01._domainkey.<domain>. CNAME mr01.dkim.mailroute.net.  
    mr02._domainkey.<domain>. CNAME mr02.dkim.mailroute.net.  
    mr03._domainkey.<domain>. CNAME mr03.dkim.mailroute.net.

See our KB article on [Implementing DKIM for the MailRoute Outbound/SmartHost
Service](https://support.mailroute.net/hc/en-
us/articles/115009100687-Implementing-DKIM-for-the-MailRoute-Outbound-
SmartHost-Service)

##

## What is DMARC?

DMARC (Domain-based Message Authentication, Reporting & Conformance) is a
message authentication method that uses both SPF and DKIM to verify whether or
not an email was actually sent by the person in the "From" header of the
message.

DMARC is documented in [RFC 7489](https://tools.ietf.org/html/rfc7489) And
here's our [obligatory Wikipedia link](https://en.wikipedia.org/wiki/DMARC).

DMARC looks at the results of the SPF and DKIM checks. A message must pass
both DKIM and SPF to pass dmarc, and at least one of the two must show proper
"alignment". Identifier "alignment" is where the domain name in the "From:"
header matches the domain in the DKIM signature, and/or the domain name in the
SMTP Envelope sender matches the "From:" header of the message.

If both pass, and at least one is in proper alignment, a message passes DMARC.
Failing to pass SPF or DKIM, or if both are out of alignment will result in a
DMARC failure.

A dmarc record may be as simple as

    
    
    _dmarc.domain.com.  3600  IN  TXT  "v=DMARC1; p=reject;"

The policy in this case is "reject". It's also possible to specify a
destination email address to receive reports of DMARC checks from other mail
servers, or to apply the restrictions to just a percentage of total email
volume. Senders with great concerns about forgeries (like banks and financial
institutions) and large outbound mailers may want to look at a service like
[Dmarcian](http://dmarcian.com) to assist in creating more complex DMARC
records and to manage error reports.

You guessed it - we have an article on [Implementing DMARC for the MailRoute
Outbound SmartHost Service](https://support.mailroute.net/hc/en-
us/articles/360062946093-Implementing-DMARC-for-the-MailRoute-Outbound-
SmartHost-Service)

## What about ADSP?

And wait - did we say there were three methods for email authentication? Well,
there's sort of a fourth one.

  
Long before DMARC came along, there was a little thing called ADSP (Author
Domain Signing Practices). The was an
[RFC](https://tools.ietf.org/html/rfc5617) in 2009, but it was abandoned in
2013 because of general lack of use. [Wikipedia has the details, as
usual](https://en.wikipedia.org/wiki/Author_Domain_Signing_Practices).

So why do we care about this? We know that most other people are going to
ignore ADSP records. Some, who use things like SpamAssassin, might still be
checking them, but many providers don't. But MailRoute does.

  
Why? Because DMARC doesn't have any feature that specifies that every single
message from a particular domain MUST be signed with DKIM. A message that
breaks DKIM or SPF is penalized, but an unsigned message doesn't get penalized
(it doesn't get any nice bonus points either, but it's not automatically
relegated to the quarantine or the trash).

ADSP is very simple. You simply specify if your domain DKIM signs EVERY SINGLE
MESSAGE:

    
    
    _adsp._domainkey.domain.com. IN TXT "dkim=all"
    

You have to be sure that everyone who sends email on behalf of your domain is
doing DKIM signing. If all your mail goes thorugh MailRoute, you're safe
there, as long as you've set up your DNS records for DKIM, of course.

If you have a record like this, then MailRoute can discard all mail for your
domain that claims to come from your domain, but which isn't properly signed
by your domain. So you can avoid all those forgeries and phishing attacks that
try to make you think the email is coming from inside the house.

So we like it, we use it, and it's a good thing to do, even if the rest of the
world doesn't bother.

And I know you're expecting another KB article on that, but we just added it
to the one on [Implementing DMARC for the MailRoute Outbound SmartHost
Service](https://support.mailroute.net/hc/en-
us/articles/360062946093-Implementing-DMARC-for-the-MailRoute-Outbound-
SmartHost-Service)

