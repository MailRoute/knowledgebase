---
created_at: 2013-02-18 18:45:10
date: 2016-07-31 22:12:51
description: Learn how to leverage the MailRoute API to programmatically manage resellers,
  contacts, and administrators, including creating new entities, updating existing
  ones, listing available resources, and deleting unnecessary records.
draft: true
params:
  author: Unknown
summary: This article provides detailed information and examples on how to use the
  API to manage resellers, reseller contacts, and reseller administrators in the MailRoute
  system. It covers creating, updating, listing, and deleting resellers, reseller
  contacts, and reseller administrators via API calls.
tags: 
- API
title: API - (Part 2) - Reseller Resource
---


## Resellers

### The Reseller Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/reseller/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/reseller/schema/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:11 GMT
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
          "created_at" : {
             "unique" : false,
             "help_text" : "A date & time as a string. Ex: \"2010-11-10T03:07:43\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "datetime",
             "default" : "No default provided."
          },
          "allow_customer_branding" : {
             "unique" : false,
             "help_text" : "Boolean data. Ex: True",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "boolean",
             "default" : false
          },
          "allow_branding" : {
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
          "name" : {
             "unique" : true,
             "help_text" : "hi",
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
          },
          "branding_info" : {
             "unique" : false,
             "help_text" : "A single related resource. Can be either a URI or set of nested resource data.",
             "related_type" : "to_one",
             "default" : "No default provided.",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "related"
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
          "name" : 1
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Creating a Reseller

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/reseller/


#### Arguments

parameterrequireddefaultdescription

name | _required_ |  | String - The name of the Reseller  
---|---|---|---  

#### Example Request


​    
    curl -s --dump-header - -X POST \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "name" : "TestReseller"
            }' \
        https://admin.mailroute.net/api/v1/reseller/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:11 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/reseller/371/


​    
    {
       "resource_uri" : "/api/v1/reseller/371/",
       "created_at" : "Mon, 18 Feb 2013 10:10:11 -0800",
       "allow_customer_branding" : false,
       "allow_branding" : false,
       "updated_at" : "Mon, 18 Feb 2013 10:10:11 -0800",
       "name" : "TestReseller",
       "absolute_url" : "/reseller/371/",
       "id" : 371,
       "branding_info" : "/api/v1/brandinginfo/531/"
    }


### Updating a Reseller

#### Definition


​    
    PUT https://admin.mailroute.net/api/v1/reseller/371/


#### Arguments

parameterrequireddefaultdescription

name | _required_ |  | String - The name of the Reseller  
---|---|---|---  

#### Example Request


​    
    curl -s --dump-header - -X PUT \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "name" : "NewReseller"
            }' \
        https://admin.mailroute.net/api/v1/reseller/371/


#### Example Response


​    
    HTTP/1.0 202 ACCEPTED
    Date: Mon, 18 Feb 2013 18:10:12 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8


​    
    {
       "pk" : "371",
       "allow_customer_branding" : false,
       "name" : "NewReseller",
       "branding_info" : "/api/v1/brandinginfo/531/",
       "resource_uri" : "/api/v1/reseller/371/",
       "created_at" : "Mon, 18 Feb 2013 10:10:11 -0800",
       "allow_branding" : false,
       "updated_at" : "Mon, 18 Feb 2013 10:10:12 -0800",
       "absolute_url" : "/reseller/371/",
       "id" : 371
    }


