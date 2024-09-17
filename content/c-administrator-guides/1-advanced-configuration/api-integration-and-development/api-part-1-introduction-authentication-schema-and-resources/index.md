---
created_at: 2013-02-06 18:29:29
date: 2024-06-02 06:44:24
description: A comprehensive guide on using the MailRoute API, covering authentication,
  schema exploration, filtering resources, creating/updating/deleting resources, and
  handling errors, with examples using cURL.
draft: true
params:
  author: Unknown
summary: The article provides an introduction to the MailRoute API, detailing how
  to authenticate, explore the API schema, and perform CRUD operations (create, retrieve,
  update, and delete) on various resources such as email accounts, domains, and policies.
tags:
- API
title: API (Part 1) - Introduction, Authentication, Schema, and Resources
---


# The MailRoute API

# Part 1 - Introduction, Authentication, Schema and Resources

## API Introduction

The MailRoute API is built using the Tastypie Webservice API for Django. Parts
of this documentation are based upon the standard Tastypie documentation, but
adapted to show MailRoute-specific examples. You can view the full Tastypie
documentation at <http://django-tastypie.readthedocs.org/en/latest/>

The API is a REST-style API providing access to all aspects of the MailRoute
Service configuration. Everything you see in our own interface at
<https://admin.mailroute.net> is done through this API and all of that
functionality is available to you.

Our examples below will all use curl to show the details of the API calls and
their returned values, but you can call our API from whatever language you
prefer - anything that can issue HTTP requests can talk to our system.

If you wish to experiment or use the MailRoute API in your applications,
scripts or tools, please email
[support@mailroute.net](mailto:support@mailroute.net) to request your API key.

## API Endpoint

All calls to the API are done to this parent URL:


​    
    https://admin.mailroute.net/


## Authentication

You authenticate to the MailRoute API by providing one of your API keys in the
HTTP request. You can find your API key on your account page. Your API key has
all the privileges of your login account, so be sure to keep it secret!

Please email [support@mailroute.net](mailto:support@mailroute.net) to receive
your API key.

Authentication to the API occurs via HTTP Authorization header. Provide a
header in the format:


​    
    Authorization: ApiKey <login>:<apikey>


All API calls must be made over HTTPS. Calls over plain HTTP will fail. You
must authenticate every request.


​    
    curl -s -H "Accept: application/json" \
    -H "Content-Type: application/json" \
    -H "Authorization: ApiKey <login>:<api key>" \
    https://admin.mailroute.net/api/v1/


## Errors

HTTP Response codes are used to indicate the success or failure of an API
request.

Codes in the 2xx range indicate success, those in the 4xx range indicate that
there's an error in the provided information (ie, missing parameter, duplicate
entry, etc). Errors in the 5xx range indicate an error in the MailRoute
servers.

All errors return JSON with .......

## Exploring the API

Perhaps the easiest way to explore the API is to use the curl command line
utility on unix or windows. It allows you to easily see the data returned from
every call.

This is how we make our exploratory calls:


​    
    curl -s -H "Accept: application/json" \
    -H "Content-Type: application/json" \
    -H "Authorization: ApiKey <login>:<api key>" \
    https://admin.mailroute.net/api/v1/


The "-s" option tells curl not to display the progress bars. The Accept and
Content-Type headers tell about which format we're using for our data. We
prefer JSON, but the API also supports XML, and you can specify "-H Accept:
application/xml -H Content-Type: application/xml" if you prefer.

In order to view the json content in a prettier form, we often pipe the result
of curl through "python -mjson.tool" like this:


​    
    curl -s -H "Accept: application/json" \
    -H "Content-Type: application/json" \
    -H "Authorization: ApiKey <login>:<api key>" \
    https://admin.mailroute.net/api/v1/ \
    | python -mjson.tool


It's much easier to read. All of our examples in this document will use this
style.

### Schema

You can get a list of all the different Resource classes by retrieving the
schema for the top-level resources:


