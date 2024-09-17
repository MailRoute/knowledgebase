---
created_at: 2013-02-18 18:45:17
date: 2022-03-13 18:23:17
description: A comprehensive technical guide on how to interact with the MailRoute
  API for domain management, including setting up MX records, configuring mail servers,
  defining user policies for spam/virus handling, and maintaining allow/block lists.
  Covers multiple API resources with request examples.
draft: true
params:
  author: Unknown
summary: This article provides detailed information on using the MailRoute API to
  manage domains, mail servers, user policies, and allow/block lists. It covers various
  API endpoints, request/response examples, and available parameters for creating,
  updating, and deleting domain-related resources.
tags: 
- API
title: API - (Part 4) - Domain Resource
---


## Domains

### The Domain Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/domain/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/domain/schema/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:20 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "ordering" : [
          "name",
          "created_at",
          "active",
          "hold_email"
       ],
       "fields" : {
          "bounce_unlisted" : {
             "unique" : false,
             "help_text" : "Boolean data. Ex: True",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "boolean",
             "default" : false
          },
          "name" : {
             "unique" : true,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "deliveryport" : {
             "unique" : false,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "integer",
             "default" : 25
          },
          "active" : {
             "unique" : false,
             "help_text" : "Boolean data. Ex: True",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "boolean",
             "default" : true
          },
          "resource_uri" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "hold_email" : {
             "unique" : false,
             "help_text" : "Boolean data. Ex: True",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "boolean",
             "default" : false
          },
          "created_at" : {
             "unique" : false,
             "help_text" : "A date & time as a string. Ex: \"2010-11-10T03:07:43\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "datetime",
             "default" : "No default provided."
          },
          "updated_at" : {
             "unique" : false,
             "help_text" : "A date & time as a string. Ex: \"2010-11-10T03:07:43\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "datetime",
             "default" : "No default provided."
          },
          "customer" : {
             "unique" : false,
             "help_text" : "A single related resource. Can be either a URI or set of nested resource data.",
             "related_type" : "to_one",
             "default" : "No default provided.",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "related"
          },
          "policy" : {
             "unique" : false,
             "help_text" : "A single related resource. Can be either a URI or set of nested resource data.",
             "related_type" : "to_one",
             "default" : "No default provided.",
             "readonly" : true,
             "nullable" : true,
             "blank" : false,
             "type" : "related"
          },
          "outbound_enabled" : {
             "unique" : false,
             "help_text" : "Boolean data. Ex: True",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "boolean",
             "default" : false
          },
          "id" : {
             "unique" : true,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "integer",
             "default" : ""
          }
       },
       "allowed_detail_http_methods" : [
          "get",
          "post",
          "put",
          "delete"
       ],
       "allowed_list_http_methods" : [
          "get",
          "post",
          "put",
          "delete"
       ],
       "filtering" : {
          "customer" : 2,
          "name" : 1
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Creating a Domain

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/domain/


#### Arguments

parameterrequireddefaultdescription

name | _required_ |  | String - The name of the domain  
---|---|---|---  
customer | _required_ |  | String - customer_uri  
active |  | false | Boolean - is the domain active and accepting mail?  
bounce_unlisted |  | false | Boolean - is email list complete, bounce email to
unlisted users?  
customer | _required_ |  | A single related resource. Can be either a URI or
set of nested resource data  
deliveryport |  | 25 | Integer - port for email delivery to domain mailservers  
hold_email |  | false | Boolean - is domain email deliver on hold?  
outbound_enabled |  | false | Boolean - is domain enabled for outbound mail
(may incur an extra cost)  
policy |  |  | A single related resource. Can be either a URI or set of nested
resource data  

#### Example Request


​    
    curl -s --dump-header - -X POST \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "customer" : "/api/v1/customer/157/",
               "name" : "testdomain.com"
            }' \
        https://admin.mailroute.net/api/v1/domain/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:21 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/domain/111/


​    
    {
       "bounce_unlisted" : false,
       "name" : "testdomain.com",
       "deliveryport" : 25,
       "active" : true,
       "resource_uri" : "/api/v1/domain/111/",
       "hold_email" : false,
       "created_at" : "Mon, 18 Feb 2013 10:10:21 -0800",
       "updated_at" : "Mon, 18 Feb 2013 10:10:21 -0800",
       "customer" : "/api/v1/customer/157/",
       "policy" : "/api/v1/policy_domain/177/",
       "outbound_enabled" : false,
       "absolute_url" : "/domain/111/",
       "id" : 111
    }


### Updating a Domain

#### Definition


​    
    PUT https://admin.mailroute.net/api/v1/domain/111/


#### Arguments

parameterrequireddefaultdescription

name | _required_ |  | String - The name of the domain  
---|---|---|---  
customer | _required_ |  | String - customer_uri  
active |  | false | Boolean - is the domain active and accepting mail?  
bounce_unlisted |  | false | Boolean - is email list complete, bounce email to
unlisted users?  
customer | _required_ |  | A single related resource. Can be either a URI or
set of nested resource data  
deliveryport |  | 25 | Integer - port for email delivery to domain mailservers  
hold_email |  | false | Boolean - is domain email deliver on hold?  
outbound_enabled |  | false | Boolean - is domain enabled for outbound mail
(may incur an extra cost)  
policy |  |  | A single related resource. Can be either a URI or set of nested
resource data  

#### Example Request


​    
    curl -s --dump-header - -X PUT \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "bounce_unlisted" : "true",
               "name" : "renamedtestdomain.com"
            }' \
        https://admin.mailroute.net/api/v1/domain/111/