### Listing Resellers

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/reseller/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/reseller/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:12 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "objects" : [
          {
             "resource_uri" : "/api/v1/reseller/45/",
             "created_at" : "Tue, 5 Feb 2013 23:51:14 -0800",
             "allow_customer_branding" : false,
             "allow_branding" : false,
             "updated_at" : "Tue, 5 Feb 2013 23:51:14 -0800",
             "name" : "asdfasdf.com",
             "absolute_url" : "/reseller/45/",
             "id" : 45,
             "branding_info" : "/api/v1/brandinginfo/45/"
          },
          {
             "resource_uri" : "/api/v1/reseller/353/",
             "created_at" : "Wed, 13 Feb 2013 16:30:02 -0800",
             "allow_customer_branding" : false,
             "allow_branding" : true,
             "updated_at" : "Thu, 14 Feb 2013 15:34:26 -0800",
             "name" : "Island",
             "absolute_url" : "/reseller/353/",
             "id" : 353,
             "branding_info" : "/api/v1/brandinginfo/501/"
          },
          {
             "resource_uri" : "/api/v1/reseller/1/",
             "created_at" : "Mon, 4 Feb 2013 21:11:05 -0800",
             "allow_customer_branding" : false,
             "allow_branding" : false,
             "updated_at" : "Wed, 12 Dec 2012 00:00:00 -0800",
             "name" : "MailRoute, Inc.",
             "absolute_url" : "/reseller/1/",
             "id" : 1,
             "branding_info" : "/api/v1/brandinginfo/1/"
          },
          {
             "resource_uri" : "/api/v1/reseller/371/",
             "created_at" : "Mon, 18 Feb 2013 10:10:11 -0800",
             "allow_customer_branding" : false,
             "allow_branding" : false,
             "updated_at" : "Mon, 18 Feb 2013 10:10:12 -0800",
             "name" : "NewReseller",
             "absolute_url" : "/reseller/371/",
             "id" : 371,
             "branding_info" : "/api/v1/brandinginfo/531/"
          },
          {
             "resource_uri" : "/api/v1/reseller/253/",
             "created_at" : "Sun, 10 Feb 2013 17:01:38 -0800",
             "allow_customer_branding" : false,
             "allow_branding" : false,
             "updated_at" : "Thu, 14 Feb 2013 16:12:47 -0800",
             "name" : "TestCustomer2",
             "absolute_url" : "/reseller/253/",
             "id" : 253,
             "branding_info" : "/api/v1/brandinginfo/333/"
          }
       ],
       "meta" : {
          "previous" : null,
          "next" : null,
          "limit" : 20,
          "total_count" : 5,
          "offset" : 0
       }
    }


Deleting a Reseller

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/reseller/371/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/reseller/371/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:51 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


### The Reseller Contact Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/contact_reseller/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/contact_reseller/schema/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:13 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "ordering" : [
          "first_name",
          "last_name",
          "email",
          "is_technical",
          "is_billing",
          "is_emergency"
       ],
       "fields" : {
          "state" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "string",
             "default" : ""
          },
          "last_name" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "string",
             "default" : ""
          },
          "is_technical" : {
             "unique" : false,
             "help_text" : "Boolean data. Ex: True",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "boolean",
             "default" : false
          },
          "email" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "city" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "string",
             "default" : ""
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
          "is_emergency" : {
             "unique" : false,
             "help_text" : "Boolean data. Ex: True",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "boolean",
             "default" : false
          },
          "address" : {
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
          "reseller" : {
             "unique" : false,
             "help_text" : "A single related resource. Can be either a URI or set of nested resource data.",
             "related_type" : "to_one",
             "default" : "No default provided.",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "related"
          },
          "is_billing" : {
             "unique" : false,
             "help_text" : "Boolean data. Ex: True",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "boolean",
             "default" : false
          },
          "country" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "string",
             "default" : ""
          },
          "zipcode" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "phone" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "address2" : {
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
          "updated_at" : {
             "unique" : false,
             "help_text" : "A date & time as a string. Ex: \"2010-11-10T03:07:43\"",
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "datetime",
             "default" : "No default provided."
          },
          "first_name" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "string",
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
          "email" : 1,
          "reseller" : [
             "exact"
          ]
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Creating a Reseller Contact

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/contact_reseller/


#### Arguments

parameterrequireddefaultdescription

email | _required_ |  | String - Email Address  
---|---|---|---  
reseller | _required_ |  | String - reseller_uri  
first_name |  |  | String  
last_name |  |  | String  
address |  |  | String  
address2 |  |  | String  
city |  |  | String  
state |  |  | String  
zipcode |  |  | String  
country |  |  | String  
phone |  |  | String  
is_billing |  | false | Boolean - is a billing contact  
is_emergency |  | false | Boolean - is an emergency contact  
is_technical |  | false | Boolean - is a technical contact  

#### Example Request


​    
    curl -s --dump-header - -X POST \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "is_technical" : "true",
               "email" : "email@domain.com",
               "last_name" : "LastName",
               "first_name" : "FirstName",
               "reseller" : "/api/v1/reseller/371/"
            }' \
        https://admin.mailroute.net/api/v1/contact_reseller/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:14 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/contact_reseller/313/