​    
    curl -s -H "Accept: application/json" \
            -H "Content-Type: application/json" \
            -H "Authorization: ApiKey <login>:<api key>" \
            https://admin.mailroute.net/api/v1/ \
            | python -mjson.tool


You will get back something like:


​    
    {
        "admins": {
            "list_endpoint": "/api/v1/admins/", 
            "schema": "/api/v1/admins/schema/"
        }, 
        "contact_customer": {
            "list_endpoint": "/api/v1/contact_customer/", 
            "schema": "/api/v1/contact_customer/schema/"
        }, 
        "contact_domain": {
            "list_endpoint": "/api/v1/contact_domain/", 
            "schema": "/api/v1/contact_domain/schema/"
        }, 
        "contact_email_account": {
            "list_endpoint": "/api/v1/contact_email_account/", 
            "schema": "/api/v1/contact_email_account/schema/"
        }, 
        "contact_reseller": {
            "list_endpoint": "/api/v1/contact_reseller/", 
            "schema": "/api/v1/contact_reseller/schema/"
        }, 
        "customer": {
            "list_endpoint": "/api/v1/customer/", 
            "schema": "/api/v1/customer/schema/"
        }, 
        "domain": {
            "list_endpoint": "/api/v1/domain/", 
            "schema": "/api/v1/domain/schema/"
        }, 
        "domain_alias": {
            "list_endpoint": "/api/v1/domain_alias/", 
            "schema": "/api/v1/domain_alias/schema/"
        }, 
        "domain_with_alias": {
            "list_endpoint": "/api/v1/domain_with_alias/", 
            "schema": "/api/v1/domain_with_alias/schema/"
        }, 
        "email_account": {
            "list_endpoint": "/api/v1/email_account/", 
            "schema": "/api/v1/email_account/schema/"
        }, 
        "localpart_alias": {
            "list_endpoint": "/api/v1/localpart_alias/", 
            "schema": "/api/v1/localpart_alias/schema/"
        }, 
        "mail_server": {
            "list_endpoint": "/api/v1/mail_server/", 
            "schema": "/api/v1/mail_server/schema/"
        }, 
        "notification_account_task": {
            "list_endpoint": "/api/v1/notification_account_task/", 
            "schema": "/api/v1/notification_account_task/schema/"
        }, 
        "notification_domain_task": {
            "list_endpoint": "/api/v1/notification_domain_task/", 
            "schema": "/api/v1/notification_domain_task/schema/"
        }, 
        "outbound_server": {
            "list_endpoint": "/api/v1/outbound_server/", 
            "schema": "/api/v1/outbound_server/schema/"
        }, 
        "policy_domain": {
            "list_endpoint": "/api/v1/policy_domain/", 
            "schema": "/api/v1/policy_domain/schema/"
        }, 
        "policy_user": {
            "list_endpoint": "/api/v1/policy_user/", 
            "schema": "/api/v1/policy_user/schema/"
        }, 
        "reseller": {
            "list_endpoint": "/api/v1/reseller/", 
            "schema": "/api/v1/reseller/schema/"
        }, 
        "wblist": {
            "list_endpoint": "/api/v1/wblist/", 
            "schema": "/api/v1/wblist/schema/"
        }
    }


Each top-level resource is listed along with the list_endpoint and the schema
for the resource.

### Inspecting the schema of a particular resource

Since the api-wide call gave us a schema URL, we can inspect that. Let's use
the email_account resource. Again, simple GET request by curl:


​    
    curl -s -H "Accept: application/json" 
    -H "Content-Type: application/json" 
    -H "Authorization: ApiKey <login>:<api key>" 
    https://admin.mailroute.net/api/v1/email_account/schema/ \
    | python -mjson.tool


And we get back a lot more data:


