---
created_at: 2013-02-18 18:45:21
date: 2024-03-01 14:10:23
description: A comprehensive technical guide on configuring and managing email accounts
  via the Email Account Resource API, covering CRUD operations for accounts, aliases,
  allow/block lists, user policies, and notification schedules. Ideal for developers
  integrating with the email platform.
draft: true
params:
  author: Unknown
summary: The article provides an overview of the Email Account Resource API endpoints,
  including details on how to create, update, list, and delete email accounts, aliases,
  and whitelists/blacklists. It also covers updating user policy settings and managing
  email account notification tasks.
tags: 
- API
title: API - (Part 5) - Email Account Resource
---


## Email Accounts

### The Email Account Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/email_account/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/email_account/schema/


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
       "ordering" : [
          "localpart",
          "priority",
          "domain",
          "created_at"
       ],
       "fields" : {
          "priority" : {
             "unique" : false,
             "help_text" : "Integer data. Ex: 2673",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "integer",
             "default" : 7
          },
          "localpart" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "No default provided."
          },
          "change_pwd" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : true,
             "type" : "string",
             "default" : "No default provided."
          },
          "create_opt" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : true,
             "blank" : true,
             "type" : "string",
             "default" : "No default provided."
          },
          "contact" : {
             "unique" : false,
             "help_text" : "A single related resource. Can be either a URI or set of nested resource data.",
             "related_type" : "to_one",
             "default" : "No default provided.",
             "readonly" : true,
             "nullable" : true,
             "blank" : false,
             "type" : "related"
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
             "readonly" : true,
             "nullable" : false,
             "blank" : false,
             "type" : "related"
          },
          "notification_task" : {
             "unique" : false,
             "help_text" : "A single related resource. Can be either a URI or set of nested resource data.",
             "related_type" : "to_one",
             "default" : "No default provided.",
             "readonly" : true,
             "nullable" : true,
             "blank" : false,
             "type" : "related"
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
          "localpart" : 1,
          "domain" : 2,
          "id" : [
             "in"
          ]
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Creating an Email Account

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/email_account/


#### Arguments

parameterrequireddefaultdescription

localpart | _required_ |  | String - the localpart of the email address  
---|---|---|---  
domain | _required_ |  | String - domain_uri  
create_opt | _required_ |  | String - 'generate_pwd'  
password |  |  | String  
send_welcome |  | false | Boolean - Send welcome email on creation of account  

#### Example Request


​    
    curl -s --dump-header - -X POST \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "domain" : "/api/v1/domain/111/",
               "localpart" : "test",
               "create_opt" : "generate_pwd"
            }' \
        https://admin.mailroute.net/api/v1/email_account/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:32 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/email_account/66/


​    
    {
       "priority" : 8,
       "localpart" : "test",
       "change_pwd" : null,
       "create_opt" : null,
       "contact" : null,
       "resource_uri" : "/api/v1/email_account/66/",
       "domain_name" : "renamedtestdomain.com",
       "notification_task" : "/api/v1/notification_account_task/177/",
       "created_at" : "Mon, 18 Feb 2013 10:10:30 -0800",
       "domain" : "/api/v1/domain/111/",
       "updated_at" : "Mon, 18 Feb 2013 10:10:31 -0800",
       "policy" : "/api/v1/policy_user/178/",
       "absolute_url" : "/user/66/",
       "aliases" : "",
       "id" : 66
    }


### Updating an Email Account

#### Definition


​    
    PUT https://admin.mailroute.net/api/v1/email_account/66/


#### Arguments

parameterrequireddefaultdescription

localpart | _required_ |  | String - the localpart of the email address  
---|---|---|---  
domain | _required_ |  | String - domain_uri  
create_opt | _required_ |  | String - 'generate_pwd'  
password |  |  | String  
send_welcome |  | false | Boolean - Send welcome email on creation of account  

#### Example Request


​    
    curl -s --dump-header - -X PUT \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "localpart" : "test2"
            }' \
        https://admin.mailroute.net/api/v1/email_account/66/


#### Example Response


​    
    HTTP/1.0 202 ACCEPTED
    Date: Mon, 18 Feb 2013 18:10:33 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8