#### Example Response


​    
    HTTP/1.0 202 ACCEPTED
    Date: Mon, 18 Feb 2013 18:10:22 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8


​    
    {
       "pk" : "111",
       "bounce_unlisted" : true,
       "name" : "renamedtestdomain.com",
       "deliveryport" : 25,
       "active" : true,
       "resource_uri" : "/api/v1/domain/111/",
       "hold_email" : false,
       "created_at" : "Mon, 18 Feb 2013 10:10:21 -0800",
       "updated_at" : "Mon, 18 Feb 2013 10:10:22 -0800",
       "customer" : "/api/v1/customer/157/",
       "policy" : "/api/v1/policy_domain/177/",
       "outbound_enabled" : false,
       "absolute_url" : "/domain/111/",
       "id" : 111
    }


### Listing Domains

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/domain/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/domain/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:23 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "objects" : [
          {
             "bounce_unlisted" : false,
             "name" : "asdfasdf.com",
             "deliveryport" : 25,
             "active" : true,
             "resource_uri" : "/api/v1/domain/105/",
             "hold_email" : false,
             "created_at" : "Thu, 14 Feb 2013 16:12:55 -0800",
             "updated_at" : "Thu, 14 Feb 2013 16:12:55 -0800",
             "customer" : "/api/v1/customer/149/",
             "policy" : "/api/v1/policy_domain/166/",
             "outbound_enabled" : false,
             "absolute_url" : "/domain/105/",
             "id" : 105
          },
          {
             "bounce_unlisted" : true,
             "name" : "renamedtestdomain.com",
             "deliveryport" : 25,
             "active" : true,
             "resource_uri" : "/api/v1/domain/111/",
             "hold_email" : false,
             "created_at" : "Mon, 18 Feb 2013 10:10:21 -0800",
             "updated_at" : "Mon, 18 Feb 2013 10:10:22 -0800",
             "customer" : "/api/v1/customer/157/",
             "policy" : "/api/v1/policy_domain/177/",
             "outbound_enabled" : false,
             "absolute_url" : "/domain/111/",
             "id" : 111
          }
       ],
       "meta" : {
          "previous" : null,
          "next" : null,
          "limit" : 20,
          "total_count" : 2,
          "offset" : 0
       }
    }


Deleting a Domain

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/domain/111/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/domain/111/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:46 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


