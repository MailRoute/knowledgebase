---
created_at: 2016-08-17 23:34:15
date: 2024-04-12 14:40:30
description: A guide on how to disable Microsoft Exchange Content Filtering and Sender
  ID when using an external email filtering service, with links to Microsoft documentation
  for different Exchange versions.
draft: true
params:
  author: Unknown
summary: The article provides instructions for disabling Microsoft Exchange Content
  Filtering and Sender ID when using an external email filtering service like MailRoute,
  as Microsoft has announced they will stop updating these features. It includes links
  to documentation for different Exchange versions.
tags: null
title: Disabling Microsoft Exchange Content Filtering
---


When using MS Exchange with an outside email filtering service, you should
disable Content Filtering and Sender ID on the Exchange server. All of the
filter types are enabled by default, and if the server's mail traffic is
filtered by MailRoute, it is not necessary to keep them enabled.

Microsoft announced that on November 1, 2016, they would stop updating their
Content Filtering definitions, so disabling this feature is probably the
safest way to avoid false-positives. See:  
<https://technet.microsoft.com/en-us/library/bb124739(v=exchg.160).aspx>

The exact steps to take to disable Content Filtering and SenderID differ based
on your version of Exchange. Here are links to Microsoft's documentation for
each:

Exchange 2016:  
Configuring Content Filter: <https://technet.microsoft.com/en-
us/library/bb124739(v=exchg.160).aspx>  
Configuring SenderID: <https://technet.microsoft.com/en-
us/library/aa997136(v=exchg.160).aspx>

Exchange 2013:  
Configuring Content Filter: <https://technet.microsoft.com/en-
us/library/aa995953(v=exchg.150).aspx>  
Configuring SenderID: <https://technet.microsoft.com/en-
us/library/aa997136(v=exchg.150).aspx>

Exchange 2010:  
Configuring Content Filter: <https://technet.microsoft.com/en-
us/library/aa995953(v=exchg.141).aspx>  
Configuring SenderID: <https://technet.microsoft.com/en-
us/library/aa997136(v=exchg.141).aspx>

Exchange 2007:  
Configuring Content Filter: <https://technet.microsoft.com/en-
us/library/aa995953(v=exchg.80).aspx>  
Configuring SenderID: <https://technet.microsoft.com/en-
us/library/aa997136(v=exchg.80).aspx>

Once you disable SenderID, you should see this issue go away.

  
  
  

[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

