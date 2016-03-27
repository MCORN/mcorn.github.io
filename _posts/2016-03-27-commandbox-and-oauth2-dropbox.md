---
title: CommandBox and OAuth2 to Dropbox in ColdFusion
updated: 2016-03-27 11:05
---

## CommandBox on Ubuntu 14.04

Easy to install and use. A few random things I had to look up...

* Use a fixed port


```
server start port=8081
```

* Access the Lucee admin console - http://127.0.0.1:8081/lucee/admin/server.cfm

## OAuth2 for Dropbox

* Using https://github.com/joshuairl/oauth2.cfc as a base
* Code sample so far

```
<cfscript>
	// Initiate with client_id and client_secret as per Dropbox Apps setup (App key and App secret respectively)
	oauth2client = new oauth2.client(
	  client_id = 'v8pake023bzaf2a',
	  client_secret = 'g9e76r0wlce3uml', 
	  options = { 
	    site: '', // auth site base url
	    authorize_url: 'https://www.dropbox.com/1/oauth2/authorize', // relative or absolute path to authorize
	    token_url: 'https://api.dropboxapi.com/1/oauth2/token'  // relative or absolute path to get token
	  }
	);

	// Build the authorize_url
	authorizeUrl = oauth2client.auth_code().authorize_url({ redirect_uri: 'http://localhost:8081/test/callback.cfm' });

	// Redirect user to authorize_url
	location(addtoken = false, url = authorizeUrl); 
</cfscript>
```
