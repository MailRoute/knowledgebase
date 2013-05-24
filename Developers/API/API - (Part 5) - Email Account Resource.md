## Email Accounts

### The Email Account Object

#### Definition

	GET https://admin.mailroute.net/api/vi/email_account/schema/


#### Arguments

**none**  

#### Example Request

	curl -s --dump-header - \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		https://admin.mailroute.net/api/vi/email_account/schema/


#### Example Response

	HTTP/1.0 200 OK
	Date: Mon, 18 Feb 2013 18:10:30 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	Cache-Control: no-cache
	
	
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

	POST https://admin.mailroute.net/api/vi/email_account/


#### Arguments

parameter | required | default | description
-----|-----|-----|-----|
localpart|*required*| |String - the localpart of the email address|
domain|*required*| |String - domain_uri|
create_opt|*required*| |String - 'generate_pwd'|'create_pwd'|
password| | |String|
send_welcome| |false|Boolean - Send welcome email on creation of account|


#### Example Request

	curl -s --dump-header - -X POST \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		--data '   { \ 
	           "domain" : "/api/v1/domain/111/", \ 
	           "localpart" : "test", \ 
	           "create_opt" : "generate_pwd" \ 
	        }' \
		https://admin.mailroute.net/api/vi/email_account/


#### Example Response

	HTTP/1.0 201 CREATED
	Date: Mon, 18 Feb 2013 18:10:32 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	Location: http://127.0.0.1:8000/api/v1/email_account/66/
	
	
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

	PUT https://admin.mailroute.net/api/vi/email_account/66/


#### Arguments

parameter | required | default | description
-----|-----|-----|-----|
localpart|*required*| |String - the localpart of the email address|
domain|*required*| |String - domain_uri|
create_opt|*required*| |String - 'generate_pwd'|'create_pwd'|
password| | |String|
send_welcome| |false|Boolean - Send welcome email on creation of account|


#### Example Request

	curl -s --dump-header - -X PUT \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		--data '   { \ 
	           "localpart" : "test2" \ 
	        }' \
		https://admin.mailroute.net/api/vi/email_account/66/


#### Example Response

	HTTP/1.0 202 ACCEPTED
	Date: Mon, 18 Feb 2013 18:10:33 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	
	
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


### Listing Email Accounts

#### Definition

	GET https://admin.mailroute.net/api/vi/email_account/


#### Arguments

**none**  

#### Example Request

	curl -s --dump-header - \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		https://admin.mailroute.net/api/vi/email_account/


#### Example Response

	HTTP/1.0 200 OK
	Date: Mon, 18 Feb 2013 18:10:34 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	Cache-Control: no-cache
	
	
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

	DELETE https://admin.mailroute.net/api/vi/email_account/66/


#### Arguments

**none**  

#### Example Request

	curl -s --dump-header - -X DELETE \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		https://admin.mailroute.net/api/vi/email_account/66/


#### Example Response

	HTTP/1.0 204 NO CONTENT
	Date: Mon, 18 Feb 2013 18:10:43 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Length: 0
	Content-Type: text/html; charset=utf-8


### The Email Account Alias Object

#### Definition

	GET https://admin.mailroute.net/api/vi/localpart_alias/schema/


#### Arguments

**none**  

#### Example Request

	curl -s --dump-header - \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		https://admin.mailroute.net/api/vi/localpart_alias/schema/


#### Example Response

	HTTP/1.0 200 OK
	Date: Mon, 18 Feb 2013 18:10:34 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	Cache-Control: no-cache
	
	
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

	POST https://admin.mailroute.net/api/vi/localpart_alias/


#### Arguments

parameter | required | default | description
-----|-----|-----|-----|
localpart|*required*| |String - the localpart of the email address|
email_account|*required*| |String - email_account_uri|


#### Example Request

	curl -s --dump-header - -X POST \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		--data '   { \ 
	           "localpart" : "testalias", \ 
	           "email_account" : "/api/v1/email_account/66/" \ 
	        }' \
		https://admin.mailroute.net/api/vi/localpart_alias/


#### Example Response

	HTTP/1.0 201 CREATED
	Date: Mon, 18 Feb 2013 18:10:35 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	Location: http://127.0.0.1:8000/api/v1/localpart_alias/118/
	
	
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

	PUT https://admin.mailroute.net/api/vi/localpart_alias/118/


#### Arguments

parameter | required | default | description
-----|-----|-----|-----|
localpart|*required*| |String - the localpart of the email address|
email_account|*required*| |String - email_account_uri|


#### Example Request

	curl -s --dump-header - -X PUT \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		--data '   { \ 
	           "localpart" : "renamedtestalias" \ 
	        }' \
		https://admin.mailroute.net/api/vi/localpart_alias/118/


