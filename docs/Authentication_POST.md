# Authentication

## POST /oauth2/token

### <span style="color: #F05D30">Description</span>
The OData API provides authentication using OAuth 2.0 JWT. Before using Envi API, you should authenticate to obtain the JWT token. It is a simple and secure authentication mechanism that allows applications to acquire an access token for OData via a quick call to the Envi site.

### <span style="color: #F05D30">Request Parameters</span>
To obtain a JWT token for authentication, send a POST request to ```/oauth2/token``` endpoint with the following parameters:

<style>
td, th {
   border: none!important;
}
</style>

| <div style="width:200px">Parameter</div> | <div style="width:480px">Explanation</div>         |                      
|-----:|:-------|
|**grant_type**: string default: <br> password <br> <span style="color: #F05D30">**required**</span> <br> *in formData* | Grant Type of the auth request. Should be set to 'password'.|
|**client_id**: string default:<br> 099153c<br> 2625149bc8ecb3e85e03f0022 <br> <span style="color: #F05D30">**required**</span> <br> *in formData* | ID of the client performing auth request. |
|**username**: string <br> <span style="color: #F05D30">**required**</span> <br> *in formData* | Enter your User Name here. |
|**password**: string <br> <span style="color: #F05D30">**required**</span> <br> *in formData* | Enter your Password here. |
|**organizationNo**: string <br>*in formData* |Enter Organization No to log into not default organization. |

``` title="Example"
https://<hostname>/oauth2/token/grant_type=password&client_id=<client_id>&username=<username>&password=<password>&organizationNo=<organizationNo>
        
``` 

!!! note

     - The client_id **099153c2625149bc8ecb3e85e03f0022** is the same for all clients.
     - If you don’t specify ```organizationNo```, you will be logged into the default organization. In the Envi application, ```organizationNo``` is corresponding to the **Organization ID** field. You can find your ```organizationNo``` in **Organization** > **My Organization Details**. <br> ![image](img/Authentication.png)

Now, you need to use the ```access_token``` part of obtained JWT in the Authorization header of each request to the Envi API.

To authorize, in the **Parameters** section of the needed endpoint, paste the token to the **Authorization** field.


### <span style="color: #F05D30">Refreshing the token</span>
After the ```access_token``` got expired, you have two options to refresh it:

 - Send a separate request with the specified user name and password. In this case, hardcode your credentials in the application you are using.

**OR**

 - In automatic mode, exchange ```refresh_token``` to the new pair of ```access_token```/```refresh token```. For this:
    1. Send a POST request to ```/oauth2/token``` endpoint.
    2. Fill in the following:


| <div style="width:200px">Parameter</div>|<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**grant_type**: string | ```refresh_token``` |
|**client_id**: integer | 099153c2625149bc8ecb3e85e03f0022 |
|**refresh_token**: string| the ```refresh_token``` that was received during Authentication |

If the provided information is correct, you will receive a new pair of ```access_token/refresh_token```.

### <span style="color: #F05D30">Properties</span>
If the provided authentication information is correct, you will receive the following in the **Response Body**:

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Parameter</div>     |  <div style="width:380px">Explanation</div>         |                      
|-----:|:-------|
|**grant_type**: string | ```refresh_token``` |
|**access_token**: string| Token that you need for authentication. |
|**token_type**: string | Type of the token. It is always bearer in our app. |
|**expires_in**: integer | Number of seconds until the token expires. |
|**refresh_token**: string | Send this token to the server when ```access_token``` becomes expired, to obtain a new pair of ```access_token/refresh token```. |



### <span style="color: #F05D30">Responses</span>

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response</div>     |  <div style="width:380px">Explanation</div>         |                      
|-----:|:-------|
|**200 OK**|Undefined|
|**400 Bad Request**| An error occurred during the authorization process. |
|**400 (invalid_client_ID)** | Provided client ID is invalid. |
|**400 (invalid_grant)** | Grant Type is invalid. |
|**400 (maintenance)**| Application is currently down for maintenance. It will be back as soon as possible. |
|**400 (network restriction)** | You cannot log in from the current network. Contact your application administrator. |
|**400 (invalid cred.)** | Provided password or login is incorrect or was mistyped.  |
|**400 (no role)**| This account does not have any preconfigured role. Contact your application administrator. |
|**400 (no org.)** | No default organization is associated with this account. Contact your application administrator. |
|**400 (locked)** | This account has been locked. Check your email or contact your administrator to unlock it. |
|**400 (no active role)** | This account does not have any active role. Contact your application administrator. |

``` json title="Response Example (200 OK)"
{
  "access_token": "string",
  "token_type": "string",
  "expires_in": "integer",
  "refresh_token": "string"
}
```

``` json title="Response Example (400 Bad Request)"
{
  "error": "string",
  "error_description": "string"
}
```

### <span style="color: #F05D30">Authentication with cURL</span>
Each HTTP request of Envi OData API is authenticated. To authenticate with cURL do the following:

1. Specify the POST request method to use when communicating with the HTTP server. The -X signifies the method used for the request.
2. Submit the HTTP headers. Include an additional header for each key-value you’re submitting. The cURL should contain the **grant type**, **client ID**, **username**, **password**, and optional **organization No** headers.
3. Specify the URI. It is a standard HTTP header that contains URI to which the cURL server will redirect you.

In the response, you’ll receive the JWT token for authentication to perform all needed requests in the Envi API.

``` title="Example"
curl -X POST --header 'Content-Type: application/x-www-form-urlencoded' --header 'Accept: application/json' -d 'grant_type=password&client_id=<client_id>&username=<username>&password=<password>' 'https:<HOSTNAME>/oauth2/token'
        
``` 