### The DomainAlias Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/domain_alias/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/domain_alias/schema/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:23 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "ordering" : [
          "name",
          "created_at"
       ],
       "fields" : {
          "resource_uri" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "domain" : {
             "unique" : false,
             "help_text" : "A single related resource. Can be either a URI or set of nested resource data.",
             "related_type" : "to_one",
             "default" : "No default provided.",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "related"
          },
          "created_at" : {
             "unique" : false,
             "help_text" : "A date & time as a string. Ex: \"2010-11-10T03:07:43\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "datetime",
             "default" : "No default provided."
          },
          "updated_at" : {
             "unique" : false,
             "help_text" : "A date & time as a string. Ex: \"2010-11-10T03:07:43\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "datetime",
             "default" : "No default provided."
          },
          "name" : {
             "unique" : true,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "active" : {
             "unique" : false,
             "help_text" : "Boolean data. Ex: True",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "boolean",
             "default" : true
          },
          "id" : {
             "unique" : true,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "integer",
             "default" : ""
          }
       },
       "allowed_detail_http_methods" : [
          "get",
          "post",
          "put",
          "patch",
          "delete"
       ],
       "allowed_list_http_methods" : [
          "get",
          "post",
          "put",
          "patch",
          "delete"
       ],
       "filtering" : {
          "domain" : [
             "exact"
          ]
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Creating a DomainAlias

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/domain_alias/


#### Arguments

parameterrequireddefaultdescription

name | _required_ |  | String - The name of the domainalias  
---|---|---|---  
domain | _required_ |  | String - domain_uri  
active |  | false | Boolean - is the domain active and accepting mail?  

#### Example Request


​    
    curl -s --dump-header - -X POST \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "domain" : "/api/v1/domain/111/",
               "name" : "testalias.com"
            }' \
        https://admin.mailroute.net/api/v1/domain_alias/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:23 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/domain_alias/198/


​    
    {
       "resource_uri" : "/api/v1/domain_alias/198/",
       "domain" : "/api/v1/domain/111/",
       "created_at" : "Mon, 18 Feb 2013 10:10:23 -0800",
       "updated_at" : "Mon, 18 Feb 2013 10:10:23 -0800",
       "name" : "testalias.com",
       "active" : true,
       "id" : 198
    }


### Updating a DomainAlias

#### Definition


​    
    PUT https://admin.mailroute.net/api/v1/domain_alias/198/


#### Arguments

parameterrequireddefaultdescription

name | _required_ |  | String - The name of the domainalias  
---|---|---|---  
domain | _required_ |  | String - domain_uri  
active |  | false | Boolean - is the domain active and accepting mail?  

#### Example Request


​    
    curl -s --dump-header - -X PUT \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "name" : "renamedtestalias.com"
            }' \
        https://admin.mailroute.net/api/v1/domain_alias/198/


#### Example Response


​    
    HTTP/1.0 202 ACCEPTED
    Date: Mon, 18 Feb 2013 18:10:24 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8


​    
    {
       "resource_uri" : "/api/v1/domain_alias/198/",
       "domain" : "/api/v1/domain/111/",
       "created_at" : "Mon, 18 Feb 2013 10:10:23 -0800",
       "pk" : "198",
       "updated_at" : "Mon, 18 Feb 2013 10:10:24 -0800",
       "name" : "renamedtestalias.com",
       "active" : true,
       "id" : 198
    }


### Listing DomainAliases

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/domain_alias/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/domain_alias/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:24 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "objects" : [
          {
             "resource_uri" : "/api/v1/domain_alias/198/",
             "domain" : "/api/v1/domain/111/",
             "created_at" : "Mon, 18 Feb 2013 10:10:23 -0800",
             "updated_at" : "Mon, 18 Feb 2013 10:10:24 -0800",
             "name" : "renamedtestalias.com",
             "active" : true,
             "id" : 198
          }
       ],
       "meta" : {
          "previous" : null,
          "next" : null,
          "limit" : 20,
          "total_count" : 1,
          "offset" : 0
       }
    }


Deleting a DomainAlias

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/domain_alias/198/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/domain_alias/198/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:45 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


### The MailServer Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/mail_server/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/mail_server/schema/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:24 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "ordering" : [
          "server",
          "priority"
       ],
       "fields" : {
          "priority" : {
             "unique" : false,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "integer",
             "default" : 10
          },
          "sasl_password" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "resource_uri" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "created_at" : {
             "unique" : false,
             "help_text" : "A date & time as a string. Ex: \"2010-11-10T03:07:43\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "datetime",
             "default" : "No default provided."
          },
          "domain" : {
             "unique" : false,
             "help_text" : "A single related resource. Can be either a URI or set of nested resource data.",
             "related_type" : "to_one",
             "default" : "No default provided.",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "related"
          },
          "use_sasl" : {
             "unique" : false,
             "help_text" : "Boolean data. Ex: True",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "boolean",
             "default" : false
          },
          "updated_at" : {
             "unique" : false,
             "help_text" : "A date & time as a string. Ex: \"2010-11-10T03:07:43\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "datetime",
             "default" : "No default provided."
          },
          "sasl_login" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "id" : {
             "unique" : true,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "integer",
             "default" : ""
          },
          "server" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          }
       },
       "allowed_detail_http_methods" : [
          "get",
          "post",
          "put",
          "patch",
          "delete"
       ],
       "allowed_list_http_methods" : [
          "get",
          "post",
          "put",
          "patch",
          "delete"
       ],
       "filtering" : {
          "domain" : [
             "exact"
          ]
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Creating a MailServer

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/mail_server/


#### Arguments

parameterrequireddefaultdescription

server | _required_ |  | String - mailserver FQDN or IP address  
---|---|---|---  
domain | _required_ |  | String - domain_uri  
priority |  | 10 | Integer - mail server priority?  

#### Example Request


​    
    curl -s --dump-header - -X POST \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "priority" : 20,
               "domain" : "/api/v1/domain/111/",
               "server" : "mail.testdomain.com"
            }' \
        https://admin.mailroute.net/api/v1/mail_server/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:25 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/mail_server/86/


