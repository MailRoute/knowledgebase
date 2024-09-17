---
created_at: 2023-03-24 20:14:34
date: 2023-11-16 17:36:18
description: API documentation for managing quarantined emails, including retrieving
  spam, virus, and other quarantined messages, deleting or recovering messages, and
  adding senders to allow lists at the domain or email account level.
draft: true
params:
  author: Unknown
summary: This article provides detailed documentation for the API endpoints related
  to managing and retrieving quarantined emails, including filtering by content type,
  deleting and recovering messages, and adding senders to allow lists. It covers both
  domain-level and email account-level quarantine APIs.
tags: 
- API
title: API - (Part 6) - Quarantine Resource
---


API Documentation:``

_Note: v2 api endpoints replaced previous v1 quarantine api endpoints._``

**_Domain Quarantine_**``

Endpoint: `/api/v2/quarantine/domain/{pk}/```

Endpoint: `/api/v2/quarantine/domain/{domain_name}/```

**Method** : GET

**Parameters** :````

Url placeholders:``

  * pk (required): The primary key of the domain for which to retrieve quarantine messages.
  * domain_name (required): The name of the domain for which to retrieve quarantine messages.

GET params:``

  * label: Filter the messages by content type. Possible values are Spam, Spoof, Virus, Banned, BadMIME, Unchecked, Deleted, Recovered, Blocked.

**Response message format**``


​    
    {
        "author": [
        "foxnews@inbox.foxnews.com"
        ],
        "blacklisted": false,
        "content_type": "Spam",
        "date": "14 Nov 2023, 12:31 AM",
        "domain_id": 3,
        "email_account_id": 1,
        "envelope_sender": "foxnews_148ab4a67b269b58c03c0906340c459d4c7f77af4a1d50c2@inbox.foxnews.com",
        "from_addr": "foxnews@inbox.foxnews.com",
        "has_attachments": false,
        "id": "test/_z0wzosBS2HOxF2OZQIB",
        "mail_from": "foxnews_148ab4a67b269b58c03c0906340c459d4c7f77af4a1d50c2@inbox.foxnews.com",
        "mail_id": "EieNvTDw3Itr",
        "pk": "test/-j0wzosBS2HOxF2OZQIB",
        "rcpt_to": "u1@usercase.com",
        "recipient": "u1@usercase.com",
        "resource_uri": "/api/v2/quarantine/test/_z0wzosBS2HOxF2OZQIB/",
        "size": 6775,
        "spam_score": -16.151,
        "status": null,
        "subject": "IDALIA'S WRATH: Monster storm leaves 'severe damage' and flooding in coastal states",
        "time_unix": 1693438313.248,
        "timestamp": "2023-11-13T23:31:53.248000Z",
        "virusnames": []
    },


Where``

  * spam_level: The spam level of the message
  * content_type: One of Spam, Spoof, Virus, Banned, BadMIME, Unchecked, Deleted, Recovered, Blocked.
  * date: The date the message was received
  * mail_from: The envelope sender of the message
  * author: The from address of the message
  * resource_uri: The URI of the full message with body and headers
  * recipient: The recipient of the message
  * resource_uri: The URI of this quarantine item
  * size: The size of the message in bytes
  * subject: The subject of the message
  * status: 'D' for deleted, 'R' for recovered

**Examples**``

To fetch Spam messages for domain "example.com":``


​    
    GET /api/v2/quarantine/domain/example.com/?label=Spam


**Response** :``