​    
    {
    "allowed_detail_http_methods": [
        "get", 
        "post", 
        "put", 
        "delete"
    ], 
    "allowed_list_http_methods": [
        "get", 
        "post", 
        "put", 
        "delete"
    ], 
    "default_format": "application/json", 
    "default_limit": 20, 
    "fields": {
        "change_pwd": {
            "blank": true, 
            "default": "No default provided.", 
            "help_text": "Unicode string data. Ex: \"Hello World\"", 
            "nullable": true, 
            "readonly": false, 
            "type": "string", 
            "unique": false
        }, 
        "contact": {
            "blank": false, 
            "default": "No default provided.", 
            "help_text": "A single related resource. Can be either a URI or set of nested resource data.", 
            "nullable": true, 
            "readonly": true, 
            "related_type": "to_one", 
            "type": "related", 
            "unique": false
        }, 
        "create_opt": {
            "blank": true, 
            "default": "No default provided.", 
            "help_text": "Unicode string data. Ex: \"Hello World\"", 
            "nullable": true, 
            "readonly": false, 
            "type": "string", 
            "unique": false
        }, 
        "created_at": {
            "blank": false, 
            "default": "No default provided.", 
            "help_text": "A date & time as a string. Ex: \"2010-11-10T03:07:43\"", 
            "nullable": false, 
            "readonly": true, 
            "type": "datetime", 
            "unique": false
        }, 
        "domain": {
            "blank": false, 
            "default": "No default provided.", 
            "help_text": "A single related resource. Can be either a URI or set of nested resource data.", 
            "nullable": false, 
            "readonly": false, 
            "related_type": "to_one", 
            "type": "related", 
            "unique": false
        }, 
        "id": {
            "blank": true, 
            "default": "", 
            "help_text": "Integer data. Ex: 2673", 
            "nullable": false, 
            "readonly": false, 
            "type": "integer", 
            "unique": true
        }, 
        "localpart": {
            "blank": false, 
            "default": "No default provided.", 
            "help_text": "Unicode string data. Ex: \"Hello World\"", 
            "nullable": false, 
            "readonly": false, 
            "type": "string", 
            "unique": false
        }, 
        "notification_task": {
            "blank": false, 
            "default": "No default provided.", 
            "help_text": "A single related resource. Can be either a URI or set of nested resource data.", 
            "nullable": true, 
            "readonly": true, 
            "related_type": "to_one", 
            "type": "related", 
            "unique": false
        }, 
        "policy": {
            "blank": false, 
            "default": "No default provided.", 
            "help_text": "A single related resource. Can be either a URI or set of nested resource data.", 
            "nullable": true, 
            "readonly": true, 
            "related_type": "to_one", 
            "type": "related", 
            "unique": false
        }, 
        "priority": {
            "blank": false, 
            "default": 7, 
            "help_text": "Integer data. Ex: 2673", 
            "nullable": false, 
            "readonly": false, 
            "type": "integer", 
            "unique": false
        }, 
        "resource_uri": {
            "blank": false, 
            "default": "No default provided.", 
            "help_text": "Unicode string data. Ex: \"Hello World\"", 
            "nullable": false, 
            "readonly": true, 
            "type": "string", 
            "unique": false
        }, 
        "updated_at": {
            "blank": false, 
            "default": "No default provided.", 
            "help_text": "A date & time as a string. Ex: \"2010-11-10T03:07:43\"", 
            "nullable": false, 
            "readonly": true, 
            "type": "datetime", 
            "unique": false
        }
    }, 
    "filtering": {
        "domain": 2, 
        "id": [
            "in"
        ], 
        "localpart": 1
    }, 
    "ordering": [
        "localpart", 
        "priority", 
        "domain", 
        "created_at"
    ]
    }


This lists out the default_format this resource responds with, the fields on
the resource & the filtering options available. This information can be used
to prepare the other aspects of the code for the data it can obtain & ways to
filter the resources.

### Getting a collection of resources (Resellers, Customers, Email Account,
etc...)

You can request a list of resources by hitting the list_endpoint for the top-
level schema of interest.

Let's try getting a list of domains for this account:


​    
    curl -s -H "Accept: application/json"  \
    -H "Content-Type: application/json" \
    -H "Authorization: ApiKey <login>:<api key>" \
    https://admin.mailroute.net/api/v1/domain/ \
    | python -mjson.tool
    {
    "meta": {
        "limit": 20, 
        "next": "/api/v1/domain/?limit=20&offset=20", 
        "offset": 0, 
        "previous": null, 
        "total_count": 3
    }, 
    "objects": [
        {
            "absolute_url": "/domain/912345/", 
            "active": true, 
            "bounce_unlisted": false, 
            "created_at": "Thu, 7 Jun 2012 15:24:27 -0700", 
            "customer": "/api/v1/customer/912345/", 
            "deliveryport": 25, 
            "hold_email": false, 
            "id": 1, 
            "name": "testdomain.com", 
            "outbound_enabled": false, 
            "policy": "/api/v1/policy_domain/912345/", 
            "resource_uri": "/api/v1/domain/912345/", 
            "updated_at": "Sun, 9 Sep 2012 14:58:52 -0700"
        }, 
        {
            "absolute_url": "/domain/912346/", 
            "active": true, 
            "bounce_unlisted": true, 
            "created_at": "Fri, 26 Oct 2012 11:19:48 -0700", 
            "customer": "/api/v1/customer/912346/", 
            "deliveryport": 25, 
            "hold_email": false, 
            "id": 912346, 
            "name": "testdomain2.com", 
            "outbound_enabled": true, 
            "policy": "/api/v1/policy_domain/912346/", 
            "resource_uri": "/api/v1/domain/912346/", 
            "updated_at": "Mon, 12 Nov 2012 12:04:27 -0800"
        }, 
        {
            "absolute_url": "/domain/912347/", 
            "active": true, 
            "bounce_unlisted": true, 
            "created_at": "Thu, 13 Sep 2012 10:35:35 -0700", 
            "customer": "/api/v1/customer/912345/", 
            "deliveryport": 25, 
            "hold_email": false, 
            "id": 3271, 
            "name": "testdomain3.com", 
            "outbound_enabled": true, 
            "policy": "/api/v1/policy_domain/912347/", 
            "resource_uri": "/api/v1/domain/912347/", 
            "updated_at": "Mon, 29 Oct 2012 09:56:38 -0700"
        }, 
    ]
    }


Some things to note:

  * By default, you get a paginated set of objects (20 per page is the default).
  * In the meta, you get a previous & next. If available, these are URIs to the previous & next pages.
  * You get a list of resources/objects under the objects key.
  * Each resources/object has a resource_uri field that points to the detail view for that object.

####Filtering a resource

We can see that the schema allows us to filter by name, so let's get a domain
by name:


​    
    curl -s -H "Accept: application/json" \
    -H "Content-Type: application/json" \
    -H "Authorization: ApiKey <login>:<api key>" \
    https://admin.mailroute.net/api/v1/domain/?name=testdomain.com \
    | python -mjson.tool
    {
    "meta": {
        "limit": 20, 
        "next": null, 
        "offset": 0, 
        "previous": null, 
        "total_count": 1
    }, 
    "objects": [
        {
            "absolute_url": "/domain/912345/", 
            "active": true, 
            "bounce_unlisted": true, 
            "created_at": "Thu, 7 Jun 2012 17:01:47 -0700", 
            "customer": "/api/v1/customer/912345/", 
            "deliveryport": 25, 
            "hold_email": false, 
            "id": 912345, 
            "name": "testdomain.com", 
            "outbound_enabled": true, 
            "policy": "/api/v1/policy_domain/912345/", 
            "resource_uri": "/api/v1/domain/912345/", 
            "updated_at": "Fri, 9 Nov 2012 20:57:05 -0800"
        }
    ]
    }


###Getting A Detail Resource

Since each resource/object in the list view had a resource_uri, let’s explore
what’s there:


​    
    curl -s -H "Accept: application/json" \
    -H "Content-Type: application/json" \
    -H "Authorization: ApiKey <login>:<api key>" \
    https://admin.mailroute.net/api/v1/domain/912345/ \
    | python -mjson.tool
    {
        "absolute_url": "/domain/912345/", 
        "active": true, 
        "bounce_unlisted": true, 
        "created_at": "Thu, 7 Jun 2012 17:01:47 -0700", 
        "customer": "/api/v1/customer/912345/", 
        "deliveryport": 25, 
        "hold_email": false, 
        "id": 912345, 
        "name": "testdomain.com", 
        "outbound_enabled": true, 
        "policy": "/api/v1/policy_domain/912345/", 
        "resource_uri": "/api/v1/domain/912345/", 
        "updated_at": "Fri, 9 Nov 2012 20:57:05 -0800"
    }


We can see the policy resource here, and get the policy for this user this way
- without even having ever looked up the resource definition for the policy:

    
  
    curl -s -H "Accept: application/json" \
    -H "Content-Type: application/json" \
    -H "Authorization: ApiKey <login>:<api key>" \
    https://admin.mailroute.net/api/v1/policy_domain/912345/ \
    | python -mjson.tool
    {
        "addr_extension_bad_header": null, 
        "addr_extension_banned": null, 
        "addr_extension_spam": null, 
        "addr_extension_virus": null, 
        "bad_header_lover": "N", 
        "bad_header_quarantine_to": "sql:", 
        "banned_files_lover": "N", 
        "banned_quarantine_to": "sql:", 
        "bypass_banned_checks": "N", 
        "bypass_header_checks": "Y", 
        "bypass_spam_checks": "N", 
        "bypass_virus_checks": "N", 
        "domain": "/api/v1/domain/912345/", 
        "id": 912345, 
        "is_default": false, 
        "message_size_limit": 0, 
        "priority": 5, 
        "resource_uri": "/api/v1/policy_domain/912345/", 
        "spam_kill_level": 7.0, 
        "spam_lover": "N", 
        "spam_modifies_subj": "N", 
        "spam_quarantine_cutoff_level": null, 
        "spam_quarantine_to": "sql:", 
        "spam_subject_tag": null, 
        "spam_subject_tag2": null, 
        "spam_subject_tag3": null, 
        "spam_tag2_level": null, 
        "spam_tag3_level": null, 
        "spam_tag_level": -9999.0, 
        "unchecked_lover": "Y", 
        "unchecked_quarantine_to": null, 
        "virus_lover": "N", 
        "virus_quarantine_to": "sql:", 
        "warnbadhrecip": "N", 
        "warnbannedrecip": "N", 
        "warnvirusrecip": "N"
    }
    

## Sending data

There are no new URLs to learn. The “list” & “detail” URLs we’ve been using to
fetch data ALSO support the POST/PUT/DELETE HTTP methods.

###Creating a new resource (POST)

To create new resources/objects, you will POST to the list endpoint of a
resource. Trying to POST to a detail endpoint has a different meaning in the
REST mindset (meaning to add a resource as a child of a resource of the same
type).

As with all Tastypie requests, the headers we request are important. Since
we’ve been using primarily JSON throughout, let’s send a new entry in JSON
format:


​    
    curl --dump-header - -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: ApiKey <login>:<api key>" \
    --data '{"priority":8,"localpart":"testing","domain":"/domain/1899/","create_opt":"generate_pwd"}' \
    https://admin.mailroute.net/api/v1/email_account/


The Content-Type header indicates that we’re sending our data using JSON. We
send the data as a JSON-serialized body (NOT as form-data in the form of URL
parameters). What we get back is the following response:


​    
    HTTP/1.1 201 CREATED
    Server: nginx/1.2.1
    Date: Sun, 02 Dec 2012 18:07:39 GMT
    Content-Type: text/html; charset=utf-8
    Transfer-Encoding: chunked
    Connection: keep-alive
    Vary: Accept, Cookie
    Location: https://admin.mailroute.net/api/v1/email_account/24263/