​    
    {
       "priority" : 20,
       "sasl_password" : null,
       "resource_uri" : "/api/v1/mail_server/86/",
       "created_at" : "Mon, 18 Feb 2013 10:10:25 -0800",
       "domain" : "/api/v1/domain/111/",
       "use_sasl" : false,
       "updated_at" : "Mon, 18 Feb 2013 10:10:25 -0800",
       "sasl_login" : null,
       "absolute_url" : "/mail_server/86/",
       "id" : 86,
       "server" : "mail.testdomain.com"
    }


### Updating a MailServer

#### Definition


​    
    PUT https://admin.mailroute.net/api/v1/mail_server/86/


#### Arguments

parameterrequireddefaultdescription

server | _required_ |  | String - mailserver FQDN or IP address  
---|---|---|---  
domain | _required_ |  | String - domain_uri  
priority |  | 10 | Integer - mail server priority?  

#### Example Request


​    
    curl -s --dump-header - -X PUT \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "priority" : 30,
               "server" : "renamedmail.testdomain.com"
            }' \
        https://admin.mailroute.net/api/v1/mail_server/86/


#### Example Response


​    
    HTTP/1.0 202 ACCEPTED
    Date: Mon, 18 Feb 2013 18:10:26 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8


​    
    {
       "priority" : 30,
       "pk" : "86",
       "sasl_password" : null,
       "resource_uri" : "/api/v1/mail_server/86/",
       "created_at" : "Mon, 18 Feb 2013 10:10:25 -0800",
       "domain" : "/api/v1/domain/111/",
       "use_sasl" : false,
       "updated_at" : "Mon, 18 Feb 2013 10:10:26 -0800",
       "sasl_login" : null,
       "absolute_url" : "/mail_server/86/",
       "id" : 86,
       "server" : "renamedmail.testdomain.com"
    }


### Listing MailServers

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/mail_server/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/mail_server/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:26 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "objects" : [
          {
             "priority" : 30,
             "sasl_password" : null,
             "resource_uri" : "/api/v1/mail_server/86/",
             "created_at" : "Mon, 18 Feb 2013 10:10:25 -0800",
             "domain" : "/api/v1/domain/111/",
             "use_sasl" : false,
             "updated_at" : "Mon, 18 Feb 2013 10:10:26 -0800",
             "sasl_login" : null,
             "absolute_url" : "/mail_server/86/",
             "id" : 86,
             "server" : "renamedmail.testdomain.com"
          }
       ],
       "meta" : {
          "previous" : null,
          "next" : null,
          "limit" : 20,
          "total_count" : 1,
          "offset" : 0
       }
    }


Deleting a MailServer

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/mail_server/86/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/mail_server/86/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:44 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


### The OutboundServer Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/outbound_server/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/outbound_server/schema/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:27 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "ordering" : [
          "server"
       ],
       "fields" : {
          "resource_uri" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "domain" : {
             "unique" : false,
             "help_text" : "A single related resource. Can be either a URI or set of nested resource data.",
             "related_type" : "to_one",
             "default" : "No default provided.",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "related"
          },
          "created_at" : {
             "unique" : false,
             "help_text" : "A date & time as a string. Ex: \"2010-11-10T03:07:43\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "datetime",
             "default" : "No default provided."
          },
          "updated_at" : {
             "unique" : false,
             "help_text" : "A date & time as a string. Ex: \"2010-11-10T03:07:43\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "datetime",
             "default" : "No default provided."
          },
          "server" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "id" : {
             "unique" : true,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "integer",
             "default" : ""
          }
       },
       "allowed_detail_http_methods" : [
          "get",
          "post",
          "put",
          "patch",
          "delete"
       ],
       "allowed_list_http_methods" : [
          "get",
          "post",
          "put",
          "patch",
          "delete"
       ],
       "filtering" : {
          "domain" : [
             "exact"
          ]
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Creating an OutboundServer

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/outbound_server/


#### Arguments

parameterrequireddefaultdescription

server | _required_ |  | String - mailserver IP Address  
---|---|---|---  
domain | _required_ |  | String - domain_uri  

#### Example Request


​    
    curl -s --dump-header - -X POST \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "domain" : "/api/v1/domain/111/",
               "server" : "111.111.111.111"
            }' \
        https://admin.mailroute.net/api/v1/outbound_server/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:27 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/outbound_server/81/


