
# StudentDataApi
## Contents
[Login user with "Admin" Role](##Login-user-with-"Admin"-Role)
## User Ragistration
### Request 
##### Method - `POST`
##### Url - `localhost/api/Account/Register`
##### Header -  `Content-Type = application/json`
##### Request Body
Raw Json eg.
```
{
	"Email":"nazmul@test.com",
	"Password":"Asdf@1234",
	"ConfirmPassword":"Asdf@1234"
}
```
## Access Token (login)
### Request 
##### Method - `POST`
##### Url - `localhost/Token`
##### Header - `Content-Type - application/x-www-form-urlencoded`
##### Request Body
form-urlencoded
```
grant_type = password
username   = <user name> 
password   = <user password>
```
Example-
```
grant_type = password
username   = sdtareq@test.com 
password   = Asdf@1234
```
##### Response Body
```
{
	"access_token": "Tiu5JfWmncI5YMD15VOYL7LrVJLhR8tfJc4YGdAtFxGyQ5vs67O-R94VMsUMx-mAsxrNQWwFCUb0zm--qTFkSeWwY-4eJ1E2FuA0E8SZF0u2Bp7OR3R2ZCXdyh_R5D6ekb2vHGjBthJX-rxduH8ygmSs6mdptao2R8MiZQbuhJJQZT25_U2ZmNjO8SyotWqe5nQmuVgds2k9-oaJb61DX6VOOBWyZKFLCSbki8inYoJMKpjPtSzLNx2usz0N8kBmtahgEqvPVQfU5dVaJxa_CgDtAsykFJj3IiAZ4eoc5qzpHLib_suS8W3dGrR0k0DnGV0BFc9-0-NuZIYZHLwUP8yAPrkfQFOXRNM4-R65GiLXOd_j5LY9XPLbhFNlgyUVkijjz_QqbRDicrou-QvcMtkyjnmjPaEnfB9xTxKKwC9L_rAK46A1DPK0h9niZPysJhZ42n8fuHQcaD75svhG3n9_6pIEW_PL85XxfS2--PE",
	"token_type": "bearer",
	"expires_in": 1209599,
	"userName": "sdtareq@test.com",
	".issued": "Fri, 02 Nov 2018 11:54:04 GMT",
	".expires": "Fri, 16 Nov 2018 11:54:04 GMT"
}
```

## Get Current User Info
### Request 
##### Method - `GET`
##### Url - `localhost//api/Account/UserInfo`
##### Header - `Authorization = Bearer <Token>`
##### Response Body
```
{
	"Email": "sdtareq@test.com",
	"HasRegistered": true,
	"LoginProvider": null
}
```

## Createing a Role 
### Request 
##### Method - `POST`
##### Params - `roleName = <name of the roel eg. Admin>`
##### Url - `localhost/api/roles/create`
##### Header -
 `Content-Type = application/json`<br>`Authorization = Bearer <Token>`


## Get All Roles 
### Request 
##### Method - `GET`
##### Url - `localhost/api/roles/getallroles`
##### Header - `Authorization = Bearer <Token>`
##### Response Body
```
[
	{
		"Users": [],
		"Id": "e11c2177-9a35-46a9-9b44-0dd4412c7bff",
		"Name": "Admin"
	},
	{
		"Users": [],
		"Id": "88179fa4-6275-417e-946b-f14c2a64ea0b",
		"Name": "SuperAdmin"
	},
	{
		"Users": [],
		"Id": "da1c7c32-15d3-4868-8c39-445c78028d45",
		"Name": "User"
	}
]	
```
## Assign roles for a user
### Request 
##### Method - `PUT`
##### Url - 
<code>localhost/api/Account/user/\{userId\}/roles</code><br>
eg.<br>
```localhost/api/Account/user/17ab6d09-adf0-4939-a51e-36ac8bf5ddb9/roles```
##### Header - 
```Authorization = Bearer <Token>```<br>
```Content-Type = application/json```
##### Request Body
Raw Json 
```
["Admin","User"] 
```


## Login user with "Admin" Role 
- Access action with [Authorize(Roles = "Admin")] 
- Accessing "Get(id)" Action from ValuesController. 
### Request 
##### Method - `GET`
##### Url - 
<code>localhost/api/values/{id} </code><br>
eg.<br>
```localhost/api/values/1```
##### Header - ```Authorization = Bearer <Token>```
 ##### Response Body
```
"Nazmul"
```

## Login user with "Admin" Role 
- Access action with [Authorize(Roles = "User")] 
- Accessing "Get()" Action from ValuesController. 
### Request 
##### Method - `GET`
##### Url - 
<code>localhost/api/values </code>
##### Header - ```Authorization = Bearer <Token>```
 ##### Response Body
```
{
	"Message": "Authorization has been denied for this request."
}
```

<!--
## T
### Request 
##### Method - ``
##### Url - `localhost/`
##### Header - ``
##### Request Body
```

```
##### Response Body
```

```
-->