#### Example Response

	HTTP/1.0 202 ACCEPTED
	Date: Mon, 18 Feb 2013 18:10:36 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	
	
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

	GET https://admin.mailroute.net/api/vi/localpart_alias/


#### Arguments

**none**  

#### Example Request

	curl -s --dump-header - \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		https://admin.mailroute.net/api/vi/localpart_alias/


#### Example Response

	HTTP/1.0 200 OK
	Date: Mon, 18 Feb 2013 18:10:37 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	Cache-Control: no-cache
	
	
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

	DELETE https://admin.mailroute.net/api/vi/localpart_alias/118/


#### Arguments

**none**  

#### Example Request

	curl -s --dump-header - -X DELETE \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		https://admin.mailroute.net/api/vi/localpart_alias/118/


#### Example Response

	HTTP/1.0 204 NO CONTENT
	Date: Mon, 18 Feb 2013 18:10:41 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Length: 0
	Content-Type: text/html; charset=utf-8


### The User Policy Object

#### Definition

	GET https://admin.mailroute.net/api/vi/policy_user/schema/


#### Arguments

**none**  

#### Example Request

	curl -s --dump-header - \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		https://admin.mailroute.net/api/vi/policy_user/schema/


#### Example Response

	HTTP/1.0 200 OK
	Date: Mon, 18 Feb 2013 18:10:37 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	Cache-Control: no-cache
	
	
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

	PUT https://admin.mailroute.net/api/vi/policy_user/178/


#### Arguments

parameter | required | default | description
-----|-----|-----|-----|
user|*required*| |String - user_uri|
priority| |1|Integer - priority - higher priority takes precedence in domain/user policy settings|
addr_extension_bad_header| | |String - address extension - bad header|
addr_extension_banned| | |String - address extension - banned file|
addr_extension_spam| | |String - address extension - spam|
addr_extension_virus| | |String - address extension - virus|
bad_header_lover| |N|Character - "Y\|N" - deliver bad headers to recipient instead of qtn|
banned_files_lover| |N|Character - "Y\|N" - deliver banned files to recipient instead of qtn|
spam_lover| |N|Character - "Y\|N" - deliver spam to recipient instead of qtn|
unchecked_lover| |N|Character - "Y\|N" - deliver unchecked files to recipient instead of qtn|
virus_lover| |N|Character - "Y\|N" - deliver virus-infected files to recipient instead of qtn|
bypass_banned_checks| |N|Character - "Y\|N" - disable banned file checks|
bypass_header_checks| |Y|Character - "Y\|N" - disable bad header checks|
bypass_spam_checks| |N|Character - "Y\|N" - disable spam checks|
bypass_virus_checks| |N|Character - "Y\|N" - disable virus checks|
bad_header_quarantine_to| |sql:|String - where to redirect bad hdr, "sql:" for quarantine|
banned_quarantine_to| |sql:|String - where to redirect banned, "sql:" for quarantine|
spam_quarantine_to| |sql:|String - where to redirect spam, "sql:" for quarantine|
unchecked_quarantine_to| |sql:|String - where to redirect unchecked, "sql:" for quarantine|
virus_quarantine_to| |sql:|String - where to redirect virus, "sql:" for quarantine|
message_size_limit| | |Integer - max size in bytes, 0 to disable|
spam_kill_level| |7|Float - score above which to quarantine spam|
spam_quarantine_cutoff_level| |NULL|Float - score above which email isn't even quarantined|
spam_subject_tag2| |NULL|String - prepended to subject of messages scoring > spam_tag2_level|
spam_subject_tag3| |NULL|String - prepended to subject of messages scoring > spam_tag3_level|
spam_tag_level| |-9999|Float - score above this adds X-Spam-* headers to emails|
spam_tag2_level| |NULL|Float - score above this adds spam_subject_tag2 text to subject, redirect to user+ext@domain.com if addr_extension_spam is set|
spam_tag3_level| |NULL|Float - score above this adds spam_subject_tag3 text to subject, redirect to user+ext@domain.com if addr_extension_spam is set|
warnbadhrecip| |N|Character - "Y\|N" - warn recipient that a bad header message was quarantined|
warnbannedrecip| |N|Character - "Y\|N" - warn recipient that a banned file message was quarantined|
warnvirusrecip| |N|Character - "Y\|N" - warn recipient that a virus-infected message was quarantined|


#### Example Request

	curl -s --dump-header - -X PUT \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		--data '   { \ 
	           "spam_tag2_level" : 5.5, \ 
	           "spam_subject_tag2" : "Updated spam_subject_tag2", \ 
	           "spam_kill_level" : 9 \ 
	        }' \
		https://admin.mailroute.net/api/vi/policy_user/178/


#### Example Response

	HTTP/1.0 202 ACCEPTED
	Date: Mon, 18 Feb 2013 18:10:38 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	
	
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


### The Email_account White and Blacklists Object