You’ll also note that we get a correct HTTP status code back (201) & a
Location header, which gives us the URI to our newly created resource.

Passing --dump-header - is important, because it gives you all the headers as
well as the status code. When things go wrong, this will be useful information
to help with debugging. For instance, if we send a request without a
localpart:


​    
    curl --dump-header - -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: ApiKey <login>:<api key>" \
    --data '{"priority":8,"domain":"/domain/912345/","create_opt":"generate_pwd"}' \
     https://admin.mailroute.net/api/v1/email_account/


We get back:


​    
    HTTP/1.1 400 BAD REQUEST
    Server: nginx/1.2.1
    Date: Sun, 02 Dec 2012 18:09:24 GMT
    Content-Type: application/json; charset=utf-8
    Transfer-Encoding: chunked
    Connection: keep-alive
    Vary: Cookie
    {"email_account": {"localpart": ["This field is required."]}}


###Updating An Existing Resource (PUT)

You can update an resource by sending a PUT request.

FIXME


​    
    curl --dump-header - -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: ApiKey <login>:<api key>" \
    --data '{"priority":8,"localpart":"testing234","domain":"/domain/912345/","create_opt":"generate_pwd"}' \
    https://admin.mailroute.net/api/v1/email_account/24263/


And we should get this back:


​    
    HTTP/1.0 204 NO CONTENT
    Date: Fri, 20 May 2011 07:13:21 GMT
    Server: WSGIServer/0.1 Python/2.7
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


We get a 204 status code, meaning our update was successful. We don’t get a
Location header back because we did the PUT on a detail URL, which presumably
did not change.

**Note: A PUT request requires that the entire resource representation be
enclosed. Missing fields may cause errors, or be filled in by default
values.**

###Partially Updating An Existing Resource (PATCH) - COMING SOON

In some cases, you may not want to send the entire resource when updating. To
update just a subset of the fields, we can send a PATCH request to the detail
endpoint.:


​    
    curl --dump-header - -X PATCH \
    -H "Content-Type: application/json" \
    --data '{"name": "This is a new reseller name"}' 
    http://localhost:8000/api/v1/reseller/1/


To which we should get back:


​    
    HTTP/1.0 202 ACCEPTED
    Date: Fri, 20 May 2011 07:13:21 GMT
    Server: WSGIServer/0.1 Python/2.7
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


## Deleting Data

No CRUD setup would be complete without the ability to delete
resources/objects. Deleting also requires significantly less complicated
requests than POST/PUT.

###Deleting A Single Resource

We’ve decided that we don’t like the entry we added & edited earlier. Let’s
delete it (but leave the other objects alone):


​    
    curl --dump-header - -H "Content-Type: application/json" -X DELETE \
    -H "Authorization: ApiKey <login>:<api key>" \
    https://admin.mailroute.net/api/v1/email_account/24263/


Once again, we get back the “Accepted” response of a 204:


​    
    HTTP/1.0 204 NO CONTENT
    Date: Fri, 20 May 2011 07:28:01 GMT
    Server: WSGIServer/0.1 Python/2.7
    Content-Length: 0
    Content-Type: text/html; charset=utf-8


If we request that resource, we get a 404 to show it’s no longer there:


​    
    curl --dump-header - -H "Accept: application/json" \
    -H "Content-Type: application/json" \
    -H "Authorization: ApiKey <login>:<api key>" \
    https://admin.mailroute.net/api/v1/email_account/24263/
    HTTP/1.1 404 NOT FOUND
    Server: nginx/1.2.1
    Date: Sun, 02 Dec 2012 23:16:36 GMT
    Content-Type: text/html; charset=utf-8
    Transfer-Encoding: chunked
    Connection: keep-alive
    Vary: Accept-Encoding
    Vary: Accept, Cookie


[Start a free 30-day trial today.](http://mailroute.net/signup.html)

Contact [sales@mailroute.net](mailto:sales@mailroute.net) or
[support@mailroute.net](mailto:support@mailroute.net) for more information.

888.485.7726

