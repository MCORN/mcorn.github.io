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

I am using [https://github.com/joshuairl/oauth2.cfc](https://github.com/joshuairl/oauth2.cfc) as a base. To get this to work, I made a small change to allow send the request body in JSON format, which is what Dropbox wants, and removed pulling the client object header into the request header as this crashed. Changes are available on top of the base at [https://github.com/MCORN/oauth2.cfc](https://github.com/MCORN/oauth2.cfc).

* Code sample for landing page

```
<cfscript>
	// Initiate with client_id and client_secret as per Dropbox Apps setup (App key and App secret respectively)
	oauth2client = new oauth2.client(
	  client_id = '<api_key_here>',
	  client_secret = '<api_secret_here>', 
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

* Code sample for callback page

```
<cfscript>
	oauth2client = new oauth2.client(
	  client_id = '<api_key_here>',
	  client_secret = '<api_secret_here>', 
	  options = { 
	    site: '', // auth site base url
	    authorize_url: 'https://www.dropbox.com/1/oauth2/authorize', // relative or absolute path to authorize
	    token_url: 'https://api.dropboxapi.com/1/oauth2/token'  // relative or absolute path to get token
	  }
	);

	// Once they arrive at on this callback page, you will need to request the token with your retrieved code.
	token = oauth2client.auth_code().get_token(code = '#URL.code#', params = { 'redirect_uri' = 'http://localhost:8081/test/callback.cfm'});
	
	// Sample get_space_usage call
	response = token.post(path = 'https://api.dropboxapi.com/2/users/get_space_usage');

	// Sample list_folder call
	response = token.post(path = 'https://api.dropboxapi.com/2/files/list_folder', opts = { headers = {"Content-Type" =  "application/json" }, json = { 
    "path": "",
    "recursive": false,
    "include_media_info": false,
    "include_deleted": false}
});

	writeDump(var="#response#");
</cfscript>
```