​    
    {
       "state" : "",
       "last_name" : "LastName",
       "is_technical" : true,
       "email" : "email@domain.com",
       "city" : "",
       "created_at" : "Mon, 18 Feb 2013 10:10:14 -0800",
       "is_emergency" : false,
       "id" : 313,
       "address" : null,
       "reseller" : "/api/v1/reseller/371/",
       "is_billing" : false,
       "country" : "",
       "zipcode" : null,
       "phone" : null,
       "address2" : null,
       "resource_uri" : "/api/v1/contact_reseller/313/",
       "updated_at" : "Mon, 18 Feb 2013 10:10:14 -0800",
       "absolute_url" : "/contacts/reseller/313/",
       "first_name" : "FirstName"
    }


### Updating a Reseller Contact

#### Definition


​    
    PUT https://admin.mailroute.net/api/v1/contact_reseller/313/


#### Arguments

parameterrequireddefaultdescription

email | _required_ |  | String - Email Address  
---|---|---|---  
reseller | _required_ |  | String - reseller_uri  
first_name |  |  | String  
last_name |  |  | String  
address |  |  | String  
address2 |  |  | String  
city |  |  | String  
state |  |  | String  
zipcode |  |  | String  
country |  |  | String  
phone |  |  | String  
is_billing |  | false | Boolean - is a billing contact  
is_emergency |  | false | Boolean - is an emergency contact  
is_technical |  | false | Boolean - is a technical contact  

#### Example Request


​    
    curl -s --dump-header - -X PUT \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "email" : "newemail@domain.com",
               "last_name" : "NewLastName",
               "first_name" : "NewFirstName",
               "is_billing" : "true",
               "reseller" : "/api/v1/reseller/371/"
            }' \
        https://admin.mailroute.net/api/v1/contact_reseller/313/


#### Example Response


​    
    HTTP/1.0 202 ACCEPTED
    Date: Mon, 18 Feb 2013 18:10:15 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8


​    
    {
       "state" : "",
       "last_name" : "NewLastName",
       "is_technical" : true,
       "email" : "newemail@domain.com",
       "city" : "",
       "created_at" : "Mon, 18 Feb 2013 10:10:14 -0800",
       "is_emergency" : false,
       "id" : 313,
       "address" : null,
       "reseller" : "/api/v1/reseller/371/",
       "is_billing" : true,
       "country" : "",
       "pk" : "313",
       "zipcode" : null,
       "phone" : null,
       "address2" : null,
       "resource_uri" : "/api/v1/contact_reseller/313/",
       "updated_at" : "Mon, 18 Feb 2013 10:10:14 -0800",
       "absolute_url" : "/contacts/reseller/313/",
       "first_name" : "NewFirstName"
    }