#### Definition

	GET https://admin.mailroute.net/api/vi/wblist/schema/


#### Arguments

**none**  

#### Example Request

	curl -s --dump-header - \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		https://admin.mailroute.net/api/vi/wblist/schema/


#### Example Response

	HTTP/1.0 200 OK
	Date: Mon, 18 Feb 2013 18:10:39 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	Cache-Control: no-cache
	
	
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


### Creating an Email_account White and Blacklists

#### Definition

	POST https://admin.mailroute.net/api/vi/wblist/


#### Arguments

parameter | required | default | description
-----|-----|-----|-----|
email_account|*required*| |String - email_account_uri|
email|*required*| |String - address to be whitelisted|
wb|*required*| |Char - W|B - Whitelist or Blacklist|


#### Example Request

	curl -s --dump-header - -X POST \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		--data '   { \ 
	           "email" : "whitelist.com", \ 
	           "wb" : "w", \ 
	           "email_account" : "/api/v1/email_account/66/" \ 
	        }' \
		https://admin.mailroute.net/api/vi/wblist/


#### Example Response

	HTTP/1.0 201 CREATED
	Date: Mon, 18 Feb 2013 18:10:40 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	Location: http://127.0.0.1:8000/api/v1/wblist/78/
	
	
	{
	   "resource_uri" : "/api/v1/wblist/78/",
	   "email" : "whitelist.com",
	   "domain" : null,
	   "wb" : "w",
	   "email_account" : null,
	   "rid" : "1110000066",
	   "id" : 78
	}


Deleting an Email_account White and Blacklists

#### Definition

	DELETE https://admin.mailroute.net/api/vi/wblist/78/


#### Arguments

**none**  

#### Example Request

	curl -s --dump-header - -X DELETE \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		https://admin.mailroute.net/api/vi/wblist/78/


#### Example Response

	HTTP/1.0 204 NO CONTENT
	Date: Mon, 18 Feb 2013 18:10:40 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Length: 0
	Content-Type: text/html; charset=utf-8


### The Account Notification Task Object

#### Definition

	GET https://admin.mailroute.net/api/vi/notification_account_task/


#### Arguments

**none**  

#### Example Request

	curl -s --dump-header - \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		https://admin.mailroute.net/api/vi/notification_account_task/


#### Example Response

	HTTP/1.0 200 OK
	Date: Mon, 18 Feb 2013 18:10:38 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	Cache-Control: no-cache
	
	
	{
	   "objects" : [
	      {
	         "priority" : 4,
	         "fri" : true,
	         "wed" : true,
	         "resource_uri" : "/api/v1/notification_account_task/177/",
	         "tue" : true,
	         "sun" : false,
	         "email_account" : "/api/v1/email_account/66/",
	         "enable_default" : true,
	         "sat" : false,
	         "mon" : true,
	         "id" : 177,
	         "thu" : true,
	         "enabled" : false
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


### Updating an Account Notification Task

#### Definition

	PUT https://admin.mailroute.net/api/vi/notification_account_task/177/


#### Arguments

parameter | required | default | description
-----|-----|-----|-----|
account|*required*| |String - account_uri|
enable_default| |true|Boolean - use the domain-wide settings (only applies to user notification task)|
enabled| |false|Boolean - enable sending of notifications|
mon| |true|Boolean - send on this day|
tue| |true|Boolean - send on this day|
wed| |true|Boolean - send on this day|
thu| |true|Boolean - send on this day|
fri| |true|Boolean - send on this day|
sat| |false|Boolean - send on this day|
sun| |false|Boolean - send on this day|


#### Example Request

	curl -s --dump-header - -X PUT \
		-H 'Content-Type: application/json' \
		-H 'Authorization: ApiKey <login>:<apikey>' \
		--data '   { \ 
	           "sun" : "true", \ 
	           "enable_default" : "false", \ 
	           "account" : "/api/v1/email_account/66/", \ 
	           "sat" : "true", \ 
	           "enabled" : "true" \ 
	        }' \
		https://admin.mailroute.net/api/vi/notification_account_task/177/


#### Example Response

	HTTP/1.0 202 ACCEPTED
	Date: Mon, 18 Feb 2013 18:10:39 GMT
	Server: WSGIServer/0.1 Python/2.7.2
	Vary: Accept, Cookie
	Content-Type: application/json; charset=utf-8
	
	
	{
	   "priority" : 10,
	   "fri" : true,
	   "account" : "/api/v1/email_account/66/",
	   "wed" : true,
	   "resource_uri" : "/api/v1/notification_account_task/177/",
	   "tue" : true,
	   "sun" : true,
	   "email_account" : "/api/v1/email_account/66/",
	   "enable_default" : false,
	   "sat" : true,
	   "mon" : true,
	   "id" : 177,
	   "thu" : true,
	   "enabled" : true
	}


