---
created_at: 2016-08-19 17:28:03
date: 2016-08-19 17:32:23
description: Oxford University temporarily blocked Google Docs due to a surge in phishing
  attacks hosting malicious login forms, highlighting the challenges institutions
  face in combating such attacks and urging better responsiveness from Google to address
  abuse of their services.
draft: true
params:
  author: Unknown
summary: This article discusses the measures taken by the University of Oxford to
  block Google Docs temporarily due to a surge in phishing attacks that used Google
  Docs for hosting malicious login forms. It highlights the challenges faced by institutions
  in dealing with such attacks and calls for better responsiveness from Google to
  mitigate abuse of their services.
tags:
- image-missing
title: Google Docs rejected by OxUni for Security
---


[R.A. Plecas](https://support.mailroute.net/agent/#/users/323805032 "Click
here to view this user's profile.")  
posted this on March 8, 2013, 08:12

<http://blogs.oucs.ox.ac.uk/oxcert/2013/02/18/google-blocks/>

We recently felt it necessary to take, temporarily, extreme action for the
majority of University users: we blocked Google Docs.

Why would we do such a thing, you might well ask. Surely Google Docs is a
perfectly legitimate site, widely used by staff and students as part of their
work and personal lives?

We know that. Unfortunately, it is also frequently used for illegal
activities; importantly, illegal activities which threaten the security of the
University’s systems and data.

**Background: phishing
attacks**[](http://blogs.oucs.ox.ac.uk/oxcert/files/2013/02/phishing.png)

Many readers will be aware that over the past few years, [phishing has been a
major problem for us](https://blogs.oucs.ox.ac.uk/oxcert/2011/08/12/the-price-
of-phish/). Not the sort of phishing in which the attacker gets hold of online
banking details – in general that’s a matter for users, their banks, and law
enforcement. What we care about are phishing attacks harvesting credentials
for University systems, in particular email accounts.

In general the attackers are seeking accounts from which to send out spam.
Lots of spam. Universities tend to have well-connected email systems which are
generally considered reputable by other email providers. In the absence of
effective monitoring, it can be easy for over a million messages to be sent
out before someone happened to notice. Once a compromised account is closed
off, the attackers simply move to another one. Every so often they need to
send out a bunch of phishing emails to snare some more accounts from which to
advertise their little blue pills or whatever.

For a successful phishing attack, the attackers need some means of capturing
login credentials. Not so long ago, they’d simply ask for users to reply to
the phishing email, including their details. These days that approach is less
common, and most attacks bear a link to a web form. The forms are hosted
anywhere they can find – perhaps a compromised webserver, perhaps one of the
world’s many free webform hosting providers.

Now, Mom & Pop’s Free Form Farm is unlikely to be used by many legitimate
users, and if we were to block access to it, it’s unlikely to be a big deal
for anyone but the phishers. But as well as all the small providers, there’s a
big one: Google Docs.

**Google Docs and phishing**

[](http://blogs.oucs.ox.ac.uk/oxcert/files/2013/02/google-phish.png)

One of many recent phishing pages on Google Docs

Google Docs has many advantages. One significant one is that millions of
people use it for perfectly law-abiding purposes. Another is that traffic is
encrypted. Many educational establishments will have some capability for
filtering traffic to malicious URLs as it flows through their network. That’s
easy with unencrypted traffic. If the site uses SSL, then you have to do some
kind of SSL interception. Straightforward on a corporate network full of
tightly-managed systems. Much harder on a network full of student machines,
visitor laptops and the like, and [in our opinion, something to be
avoided](http://blogs.oucs.ox.ac.uk/oxcert/2011/06/10/ssl-interception-making-
the-world-a-safer-place/).

So how can you stop your users reaching the phishing forms? Assuming that the
phishing emails get past all your anti-spam and anti-malware defences, you
essentially need to ask Google nicely if they could take the form down. That’s
simple enough – Google’s own security team have advised us that the best way
is to use the “Report abuse” link that’s at the bottom of each page. Easy
enough.

Unfortunately, you then need to wait for them to take action. Of late that
seems typically to take a day or two; in the past it’s been _much_ longer,
sometimes on a scale of _weeks_. Most users are likely to visit the phishing
form when they first see the email. After all it generally requires “urgent”
action to avoid their account being shut down. So the responses will be within
a few hours of the mails being sent, or perhaps the next working day. If the
form is still up, they lose. As do you – within the next few days, you’re
likely to find another spam run being dispatched from your email system.

**Recent attacks**

Over the past few weeks there has been a marked increase in phishing activity
against our users. Now, we may be home to some of the brightest minds in the
nation. Unfortunately, their expertise in their chosen academic field does not
necessarily make them an expert in dealing with such mundane matters as emails
purporting to be from their IT department. Some users simply see that there’s
some problem, some action is required, carry it out, and go back to
considering important matters such as the mass of the Higgs Boson, or the
importance of the March Hare to the Aztecs. Granted, many, if not most of our
users do spot the scams, and do nothing (or better, [warn _us_ about
it](http://www.oucs.ox.ac.uk/email/phishing/index.xml?ID=howtohelp)). But as
with most spam, it only takes a small proportion to respond for the attacks to
be worthwhile. And we have tens of thousands of users. Despite all attempts at
user education, some will inevitably respond. We see a good mix: first-year
“digital native” undergraduates, ancillary staff, emeritus professors.

The recent attacks have often seen us dealing with several account compromises
within a short length of time. We are keen to see that compromises and
associated spam runs do not adversely impact the University’s “reputation”
with external email services such as Hotmail and GMail. We have had problems
in the past in which [Hotmail have rejected all mail from us over a period of
many days](https://blogs.oucs.ox.ac.uk/oxcert/2011/10/07/oxmail-versus-
hotmail/), owing to too high a proportion of the mail from us being marked as
spam. Such incidents can cause major disruption to legitimate University
business, especially given the number of sites which make use of Live@edu and
other outsourced email solutions. Spam is not the only threat to University
business from an account compromise, of course – something the University of
East Anglia [know all too well](http://www.bbc.co.uk/news/world-15840562).

**Blocking Google
Docs**[](http://blogs.oucs.ox.ac.uk/oxcert/files/2013/02/phishblock.png)

Almost all the recent attacks have used Google Docs URLs, and in some cases
the phishing emails have been sent from an already-compromised University
account to large numbers of other Oxford users. Seeing multiple such incidents
the other afternoon tipped things over the edge. We considered these to be
exceptional circumstances and felt that the impact on legitimate University
business by temporarily suspending access to Google Docs was outweighed by the
risks to University business by _not_ taking such action. While this wouldn’t
be effective for users on other networks, in the middle of the working day a
substantial proportion of users would be on our network and actively reading
email. A temporary block would get users’ attention and, we hoped, serve to
moderate the “chain reaction”.

It is fair to say that the impact on legitimate business was greater than
anticipated, in part owing to the tight integration of Google Docs into other
Google services. This was taken into account along with changes to the threats
and balance of risks over the course of the afternoon, and after around two
and a half hours, the restrictions on access to Google Docs were removed.

**What next?**

We appreciate and apologise for the disruption this caused for our users.
Nevertheless, we must always think in terms of the overall risk to the
University as a whole, and we certainly cannot rule out taking such action
again in future, although our thresholds for doing so may be somewhat higher.
We are meanwhile investigating several possible technical measures for
reducing the risks to the University with less impact on legitimate network
usage, and will be reviewing our emergency communications procedures.

We will also be pressuring Google that they need to be far more responsive, if
not proactive, regarding abuse of their services for criminal activities.
Google’s persistent failures to put a halt to criminal abuse of their systems
in a timely manner is having severe consequences for us, and for many other
institutions. If OxCERT are alerted to criminal abuse of a University website,
we would certainly aim to have it taken down within two working hours, if not
substantially quicker. Even out of official hours there is a good chance of
action being taken. We have to ask why Google, with the far greater resources
available to them, cannot respond better. Indeed much, if not all, of the
process could be entirely automated – and part of their corporate culture is
that their programmers and sysadmins should be automating common tasks such
that they can devote efforts to more interesting matters. Google may not
themselves be being evil, but their inaction is making it easier for others to
conduct evil activities using Google-provided services.

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)  
  
---