### Listing Reseller Contacts

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/reseller/371/contacts/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/reseller/371/contacts/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:15 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "objects" : [
          {
             "state" : "",
             "last_name" : "NewLastName",
             "is_technical" : true,
             "email" : "newemail@domain.com",
             "city" : "",
             "created_at" : "Mon, 18 Feb 2013 10:10:14 -0800",
             "is_emergency" : false,
             "id" : 313,
             "address" : null,
             "reseller" : "/api/v1/reseller/371/",
             "is_billing" : true,
             "country" : "",
             "zipcode" : null,
             "phone" : null,
             "address2" : null,
             "resource_uri" : "/api/v1/contact_reseller/313/",
             "updated_at" : "Mon, 18 Feb 2013 10:10:14 -0800",
             "absolute_url" : "/contacts/reseller/313/",
             "first_name" : "NewFirstName"
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


Deleting a Reseller Contact

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/contact_reseller/313/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/contact_reseller/313/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:49 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


### The Reseller Admin Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/admins/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/admins/schema/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:12 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "ordering" : [
          "username",
          "date_joined",
          "last_login"
       ],
       "fields" : {
          "last_login" : {
             "unique" : false,
             "help_text" : "A date & time as a string. Ex: \"2010-11-10T03:07:43\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "datetime",
             "default" : "Mon, 18 Feb 2013 10:10:12 -0800"
          },
          "send_welcome" : {
             "unique" : false,
             "help_text" : "Boolean data. Ex: True",
             "readonly" : false,
             "nullable" : true,
             "blank" : true,
             "type" : "boolean",
             "default" : "No default provided."
          },
          "username" : {
             "unique" : true,
             "help_text" : "Required. 30 characters or fewer. Letters, numbers and @/./+/-/_ characters",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "date_joined" : {
             "unique" : false,
             "help_text" : "A date & time as a string. Ex: \"2010-11-10T03:07:43\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "datetime",
             "default" : "Mon, 18 Feb 2013 10:10:12 -0800"
          },
          "email" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "string",
             "default" : ""
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
          "is_active" : {
             "unique" : false,
             "help_text" : "Designates whether this user should be treated as active. Unselect this instead of deleting accounts.",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "boolean",
             "default" : true
          },
          "customer" : {
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
          "reseller" : {
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
          "delete"
       ],
       "allowed_list_http_methods" : [
          "get",
          "post",
          "delete"
       ],
       "filtering" : {
          "customer" : [
             "exact"
          ],
          "reseller" : [
             "exact"
          ]
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Creating a Reseller Admin

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/admins/reseller/371/


#### Arguments

parameterrequireddefaultdescription

email | _required_ |  | String - Email Address  
---|---|---|---  
send_welcome |  | false | Boolean - send a welcome email to this new admin  

#### Example Request


​    
    curl -s --dump-header - -X POST \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "email" : "email@domain.com",
               "reseller" : "/api/v1/reseller/371/"
            }' \
        https://admin.mailroute.net/api/v1/admins/reseller/371/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:13 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/admins/reseller/371/admin/50/


​    
    {
       "last_login" : "Mon, 18 Feb 2013 10:10:13 -0800",
       "send_welcome" : null,
       "username" : "email@domain.com",
       "date_joined" : "Mon, 18 Feb 2013 10:10:13 -0800",
       "email" : "email@domain.com",
       "resource_uri" : "/api/v1/admins/reseller/371/admin/50/",
       "is_active" : true,
       "customer" : null,
       "id" : 50,
       "reseller" : null
    }


### Listing Reseller Admins

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/admins/reseller/371/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/admins/reseller/371/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:13 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "objects" : [
          {
             "last_login" : "Mon, 18 Feb 2013 10:10:13 -0800",
             "send_welcome" : null,
             "username" : "email@domain.com",
             "date_joined" : "Mon, 18 Feb 2013 10:10:13 -0800",
             "email" : "email@domain.com",
             "resource_uri" : "/api/v1/admins/reseller/371/admin/50/",
             "is_active" : true,
             "customer" : null,
             "id" : 50,
             "reseller" : null
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


Deleting a Reseller Admin

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/admins/reseller/371/admin/50/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/admins/reseller/371/admin/50/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:50 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

