---
created_at: 2013-02-18 18:45:13
date: 2016-07-31 22:12:50
description: A technical guide covering the API schema, methods (GET, POST, PUT, DELETE)
  and parameters for creating, updating, listing and deleting customer resources,
  contact details, and admin users in the MailRoute email management system.
draft: true
params:
  author: Unknown
summary: The article provides detailed information on API endpoints and request/response
  examples for managing customers, customer contacts, and customer admins in the MailRoute
  platform.
tags: 
- API
title: API - (Part 3) - Customer Resource
---


## Customers

### The Customer Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/customer/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/customer/schema/


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
          "is_full_user_list" : {
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
          },
          "reported_user_count" : {
             "unique" : false,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : true,
             "blank" : false,
             "type" : "integer",
             "default" : "No default provided."
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
          "name" : 1,
          "reseller" : [
             "exact"
          ]
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Creating a Customer

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/customer/


#### Arguments

parameterrequireddefaultdescription

name | _required_ |  | String - The name of the Customer  
---|---|---|---  
reseller | _required_ |  | String - reseller_uri  

#### Example Request


​    
    curl -s --dump-header - -X POST \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "name" : "TestCustomer",
               "reseller" : "/api/v1/reseller/371/"
            }' \
        https://admin.mailroute.net/api/v1/customer/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:17 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/customer/157/


​    
    {
       "is_full_user_list" : false,
       "name" : "TestCustomer",
       "branding_info" : "/api/v1/brandinginfo/532/",
       "resource_uri" : "/api/v1/customer/157/",
       "created_at" : "Mon, 18 Feb 2013 10:10:15 -0800",
       "allow_branding" : false,
       "updated_at" : "Mon, 18 Feb 2013 10:10:17 -0800",
       "absolute_url" : "/customer/157/",
       "id" : 157,
       "reported_user_count" : null,
       "reseller" : "/api/v1/reseller/371/"
    }


### Updating a Customer

#### Definition


​    
    PUT https://admin.mailroute.net/api/v1/customer/157/


#### Arguments

parameterrequireddefaultdescription

name | _required_ |  | String - The name of the Customer  
---|---|---|---  
reseller | _required_ |  | String - reseller_uri  

#### Example Request


​    
    curl -s --dump-header - -X PUT \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "name" : "NewCustomer"
            }' \
        https://admin.mailroute.net/api/v1/customer/157/


#### Example Response


​    
    HTTP/1.0 202 ACCEPTED
    Date: Mon, 18 Feb 2013 18:10:18 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8


​    
    {
       "is_full_user_list" : false,
       "pk" : "157",
       "name" : "NewCustomer",
       "branding_info" : "/api/v1/brandinginfo/532/",
       "resource_uri" : "/api/v1/customer/157/",
       "created_at" : "Mon, 18 Feb 2013 10:10:15 -0800",
       "allow_branding" : false,
       "updated_at" : "Mon, 18 Feb 2013 10:10:17 -0800",
       "absolute_url" : "/customer/157/",
       "id" : 157,
       "reported_user_count" : null,
       "reseller" : "/api/v1/reseller/371/"
    }