​    
    {
       "resource_uri" : "/api/v1/outbound_server/81/",
       "domain" : "/api/v1/domain/111/",
       "created_at" : "Mon, 18 Feb 2013 10:10:27 -0800",
       "updated_at" : "Mon, 18 Feb 2013 10:10:27 -0800",
       "server" : "111.111.111.111",
       "id" : 81
    }


### Updating an OutboundServer

#### Definition


​    
    PUT https://admin.mailroute.net/api/v1/outbound_server/81/


#### Arguments

parameterrequireddefaultdescription

server | _required_ |  | String - mailserver IP Address  
---|---|---|---  
domain | _required_ |  | String - domain_uri  

#### Example Request


​    
    curl -s --dump-header - -X PUT \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "server" : "123.123.123.123"
            }' \
        https://admin.mailroute.net/api/v1/outbound_server/81/


#### Example Response


​    
    HTTP/1.0 202 ACCEPTED
    Date: Mon, 18 Feb 2013 18:10:28 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8


​    
    {
       "resource_uri" : "/api/v1/outbound_server/81/",
       "domain" : "/api/v1/domain/111/",
       "created_at" : "Mon, 18 Feb 2013 10:10:27 -0800",
       "pk" : "81",
       "updated_at" : "Mon, 18 Feb 2013 10:10:28 -0800",
       "server" : "123.123.123.123",
       "id" : 81
    }


### Listing OutboundServers

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/outbound_server/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/outbound_server/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:28 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "objects" : [
          {
             "resource_uri" : "/api/v1/outbound_server/81/",
             "domain" : "/api/v1/domain/111/",
             "created_at" : "Mon, 18 Feb 2013 10:10:27 -0800",
             "updated_at" : "Mon, 18 Feb 2013 10:10:28 -0800",
             "server" : "123.123.123.123",
             "id" : 81
          }
       ],
       "meta" : {
          "previous" : null,
          "next" : null,
          "limit" : 20,
          "total_count" : 1,
          "offset" : 0
       }
    }


Deleting an OutboundServer

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/outbound_server/81/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/outbound_server/81/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:44 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


