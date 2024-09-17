---
created_at: 2016-08-19 17:28:40
date: 2018-08-08 08:44:46
description: Explore the rise of internet traffic hijacking attacks abusing the trust-based
  BGP routing system, exposing the need for secure BGP deployment and transparency
  among network operators.
draft: true
params:
  author: Unknown
summary: The article discusses the rise of internet traffic hijacking, where attackers
  abuse the trust-based system of routing announcements to redirect traffic through
  their networks, allowing interception and data capture. It also explores potential
  solutions like securing BGP routes and increasing transparency between network operators.
tags: null
title: Internet Hijackings on the Rise, ITNews.com.au
---


[R.A. Plecas](https://support.mailroute.net/users/323805032 "Click here to
view this user's profile.")  
posted this on November 21, 2013, 07:25

[News on abuse of the internet's trust-based
system](http://www.itnews.com.au/News/365006%2Cinternet-traffic-hijacking-on-
the-rise.aspx)

By [Juha Saarinen](http://www.itnews.com.au/Author/224495,juha-saarinen.aspx)
on Nov 21, 2013 5:17 AM

## Trust-based system abused

Intentional redirection of internet traffic is on the rise, spurring calls for
route announcements to be signed and secured and for violations of trust to be
exposed through greater transparency between network operators.

Internet performance metrics vendor Renesys
[said](http://www.renesys.com/2013/11/mitm-internet-hijacking/) that this year
around 1,500 Internet Protocol (IP) address blocks have been hijacked on more
than 60 days, including several incidents in Australia.

The attacks targetted financial institutions, voice over IP providers and
governments, Renesys said.

Attackers take advantage of traffic routing announcements between networks
using Border Gateway Protocol ([BGP](http://www.ietf.org/rfc/rfc1771.txt))
being trust-based.

An attacker can abuse this by hijacking BGP routes of other providers, and
inserting their own routers in the network path. Such a man in the middle
attack would allow miscreants to intercept and capture data that originally
was not destined to go through their networks.

It is easy to work out which network operator conducted the route hijacking,
Renesys said, pointing to analysis of recent traffic redirection attacks done
by Icelandic and Belarus providers.

Attackers rely on the misdirection going unnoticed, and Renesys explained that
providers, banks, credit card processors and government agencies should
monitor how their advertised IP address prefixes are being routed globally.

Work towards digitally signing and securing BGP routes is also underway.
Guidelines published by the Communications Security Reliability and
Interoperability Council
([CSRIC](http://transition.fcc.gov/pshs/advisory/csric/)) under the United
States Federal Communications Commission (FCC) propose several measures for
secure BGP deployment.

These include better information being published on which provider is
authorised to route certain traffic at any given time and location, as well as
setting up a cryptographic identity management system for this - the Resource
Public Key Infrastructure (RPKI) - as part of a cautious, staged deployment of
improved security for BGP.

However, Renesys warns that the internet may never see secured and signed BBGP
routes, and suggests greater transparency between operators on the issue is
the way to go to expose targeted traffic misdirection.

Routing mishaps have happened in the past, mostly by accident. In 1997, the
operators of the Autonymous System 7007 caused widespread disruption to the
internet by accidentally leaking most of its entire routing table and creating
to a traffic black hole.

One of the better known cases of recent internet redirection involved the
Pakistani government, which [ordered YouTube to be
blocked](http://news.bbc.co.uk/2/hi/technology/7262071.stm) because of a video
it considered offensive.

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

