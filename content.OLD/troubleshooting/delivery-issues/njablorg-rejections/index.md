---
created_at: 2019-01-02 16:20:40
date: 2019-01-02 16:23:14
description: Informative article on the expiration of njabl.org domain and the need
  to remove related blacklisting from servers to prevent mail rejections, also stating
  that additional filtering is unnecessary.
draft: true
params:
  author: Unknown
summary: The article discusses the expiration of the njabl.org domain name and the
  resulting rejections that may occur, advising administrators to remove any blacklisting
  related to njabl.org from their servers. It also mentions that since mail is being
  filtered, there is no need for additional filtering on the server.
tags: null
title: Njabl.org Rejections
---


As of Jan 02/2019, the domain name njabl.org was set to expire and DNS servers
were switched to Tucows autorenew servers which would cause any lookups by
servers still not having removed the configuration to have rejections.

Remove any blacklistings regarding njabl.org from your servers in order to
prevent this from occurring - and since your mail is being filtered, there
should be no need to any have additional filtering set on your server.

<https://en.m.wikipedia.org/wiki/Not_Just_Another_Bogus_List>