### The User Policy Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/policy_user/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/policy_user/schema/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:28 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "fields" : {
          "priority" : {
             "unique" : false,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "integer",
             "default" : 1
          },
          "spam_subject_tag3" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "spam_subject_tag" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "id" : {
             "unique" : true,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "integer",
             "default" : ""
          },
          "unchecked_lover" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "Y"
          },
          "addr_extension_virus" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "bad_header_quarantine_to" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "sql:"
          },
          "warnbadhrecip" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "N"
          },
          "warnbannedrecip" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "N"
          },
          "unchecked_quarantine_to" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "bypass_spam_checks" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "N"
          },
          "spam_quarantine_to" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "sql:"
          },
          "message_size_limit" : {
             "unique" : false,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "integer",
             "default" : "No default provided."
          },
          "bypass_virus_checks" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "N"
          },
          "email_account" : {
             "unique" : false,
             "help_text" : "A single related resource. Can be either a URI or set of nested resource data.",
             "related_type" : "to_one",
             "default" : "No default provided.",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "related"
          },
          "virus_quarantine_to" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "sql:"
          },
          "spam_kill_level" : {
             "unique" : false,
             "help_text" : "Floating point numeric data. Ex: 26.73",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "float",
             "default" : 7
          },
          "warnvirusrecip" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "N"
          },
          "addr_extension_bad_header" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "banned_quarantine_to" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "sql:"
          },
          "spam_quarantine_cutoff_level" : {
             "unique" : false,
             "help_text" : "Floating point numeric data. Ex: 26.73",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "float",
             "default" : "No default provided."
          },
          "spam_tag2_level" : {
             "unique" : false,
             "help_text" : "Floating point numeric data. Ex: 26.73",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "float",
             "default" : "No default provided."
          },
          "bypass_header_checks" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "Y"
          },
          "spam_subject_tag2" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "bad_header_lover" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "N"
          },
          "addr_extension_spam" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "spam_lover" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "N"
          },
          "banned_files_lover" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "N"
          },
          "virus_lover" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "N"
          },
          "bypass_banned_checks" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "N"
          },
          "spam_tag3_level" : {
             "unique" : false,
             "help_text" : "Floating point numeric data. Ex: 26.73",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "float",
             "default" : "No default provided."
          },
          "resource_uri" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "spam_tag_level" : {
             "unique" : false,
             "help_text" : "Floating point numeric data. Ex: 26.73",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "float",
             "default" : -9999
          },
          "addr_extension_banned" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          }
       },
       "allowed_detail_http_methods" : [
          "get",
          "post",
          "put"
       ],
       "allowed_list_http_methods" : [
          "get",
          "post",
          "put"
       ],
       "filtering" : {
          "domain" : [
             "exact"
          ]
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Updating a User Policy

#### Definition


​    
    PUT https://admin.mailroute.net/api/v1/policy_domain/177/


#### Arguments

parameterrequireddefaultdescription

user | _required_ |  | String - user_uri  
---|---|---|---  
priority |  | 1 | Integer - priority - higher priority takes precedence in
domain/user policy settings  
addr _extension_ bad_header |  |  | String - address extension - bad header  
addr _extension_ banned |  |  | String - address extension - banned file  
addr _extension_ spam |  |  | String - address extension - spam  
addr _extension_ virus |  |  | String - address extension - virus  
bad _header_ lover |  | N | Character - "Y\  
banned _files_ lover |  | N | Character - "Y\  
spam_lover |  | N | Character - "Y\  
unchecked_lover |  | N | Character - "Y\  
virus_lover |  | N | Character - "Y\  
bypass _banned_ checks |  | N | Character - "Y\  
bypass _header_ checks |  | Y | Character - "Y\  
bypass _spam_ checks |  | N | Character - "Y\  
bypass _virus_ checks |  | N | Character - "Y\  
bad _header_ quarantine_to |  | sql: | String - where to redirect bad hdr,
"sql:" for quarantine  
banned _quarantine_ to |  | sql: | String - where to redirect banned, "sql:"
for quarantine  
spam _quarantine_ to |  | sql: | String - where to redirect spam, "sql:" for
quarantine  
unchecked _quarantine_ to |  | sql: | String - where to redirect unchecked,
"sql:" for quarantine  
virus _quarantine_ to |  | sql: | String - where to redirect virus, "sql:" for
quarantine  
message _size_ limit |  |  | Integer - max size in bytes, 0 to disable  
spam _kill_ level |  | 7 | Float - score above which to quarantine spam  
spam _quarantine_ cutoff_level |  | NULL | Float - score above which email
isn't even quarantined  
spam _subject_ tag2 |  | NULL | String - prepended to subject of messages
scoring > spam _tag2_ level  
spam _subject_ tag3 |  | NULL | String - prepended to subject of messages
scoring > spam _tag3_ level  
spam _tag_ level |  | -9999 | Float - score above this adds X-Spam-* headers
to emails  
spam _tag2_ level |  | NULL | Float - score above this adds spam _subject_
tag2 text to subject, redirect to
[user+ext@domain.com](mailto:user+ext@domain.com) if addr _extension_ spam is
set  
spam _tag3_ level |  | NULL | Float - score above this adds spam _subject_
tag3 text to subject, redirect to
[user+ext@domain.com](mailto:user+ext@domain.com) if addr _extension_ spam is
set  
warnbadhrecip |  | N | Character - "Y\  
warnbannedrecip |  | N | Character - "Y\  
warnvirusrecip |  | N | Character - "Y\  

#### Example Request


​    
    curl -s --dump-header - -X PUT \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "spam_tag2_level" : 5.5,
               "spam_subject_tag2" : "Updated spam_subject_tag2",
               "spam_kill_level" : 9
            }' \
        https://admin.mailroute.net/api/v1/policy_domain/177/


#### Example Response


​    
    HTTP/1.0 202 ACCEPTED
    Date: Mon, 18 Feb 2013 18:10:29 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8