​    
    {
       "priority" : 8,
       "localpart" : "test2",
       "pk" : "66",
       "change_pwd" : null,
       "create_opt" : null,
       "contact" : null,
       "resource_uri" : "/api/v1/email_account/66/",
       "domain_name" : "renamedtestdomain.com",
       "notification_task" : "/api/v1/notification_account_task/177/",
       "created_at" : "Mon, 18 Feb 2013 10:10:30 -0800",
       "domain" : "/api/v1/domain/111/",
       "updated_at" : "Mon, 18 Feb 2013 10:10:33 -0800",
       "policy" : "/api/v1/policy_user/178/",
       "absolute_url" : "/user/66/",
       "aliases" : "",
       "id" : 66
    }


### Updating an Email Account Password

#### Example Request


​    
    curl -s --dump-header - -X PATCH \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey u1@usercase.com:05d7a263270f4025de3143870099a00f12b5d49d' \
        --data '{
       "confirm_password": "qazxswedc",
       "password": "qazxswedc",
       "change_pwd": "1"
    }' 'https://admin.mailroute.net/api/v1/email_account/user3@apitest.com/'


### Listing Email Accounts

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/email_account/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/email_account/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:34 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "objects" : [
          {
             "priority" : 8,
             "localpart" : "test2",
             "change_pwd" : null,
             "create_opt" : null,
             "contact" : null,
             "resource_uri" : "/api/v1/email_account/66/",
             "domain_name" : "renamedtestdomain.com",
             "notification_task" : "/api/v1/notification_account_task/177/",
             "created_at" : "Mon, 18 Feb 2013 10:10:30 -0800",
             "domain" : "/api/v1/domain/111/",
             "updated_at" : "Mon, 18 Feb 2013 10:10:33 -0800",
             "policy" : "/api/v1/policy_user/178/",
             "absolute_url" : "/user/66/",
             "aliases" : "",
             "id" : 66
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


Deleting an Email Account

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/email_account/66/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/email_account/66/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:43 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


### The Email Account Alias Object

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/localpart_alias/schema/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/localpart_alias/schema/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:34 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "ordering" : [
          "localpart",
          "created_at",
          "updated_at"
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
          "localpart" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
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
             "readonly" : true,
             "nullable" : true,
             "blank" : true,
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
          "email_account" : {
             "unique" : false,
             "help_text" : "A single related resource. Can be either a URI or set of nested resource data.",
             "related_type" : "to_one",
             "default" : "No default provided.",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "related"
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
          "type" : {
             "unique" : false,
             "help_text" : "Unicode string data. Ex: \"Hello World\"",
             "readonly" : false,
             "nullable" : false,
             "blank" : false,
             "type" : "string",
             "default" : "alias"
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
          "email_account" : [
             "exact"
          ]
       },
       "default_format" : "application/json",
       "default_limit" : 20
    }


### Creating an Email Account Alias

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/localpart_alias/


#### Arguments

parameterrequireddefaultdescription

localpart | _required_ |  | String - the localpart of the email address  
---|---|---|---  
email_account | _required_ |  | String - email _account_ uri  

#### Example Request


​    
    curl -s --dump-header - -X POST \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "localpart" : "testalias",
               "email_account" : "/api/v1/email_account/66/"
            }' \
        https://admin.mailroute.net/api/v1/localpart_alias/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:35 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/localpart_alias/118/


​    
    {
       "resource_uri" : "/api/v1/localpart_alias/118/",
       "localpart" : "testalias",
       "domain" : "/api/v1/domain/111/",
       "created_at" : "Mon, 18 Feb 2013 10:10:34 -0800",
       "email_account" : "/api/v1/email_account/66/",
       "updated_at" : "Mon, 18 Feb 2013 10:10:35 -0800",
       "type" : "alias",
       "id" : 118
    }


### Updating an Email Account Alias

#### Definition


​    
    PUT https://admin.mailroute.net/api/v1/localpart_alias/118/


#### Arguments

parameterrequireddefaultdescription

localpart | _required_ |  | String - the localpart of the email address  
---|---|---|---  
email_account | _required_ |  | String - email _account_ uri  

#### Example Request


​    
    curl -s --dump-header - -X PUT \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        --data '   {
               "localpart" : "renamedtestalias"
            }' \
        https://admin.mailroute.net/api/v1/localpart_alias/118/


#### Example Response


​    
    HTTP/1.0 202 ACCEPTED
    Date: Mon, 18 Feb 2013 18:10:36 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8


​    
    {
       "localpart" : "renamedtestalias",
       "pk" : "118",
       "resource_uri" : "/api/v1/localpart_alias/118/",
       "created_at" : "Mon, 18 Feb 2013 10:10:34 -0800",
       "domain" : "/api/v1/domain/111/",
       "email_account" : "/api/v1/email_account/66/",
       "updated_at" : "Mon, 18 Feb 2013 10:10:36 -0800",
       "id" : 118,
       "type" : "alias"
    }


### Listing Email Account Aliases

#### Definition


​    
    GET https://admin.mailroute.net/api/v1/localpart_alias/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/localpart_alias/


#### Example Response


​    
    HTTP/1.0 200 OK
    Date: Mon, 18 Feb 2013 18:10:37 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Cache-Control: no-cache


​    
    {
       "objects" : [
          {
             "resource_uri" : "/api/v1/localpart_alias/118/",
             "localpart" : "renamedtestalias",
             "domain" : "/api/v1/domain/111/",
             "created_at" : "Mon, 18 Feb 2013 10:10:34 -0800",
             "email_account" : "/api/v1/email_account/66/",
             "updated_at" : "Mon, 18 Feb 2013 10:10:36 -0800",
             "type" : "alias",
             "id" : 118
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


Deleting an Email Account Alias

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/localpart_alias/118/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/localpart_alias/118/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:41 GMT
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
    Date: Mon, 18 Feb 2013 18:10:37 GMT
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
    PUT https://admin.mailroute.net/api/v1/policy_user/178/


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
        https://admin.mailroute.net/api/v1/policy_user/178/


#### Example Response


​    
    HTTP/1.0 202 ACCEPTED
    Date: Mon, 18 Feb 2013 18:10:38 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8


​    
    {
       "priority" : 4,
       "spam_subject_tag3" : null,
       "spam_subject_tag" : null,
       "id" : 178,
       "unchecked_lover" : "Y",
       "addr_extension_virus" : null,
       "bad_header_quarantine_to" : "sql:",
       "warnbadhrecip" : "N",
       "warnbannedrecip" : "N",
       "unchecked_quarantine_to" : null,
       "bypass_spam_checks" : "N",
       "spam_quarantine_to" : "sql:",
       "message_size_limit" : 0,
       "bypass_virus_checks" : "N",
       "email_account" : "/api/v1/email_account/66/",
       "virus_quarantine_to" : "sql:",
       "spam_kill_level" : 9,
       "warnvirusrecip" : "N",
       "addr_extension_bad_header" : null,
       "banned_quarantine_to" : "sql:",
       "spam_quarantine_cutoff_level" : null,
       "spam_tag2_level" : 5.5,
       "bypass_header_checks" : "Y",
       "spam_subject_tag2" : "Updated spam_subject_tag2",
       "pk" : "178",
       "bad_header_lover" : "N",
       "addr_extension_spam" : null,
       "spam_lover" : "N",
       "banned_files_lover" : "N",
       "virus_lover" : "N",
       "bypass_banned_checks" : "N",
       "spam_tag3_level" : null,
       "resource_uri" : "/api/v1/policy_user/178/",
       "spam_tag_level" : -9999,
       "addr_extension_banned" : null
    }


### The Email_account Allow and Block lists Object

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
    Date: Mon, 18 Feb 2013 18:10:39 GMT
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


### Creating an Email_account Allow and Block lists

#### Definition


​    
    POST https://admin.mailroute.net/api/v1/wblist/


#### Arguments

parameterrequireddefaultdescription

email_account | _required_ |  | String - email _account_ uri  
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
               "wb" : "w",
               "email_account" : "/api/v1/email_account/66/"
            }' \
        https://admin.mailroute.net/api/v1/wblist/


#### Example Response


​    
    HTTP/1.0 201 CREATED
    Date: Mon, 18 Feb 2013 18:10:40 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Type: application/json; charset=utf-8
    Location: http://127.0.0.1:8000/api/v1/wblist/78/


​    
    {
       "resource_uri" : "/api/v1/wblist/78/",
       "email" : "whitelist.com",
       "domain" : null,
       "wb" : "w",
       "email_account" : null,
       "rid" : "1110000066",
       "id" : 78
    }


Deleting an Email_account Allow and Block lists

#### Definition


​    
    DELETE https://admin.mailroute.net/api/v1/wblist/78/


#### Arguments

**none**

#### Example Request


​    
    curl -s --dump-header - -X DELETE \
        -H 'Content-Type: application/json' \
        -H 'Authorization: ApiKey <login>:<apikey>' \
        https://admin.mailroute.net/api/v1/wblist/78/


#### Example Response


​    
    HTTP/1.0 204 NO CONTENT
    Date: Mon, 18 Feb 2013 18:10:40 GMT
    Server: WSGIServer/0.1 Python/2.7.2
    Vary: Accept, Cookie
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


### The Account Notification Task Object

### Turn on/off domain notifications for email account

Endpoing: `/api/v1/email_account/<email_account>/`

Method: `PATCH`

Data:


​    
    {
        "use_domain_notifications": true
    }


`use_domain_notifications` is a boolean value that determines whether email
account should use domain notification schedule or their own.

`<email_account>` is the email account's email address.

Example:


​    
    curl -X PATCH -H 'Authorization: ApiKey {user}:{key}' -H 'Content-Type: application/json' -d '{
        "use_domain_notifications": true
    }' 'https://admin.mailroute.net/api/v1/email_account/<email_account>/'


### List all email account notifications

Endpoint: `/api/v1/notification_account_task/?email_account=<email_account>`

Method: `GET`

`<email_account>` is the email account's email address.

Example:


​    
    curl -X GET -H 'Authorization: ApiKey {user}:{key}' -H 'Content-Type: application/json' 'https://admin.mailroute.net/api/v1/notification_account_task/?email_account=<email_account>'


Example output:


​    
    {
      "meta": {
        "limit": 10,
        "next": null,
        "offset": 0,
        "previous": null,
        "total_count": 1
      },
      "objects": [
        {
          "email_account": "/api/v1/email_account/290572/",
          "enabled": true,
          "fri": true,
          "hour": 9,
          "id": 341,
          "minute": 0,
          "mon": true,
          "resource_uri": "/api/v1/notification_account_task/341/",
          "sat": false,
          "sun": false,
          "thu": true,
          "tue": true,
          "wed": true
        }
      ]
    }


### Create new email account notification

Endpoint: `/api/v1/notification_account_task/`

Method: `POST`

Data:


​    
    {
        "email_account": "/api/v1/email_account/<email_account>/",
        "sun": false,
        "mon": true,
        "tue": true,
        "wed": true,
        "thu": true,
        "fri": true,
        "sat": false,
        "enabled": true,
        "hour": 9,
        "minute": 0
    }


`<email_account>` is the email account's email address.

`sun`, `mon`, `tue`, `wed`, `thu`, `fri`, `sat` are boolean values that
determine whether the notification is sent on that day.

`enabled` is a boolean value that determines whether the notification is
enabled.

`hour` is the hour of the day the notification is sent.

`minute` is the minute of the hour the notification is sent.

Example:


​    
    curl -X POST -H 'Authorization: ApiKey {user}:{key}' -H 'Content-Type: application/json' -d '{"email_account":"/api/v1/email_account/<email_account>/","sun":false,"mon":true,"tue":true,"wed":true,"thu":true,"fri":true,"sat":false,"enabled":true,"hour":9,"minute":0}' 'https://admin.mailroute.net/api/v1/notification_account_task/'


### Update email account notification

Endpoint: `/api/v1/notification_account_task/<id>/`

Method: `PUT`

Parameters:

  * `<id>` is the id of the notification account task. See List all email account notifications for how to get the id.

Data:


​    
    {
        "email_account":"/api/v1/email_account/<email_account>/",
        "enabled":true,
        "fri":true,
        "hour":14,
        "id":<id>,
        "minute":0,
        "mon":true,
        "resource_uri":"/api/v1/notification_account_task/<id>/",
        "sat":false,
        "sun":false,
        "thu":true,
        "tue":true,
        "wed":true
    }


`<id>` is the id of the notification account task.

`<email_account>` is the email account's email address.

Example:


​    
    curl -X PUT -H 'Authorization: ApiKey {user}:{key}' -H 'Content-Type: application/json' -H 'Content-Type: application/json' -d '{
        "email_account":"/api/v1/email_account/290572/",
        "enabled":true,
        "fri":true,
        "hour":14,
        "id":341,
        "minute":0,
        "mon":true,
        "resource_uri":"/api/v1/notification_account_task/341/",
        "sat":false,
        "sun":false,
        "thu":true,
        "tue":true,
        "wed":true
    }' 'https://admin.mailroute.net/api/v1/notification_account_task/341/'


### Delete email account notification

Endpoint: `/api/v1/notification_account_task/<id>/`

Method: `DELETE`

`<id>` is the id of the notification account task.

Example:


​    
    curl -X DELETE -H 'Authorization: ApiKey {user}:{key}' -H 'Content-Type: application/json' 'https://admin.mailroute.net/api/v1/notification_account_task/341/'