​    
    {
        "meta": {
            "limit": 20,
            "next": "?label=Spam&limit=20&offset=20",
            "offset": 0,
            "previous": null,
            "total_count": 63
        },
        "objects": [
        {
            "author": [
                "ecomm.online@fileburst.net"
            ],
            "blacklisted": false,
            "content_type": "Spam",
            "date": "13 Nov 2023, 12:49 PM",
            "domain_id": 3,
            "email_account_id": 1,
            "envelope_sender": "ecomm.online@fileburst.net",
            "from_addr": "ecomm.online@fileburst.net",
            "has_attachments": true,
            "id": "test/9mUKVoMBTdm1qP6SFWgf",
            "mail_from": "ecomm.online@fileburst.net",
            "mail_id": "OKsh12hdb9zd",
            "pk": "test/-j0wzosBS2HOxF2OZQIB",
            "rcpt_to": "u1@usercase.com",
            "recipient": "u1@usercase.com",
            "resource_uri": "/api/v2/quarantine/test/9mUKVoMBTdm1qP6SFWgf/",
            "size": 30266,
            "spam_score": 14.582,
            "status": null,
            "subject": "Concern regarding your account.",
            "time_unix": 1693482589.003,
            "timestamp": "2023-11-13T11:49:49.003000Z",
            "virusnames": []
        },
    ...


To fetch Visus messages for domain "example.com":``


​    
    GET /api/v2/quarantine/domain/example.com/?label=Virus


To fetch deleted messages for domain "example.com":``


​    
    GET /api/v2/quarantine/domain/example.com/?label=Deleted


**Delete a message from quarantine**``

**Endpoint** : `/api/v2/quarantine/{id}/```

**Method** : DELETE``

`resource_uri` of quarantine item can be used to delete a message from
quarantine.``

id: is composite key of quarantine item. E.g. `"test/9mUKVoMBTdm1qP6SFWgf"`
from the item above.``

**Delete messages from quarantine**``

**Endpoint** : `/api/v2/quarantine/domain/{domain_name}/delete_collection/`
**Endpoint** : `/api/v2/quarantine/domain/{domain_id}/delete_collection/```

**Method** : POST``

**Body** : JSON of the following format `{"id__in":"<comma separated list of
quarantine item ids>"}```

**Example** :``


​    
    POST /api/v2/quarantine/domain/example.com/delete_collection/
    {
      "id__in":"test/-j0wzosBS2HOxF2OZQIB,test/9mUKVoMBTdm1qP6SFWgf"
    }


**Response** :``


​    
    {deleted: 2}


**Recover messages from quarantine**``

**Endpoint** : `/api/v2/quarantine/domain/{domain_name}/recover_collection/`
**Endpoint** : `/api/v2/quarantine/domain/{domain_id}/recover_collection/```

**Method** : POST``

**Body** : JSON of the following format `{"id__in":"<single id or comma
separated list of quarantine item ids>"}```

**Example** :``


​    
    POST /api/v2/quarantine/domain/example.com/recover_collection/
    {
      "id__in":"test/-j0wzosBS2HOxF2OZQIB,test/9mUKVoMBTdm1qP6SFWgf"
    }


**Response** :``


​    
    {recovered: 2}


**Adding sender to allow list**``

**Endpoint** :
`/api/v2/quarantine/domain/{domain_name}/allow_sender_collection/{destination}/?recover=false`
**Endpoint** :
`/api/v2/quarantine/domain/{domain_id}/allow_sender_collection/{destination}/?recover=false```

**Method** : POST``

**Body** : JSON of the following format `{"id__in":"<single id or comma
separated list of quarantine item ids>"}```

Where `destination` can be `email_account` if sender need to be added to
recipient's allow list or `domain` if sender need to be added to domain's
allow list.``

**GET or POST params** :``

recover: If set to `true`, the message will be recovered from quarantine after
adding to allow list. Default is false.``

**Examples**``

Add 2 senders to recipient's allow list and recover the message:``


​    
    POST /api/v2/quarantine/domain/example.com/allow_sender_collection/email_account/?recover=true
    {
      "id__in":"test/-j0wzosBS2HOxF2OZQIB,test/9mUKVoMBTdm1qP6SFWgf"
    }


Add 2 senders to domain's allow list:``


​    
    POST /api/v2/quarantine/domain/example.com/allow_sender_collection/domain/
    {
      "id__in":"test/-j0wzosBS2HOxF2OZQIB,test/9mUKVoMBTdm1qP6SFWgf"
    }


**Fetch full message from quarantine**``

Full message will contain full headers and body of the message.``

**Endpoint** : `/api/v2/quarantine/{pk}/```

**Method** : GET``

Use `resource_uri` uri field of quarantine item to fetch full message. Or
build endpoint from above with `pk` of quarantine item.``

**Example** :``


​    
    GET /api/v2/quarantine/test/-j0wzosBS2HOxF2OZQIB/


**Response** :``


​    
        {
        "author": [
            "foxnews@inbox.foxnews.com"
        ],
        "blacklisted": false,
        "content_type": "Spam",
        "date": "15 Nov 2023, 03:18 PM",
        "domain_id": 1,
        "email_account_id": 1810080,
        "envelope_sender": "foxnewsletter_d0798ff036baced9f59ccd8819855cde766c4ee231dbb0f1@inbox.foxnews.com",
        "from_addr": "foxnews@inbox.foxnews.com",
        "has_attachments": false,
        "id": "test/-j0wzosBS2HOxF2OZQIB",
        "mail_from": "foxnewsletter_d0798ff036baced9f59ccd8819855cde766c4ee231dbb0f1@inbox.foxnews.com",
        "mail_id": "Y7QOahonjukF",
        "message": {
            "attachments": {},
            "date": "Wed, 15 Nov 2023 12:17:24 +0000",
            "headers": [
                [
                    "To",
                    "recipient@example.com"
                ],
                [
                    "X-Spam-Score",
                    "-12.731"
                ],
                [
                    "X-Envelope-To-Blocked",
                    "<recipient@example.com>"
                ],
                [
                    "Content-Type",
                    "text/html; charset=\"UTF-8\""
                ],
                [
                    "X-Envelope-To",
                    "<recipient@example.com>"
                ],
               ... the rest headers omitted for simplicity ...
            ],
            "payload": {
                "text/html": "html body of email message",
            }
        },
        "pk": "test/-j0wzosBS2HOxF2OZQIB",
        "rcpt_to": "recipient@example.com",
        "recipient": "recipient@example.com",
        "resource_uri": "/api/v2/quarantine/test/-j0wzosBS2HOxF2OZQIB/",
        "size": 31098,
        "spam_score": -12.731,
        "status": null,
        "subject": "Subject of email",
        "time_unix": 1700050692.227,
        "timestamp": "2023-11-15T12:18:12.227Z",
        "virusnames": []
    }


**Email Account Quarantine**``

Endpoint: `/api/v2/quarantine/email_account/{pk}/```

Endpoint: `/api/v2/quarantine/email_account/{email}/```

**Method** : GET``

**Parameters** :``

**Url placeholders** :``

  * pk (required): The primary key of the email account for which to retrieve quarantine messages.

or``

  * email (required): Email of account for which to retrieve quarantine messages.

GET params:``

  * label: Filter the messages by content type. Possible values are Spam, Spoof, Virus, Banned, BadMIME, Unchecked, Deleted, Recovered, Blocked.

**Response message format**``


​    
    {
        "author": [
        "foxnews@inbox.foxnews.com"
        ],
        "blacklisted": false,
        "content_type": "Spam",
        "date": "14 Nov 2023, 12:31 AM",
        "domain_id": 3,
        "email_account_id": 1,
        "envelope_sender": "foxnews_148ab4a67b269b58c03c0906340c459d4c7f77af4a1d50c2@inbox.foxnews.com",
        "from_addr": "foxnews@inbox.foxnews.com",
        "has_attachments": false,
        "id": "test/_z0wzosBS2HOxF2OZQIB",
        "mail_from": "foxnews_148ab4a67b269b58c03c0906340c459d4c7f77af4a1d50c2@inbox.foxnews.com",
        "mail_id": "EieNvTDw3Itr",
        "pk": "test/-j0wzosBS2HOxF2OZQIB",
        "rcpt_to": "u1@usercase.com",
        "recipient": "u1@usercase.com",
        "resource_uri": "/api/v2/quarantine/test/_z0wzosBS2HOxF2OZQIB/",
        "size": 6775,
        "spam_score": -16.151,
        "status": null,
        "subject": "IDALIA'S WRATH: Monster storm leaves 'severe damage' and flooding in coastal states",
        "time_unix": 1693438313.248,
        "timestamp": "2023-11-13T23:31:53.248000Z",
        "virusnames": []
    },


Where``

  * spam_level: The spam level of the message
  * content_type: One of Spam, Spoof, Virus, Banned, BadMIME, Unchecked, Deleted, Recovered, Blocked.
  * date: The date the message was received
  * mail_from: The envelope sender of the message
  * author: The from address of the message
  * resource_uri: The URI of the full message with body and headers
  * recipient: The recipient of the message
  * resource_uri: The URI of this quarantine item
  * size: The size of the message in bytes
  * subject: The subject of the message
  * status: 'D' for deleted, 'R' for recovered

**Examples**``

To fetch Spam messages for domain
"[user@example.com](mailto:user@example.com)":``


​    
    GET /api/v2/quarantine/email_account/user@example.com/?label=Spam


**Delete messages from email account's quarantine**``

**Endpoint** : `/api/v2/quarantine/email_account/{pk}/delete_collection/`
**Endpoint** : `/api/v2/quarantine/email_account/{email}/delete_collection/```

**Method** : POST``

**Body** : JSON of the following format `{"id__in":"<comma separated list of
quarantine item ids>"}```

**Example** :``


​    
    POST /api/v2/quarantine/email_account/user@example.com/delete_collection/
    {
      "id__in":"test/-j0wzosBS2HOxF2OZQIB,test/9mUKVoMBTdm1qP6SFWgf"
    }


**Response** :``


​    
    {deleted: 2}


**Recover messages from quarantine**``

**Endpoint** : `/api/v2/quarantine/email_account/{pk}/recover_collection/`
**Endpoint** :
`/api/v2/quarantine/email_account/{email}/recover_collection/```

**Method** : POST``

**Body** : JSON of the following format `{"id__in":"<single id or comma
separated list of quarantine item ids>"}```

**Example** :``


​    
    POST /api/v2/quarantine/email_account/user@example.com/recover_collection/
    {
      "id__in":"test/-j0wzosBS2HOxF2OZQIB,test/9mUKVoMBTdm1qP6SFWgf"
    }


**Response** :``


​    
    {recovered: 2}


**Adding sender to allow list**``

**Endpoint** :
`/api/v2/quarantine/email_account/{pk}/allow_sender_collection/{destination}/?recover=false`
**Endpoint** :
`/api/v2/quarantine/email_account/{email}/allow_sender_collection/{destination}/?recover=false```

**Method** : POST``

**Body** : JSON of the following format `{"id__in":"<single id or comma
separated list of quarantine item ids>"}```

Where `destination` can be `email_account` if sender need to be added to
recipient's allow list or `domain` if sender need to be added to domain's
allow list.``

**GET or POST params** :``

recover: If set to `true`, the message will be recovered from quarantine after
adding to allow list. Default is false.``

**Examples**``

Add 2 senders to recipient's allow list and recover the message:``


​    
    POST /api/v2/quarantine/email_account/user@example.com/allow_sender_collection/email_account/?recover=true
    {
      "id__in":"test/-j0wzosBS2HOxF2OZQIB,test/9mUKVoMBTdm1qP6SFWgf"
    }