​    
    {
       "priority" : 5,
       "spam_subject_tag3" : null,
       "spam_subject_tag" : null,
       "id" : 177,
       "unchecked_lover" : "Y",
       "addr_extension_virus" : null,
       "bad_header_quarantine_to" : "sql:",
       "warnbadhrecip" : "N",
       "warnbannedrecip" : "N",
       "unchecked_quarantine_to" : null,
       "is_default" : false,
       "bypass_spam_checks" : "N",
       "spam_quarantine_to" : "sql:",
       "message_size_limit" : 0,
       "bypass_virus_checks" : "N",
       "virus_quarantine_to" : "sql:",
       "spam_kill_level" : 9,
       "warnvirusrecip" : "N",
       "addr_extension_bad_header" : null,
       "domain" : "/api/v1/domain/111/",
       "banned_quarantine_to" : "sql:",
       "spam_quarantine_cutoff_level" : null,
       "spam_tag2_level" : 5.5,
       "bypass_header_checks" : "Y",
       "spam_subject_tag2" : "Updated spam_subject_tag2",
       "bad_header_lover" : "N",
       "addr_extension_spam" : null,
       "pk" : "177",
       "spam_lover" : "N",
       "banned_files_lover" : "N",
       "virus_lover" : "N",
       "bypass_banned_checks" : "N",
       "spam_tag3_level" : null,
       "resource_uri" : "/api/v1/policy_domain/177/",
       "spam_tag_level" : -9999,
       "addr_extension_banned" : null
    }


### The Domain Allow and Block lists Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/wblist/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/wblist/schema/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:29 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "fields" : {
          "resource_uri" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "domain" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "wb" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "email_account" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "rid" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "id" : {
             "unique" : true,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "integer",
             "default" : ""
          }
       },
       "allowed_detail_http_methods" : [
          "get",
          "post",
          "delete"
       ],
       "allowed_list_http_methods" : [
          "get",
          "post",
          "delete"
       ],
       "filtering" : {
          "domain" : [
             "exact"
          ],
          "wb" : [
             "exact"
          ],
          "email_account" : [
             "exact"
          ]
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Creating a Domain Allow and Block lists

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/wblist/


#### Arguments

parameterrequireddefaultdescription

domain | _required_ |  | String - domain_uri  
---|---|---|---  
email | _required_ |  | String - address to be whitelisted  
wb | _required_ |  | Char - W  

#### Example Request


​    
    curl -s --dump-header - -X POST \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "email" : "whitelist.com",
               "domain" : "/api/v1/domain/111/",
               "wb" : "w"
            }' \
        https://admin.mailroute.net/api/v1/wblist/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:29 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/wblist/77/


​    
    {
       "resource_uri" : "/api/v1/wblist/77/",
       "email" : "whitelist.com",
       "domain" : null,
       "wb" : "w",
       "email_account" : null,
       "rid" : "1110000000",
       "id" : 77
    }


Deleting a Domain Allow and Block lists

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/wblist/77/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/wblist/77/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:43 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


### The Account Notification Task Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/notification_account_task/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/notification_account_task/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:30 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "objects" : [],
       "meta" : {
          "previous" : null,
          "next" : null,
          "limit" : 20,
          "total_count" : 0,
          "offset" : 0
       }
    }


### Updating an Account Notification Task

#### Definition


​    
    PUT https://admin.mailroute.net/api/v1


#### Arguments

parameterrequireddefaultdescription

account | _required_ |  | String - account_uri  
---|---|---|---  
enable_default |  | true | Boolean - use the domain-wide settings (only
applies to user notification task)  
enabled |  | false | Boolean - enable sending of notifications  
mon |  | true | Boolean - send on this day  
tue |  | true | Boolean - send on this day  
wed |  | true | Boolean - send on this day  
thu |  | true | Boolean - send on this day  
fri |  | true | Boolean - send on this day  
sat |  | false | Boolean - send on this day  
sun |  | false | Boolean - send on this day  

#### Example Request


​    
    curl -s --dump-header - -X PUT \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "sun" : "true",
               "enable_default" : "false",
               "account" : "/api/v1/domain/111/",
               "sat" : "true",
               "enabled" : "true"
            }' \
        https://admin.mailroute.net/api/v1


#### Example Response


​    
    HTTP/1.0 301 MOVED PERMANENTLY
    Date: Mon, 18 Feb 2013 18:10:30 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Content-Type: text/html; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/


[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