### Listing Customers

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/customer/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/customer/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:18 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "objects" : [
          {
             "is_full_user_list" : false,
             "name" : "asdfasdf.com",
             "branding_info" : "/api/v1/brandinginfo/506/",
             "resource_uri" : "/api/v1/customer/149/",
             "created_at" : "Thu, 14 Feb 2013 16:12:45 -0800",
             "allow_branding" : false,
             "updated_at" : "Thu, 14 Feb 2013 16:12:55 -0800",
             "absolute_url" : "/customer/149/",
             "id" : 149,
             "reported_user_count" : null,
             "reseller" : "/api/v1/reseller/253/"
          },
          {
             "is_full_user_list" : false,
             "name" : "NewCustomer",
             "branding_info" : "/api/v1/brandinginfo/532/",
             "resource_uri" : "/api/v1/customer/157/",
             "created_at" : "Mon, 18 Feb 2013 10:10:15 -0800",
             "allow_branding" : false,
             "updated_at" : "Mon, 18 Feb 2013 10:10:17 -0800",
             "absolute_url" : "/customer/157/",
             "id" : 157,
             "reported_user_count" : null,
             "reseller" : "/api/v1/reseller/371/"
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


Deleting a Customer

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/customer/157/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/customer/157/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:48 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


### The Customer Contact Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/contact_customer/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/contact_customer/schema/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:19 GMT
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
          "id" : {
             "unique" : true,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : false,
             "blank" : true,
             "type" : "integer",
             "default" : ""
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
          "customer" : [
             "exact"
          ]
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Creating a Customer Contact

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/contact_customer/


#### Arguments

parameterrequireddefaultdescription

email | _required_ |  | String - Email Address  
---|---|---|---  
customer | _required_ |  | String - customer_uri  
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
               "customer" : "/api/v1/customer/157/",
               "last_name" : "LastName",
               "first_name" : "FirstName"
            }' \
        https://admin.mailroute.net/api/v1/contact_customer/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:19 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/contact_customer/314/


​    
    {
       "state" : "",
       "last_name" : "LastName",
       "is_technical" : true,
       "email" : "email@domain.com",
       "city" : "",
       "created_at" : "Mon, 18 Feb 2013 10:10:19 -0800",
       "is_emergency" : false,
       "id" : 314,
       "address" : null,
       "is_billing" : false,
       "country" : "",
       "zipcode" : null,
       "phone" : null,
       "address2" : null,
       "resource_uri" : "/api/v1/contact_customer/314/",
       "updated_at" : "Mon, 18 Feb 2013 10:10:19 -0800",
       "customer" : "/api/v1/customer/157/",
       "absolute_url" : "/contacts/customer/314/",
       "first_name" : "FirstName"
    }


### Updating a Customer Contact

#### Definition


​    
    PUT https://admin.mailroute.net/api/v1/contact_customer/314/


#### Arguments

parameterrequireddefaultdescription

email | _required_ |  | String - Email Address  
---|---|---|---  
customer | _required_ |  | String - customer_uri  
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
               "customer" : "/api/v1/customer/157/",
               "last_name" : "NewLastName",
               "first_name" : "NewFirstName",
               "is_billing" : "true"
            }' \
        https://admin.mailroute.net/api/v1/contact_customer/314/


#### Example Response


​    
    HTTP/1.0 202 ACCEPTED
    Date: Mon, 18 Feb 2013 18:10:20 GMT
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
       "created_at" : "Mon, 18 Feb 2013 10:10:19 -0800",
       "is_emergency" : false,
       "id" : 314,
       "address" : null,
       "is_billing" : true,
       "country" : "",
       "pk" : "314",
       "zipcode" : null,
       "phone" : null,
       "address2" : null,
       "resource_uri" : "/api/v1/contact_customer/314/",
       "updated_at" : "Mon, 18 Feb 2013 10:10:20 -0800",
       "customer" : "/api/v1/customer/157/",
       "absolute_url" : "/contacts/customer/314/",
       "first_name" : "NewFirstName"
    }


### Listing Customer Contacts

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/customer/157/contacts/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/customer/157/contacts/


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
       "objects" : [
          {
             "state" : "",
             "last_name" : "NewLastName",
             "is_technical" : true,
             "email" : "newemail@domain.com",
             "city" : "",
             "created_at" : "Mon, 18 Feb 2013 10:10:19 -0800",
             "is_emergency" : false,
             "id" : 314,
             "address" : null,
             "is_billing" : true,
             "country" : "",
             "zipcode" : null,
             "phone" : null,
             "address2" : null,
             "resource_uri" : "/api/v1/contact_customer/314/",
             "updated_at" : "Mon, 18 Feb 2013 10:10:20 -0800",
             "customer" : "/api/v1/customer/157/",
             "absolute_url" : "/contacts/customer/314/",
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


Deleting a Customer Contact

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/contact_customer/314/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/contact_customer/314/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:47 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


### The Customer Admin Object

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
    Date: Mon, 18 Feb 2013 18:10:18 GMT
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
             "default" : "Mon, 18 Feb 2013 10:10:18 -0800"
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
             "default" : "Mon, 18 Feb 2013 10:10:18 -0800"
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


### Creating a Customer Admin

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/admins/customer/157/


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
               "customer" : "/api/v1/customer/157/"
            }' \
        https://admin.mailroute.net/api/v1/admins/customer/157/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:18 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/admins/customer/157/admin/50/


​    
    {
       "last_login" : "Mon, 18 Feb 2013 10:10:13 -0800",
       "send_welcome" : null,
       "username" : "email@domain.com",
       "date_joined" : "Mon, 18 Feb 2013 10:10:13 -0800",
       "email" : "email@domain.com",
       "resource_uri" : "/api/v1/admins/customer/157/admin/50/",
       "is_active" : true,
       "customer" : null,
       "id" : 50,
       "reseller" : null
    }


### Listing Customer Admins

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/admins/customer/157/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/admins/customer/157/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:19 GMT
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
             "resource_uri" : "/api/v1/admins/customer/157/admin/50/",
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


Deleting a Customer Admin

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/admins/customer/157/admin/50/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/admins/customer/157/admin/50/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:47 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

[888.485.7726](tel:888.485.7726)

