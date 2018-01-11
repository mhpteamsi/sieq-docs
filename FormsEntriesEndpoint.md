# SIEQ Form Entries Endpoint

*URL:* `[websitedomain]/webapi/formentries/get`

**HTTP Method:** POST

### Query Parameters ###
| Name | Example Value |
| --- | --- |
| formname | sf_contactus |
| page | 1 (default) |
| resultsperpage | 50 (default) |
| sincedate | 1900-01-01 (default) |

### Headers ###
An authentication header with an access token is required. To retrieve a token, post your credentials to this URL:

`[website_url]/Sitefinity/Authenticate/SWT` 

**Use these POST parameters:**

| Name | Value |
| --- | --- |
| wrap_name | username |
| wrap_password | 8asdfasdfa |

See [How to get the headers in C#](https://gist.github.com/jmotes/0225ae77e498cabfb8986afdf3a811ff)

### Curl examples ###

**Getting the token:**
```
curl --request POST \
  --url https://mazergroup.azurewebsites.net/Sitefinity/Authenticate/SWT \
  --header 'content-type: application/x-www-form-urlencoded' \
  --data 'wrap_name=jmotes&wrap_password=******'
```

**Example SWT response:**

NOTE: you only need the `wrap_access_token` portion of the response. The C# example (link above) shows how to parse it out.

```
wrap_access_token=http%253a%252f%252fschemas.sitefinity.com%252fws%252f2011%252f06%252fidentity%252fclaims%252fuserid%3da61b857d-c805-6c22-9b58-ff00003d765f%26http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity%252fclaims%252fname%3djmotes%26http%253a%252f%252fschemas.sitefinity.com%252fws%252f2011%252f06%252fidentity%252fclaims%252frole%3d71dd8061-7e63-4b8c-9cd6-95d1bcb62726%253bEveryone%253bXmlConfigProvider%26http%253a%252f%252fschemas.sitefinity.com%252fws%252f2011%252f06%252fidentity%252fclaims%252frole%3d8efc7a02-3a17-4cc7-8bea-8efd1c8b0850%253bAuthenticated%253bXmlConfigProvider%26http%253a%252f%252fschemas.sitefinity.com%252fws%252f2011%252f06%252fidentity%252fclaims%252frole%3d8386039c-311e-4e50-8868-a7aa0ae5e3b9%253bBackendUsers%253bAppRoles%26http%253a%252f%252fschemas.sitefinity.com%252fws%252f2011%252f06%252fidentity%252fclaims%252frole%3ddc59cdd1-0d2f-410f-be0f-e51c1ad98d0c%253bAdministrators%253bAppRoles%26http%253a%252f%252fschemas.sitefinity.com%252fws%252f2011%252f06%252fidentity%252fclaims%252flastlogindate%3d2018-01-11%2b16%253a25%253a33Z%26http%253a%252f%252fschemas.sitefinity.com%252fws%252f2011%252f06%252fidentity%252fclaims%252fdomain%3dDefault%26TokenId%3db5fa0796-dd5d-40e0-99b7-8cac36f8eb4e%26Issuer%3dhttp%253a%252f%252flocalhost%253a60876%252fSitefinity%252fAuthenticate%252fSWT%26Audience%3dhttp%253a%252f%252flocalhost%253a60876%26ExpiresOn%3d1515691533%26HMACSHA256%3dofejCnqTaWXXXQrEgV6pNXw0%252fDxQK8TUcB7zoBSKxgk%253d&wrap_access_token_expires_in=3600
```

**Getting the form entries:**
```
curl --request GET \
  --url 'https://mazergroup.azurewebsites.net/webapi/formentries/get?formname=sf_contactus&page=2&resultsperpage=3&sincedate=2017-03-11' \
  --header 'authorization: "WRAP access_token=\"http%3a%2f%2fschemas.sitefinity.com%2fws%2f2011%2f06%2fidentity%2fclaims%2fuserid=a61b857d-c805-6c22-9b58-ff00003d765f&http%3a%2f%2fschemas.xmlsoap.org%2fws%2f2005%2f05%2fidentity%2fclaims%2fname=jmotes&http%3a%2f%2fschemas.sitefinity.com%2fws%2f2011%2f06%2fidentity%2fclaims%2frole=71dd8061-7e63-4b8c-9cd6-95d1bcb62726%3bEveryone%3bXmlConfigProvider&http%3a%2f%2fschemas.sitefinity.com%2fws%2f2011%2f06%2fidentity%2fclaims%2frole=8efc7a02-3a17-4cc7-8bea-8efd1c8b0850%3bAuthenticated%3bXmlConfigProvider&http%3a%2f%2fschemas.sitefinity.com%2fws%2f2011%2f06%2fidentity%2fclaims%2frole=8386039c-311e-4e50-8868-a7aa0ae5e3b9%3bBackendUsers%3bAppRoles&http%3a%2f%2fschemas.sitefinity.com%2fws%2f2011%2f06%2fidentity%2fclaims%2frole=dc59cdd1-0d2f-410f-be0f-e51c1ad98d0c%3bAdministrators%3bAppRoles&http%3a%2f%2fschemas.sitefinity.com%2fws%2f2011%2f06%2fidentity%2fclaims%2flastlogindate=2018-01-11+15%3a57%3a47Z&http%3a%2f%2fschemas.sitefinity.com%2fws%2f2011%2f06%2fidentity%2fclaims%2fdomain=Default&TokenId=fa39cd53-3a97-4678-8cf1-3e9c036b5457&Issuer=http%3a%2f%2flocalhost%3a60876%2fSitefinity%2fAuthenticate%2fSWT&Audience=http%3a%2f%2flocalhost%3a60876&ExpiresOn=1515689867&HMACSHA256=WH0zamqL3YuWrxaE%2fG9sWUSdnu9wQc5sDAytM2bV%2bas%3d\""' \
  --header 'content-type: application/x-www-form-urlencoded' \
```

### Example Entries Response ###
```
[
	{
		"EntryDate": "2017-03-12T22:47:58.36Z",
		"EntryFields": [
			{
				"Title": "First Name",
				"Value": "John"
			},
			{
				"Title": "Last Name",
				"Value": "Smith"
			},
			{
				"Title": "Email Address",
				"Value": "test@teamsi.com"
			},
			{
				"Title": "Phone Number",
				"Value": "5015555555"
			},
			{
				"Title": "Message",
				"Value": "test Message"
			}
		]
	},
	{
		"EntryDate": "2017-03-12T23:28:12.61Z",
		"EntryFields": [
			{
				"Title": "First Name",
				"Value": "Jane"
			},
			{
				"Title": "Last Name",
				"Value": "Doe"
			},
			{
				"Title": "Email Address",
				"Value": "test@teamsi.com"
			},
			{
				"Title": "Phone Number",
				"Value": "5015555555"
			},
			{
				"Title": "Message",
				"Value": "Testing message box"
			}
		]
	}
]
```
