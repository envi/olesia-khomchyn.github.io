Versioning is an important aspect of any mature web service. It ensures that clients can rely on services to be stable over time, while still enabling service changes and new features. Envi implementation of API Versioning means that almost every request should provide a specific version using the api-version request header.

!!! note 

    Some of the standard OData endpoints, such as ```$metadata``` related or authentication endpoint (oauth2/token), do not require version specification.
    

Envi API supports advertising of versions – information about which service versions are currently supported and which are deprecated. This information is included as multi-value HTTP headers **api-supported-versions** and **api-deprecated-versions**. Their values indicate the supported and deprecated API versions, respectively. A deprecated version is still implemented but is expected to be removed in six months or more. When a version is no longer supported, it stops being advertised.

Client implementations can use the OPTIONS type of a request against the ```$metadata``` endpoint to find out a list of supported and deprecated versions. Now, Envi OData API supports only one version (1.0), but it will change soon. To check available versions, send the following request:


``` title="Request Example"
https://<HOSTNAME>/odata/$metadata
    
```
(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

``` cs title="Response Example"
HTTP/1.1 200 OK
    Allow: GET,OPTIONS
    Content-Length: 0
    Server: Microsoft-HTTPAPI/2.0
    OData-Version: 4.0
    api-supported-versions: 1.0

```

The following code shows how to specify the information on API in the request header using the C# programming language with the HTTP Client standard class:

``` cs title="Request Example"
var http = new HttpClient();
    http.DefaultRequestHeaders.Add("api-version", "1.0");

```

If you specify a non-existing version, Envi API returns a response with the 400 status code.

``` json title="Response Example"
HTTP/1.1 400 Bad Request
    api-supported-versions: 1.0
    {
      "error":
      {
        "code":"UnsupportedApiVersion",
        "message":"The HTTP resource that matches the request URI does not support the API version '1.1'.",
        "innerError":
        {
          "message":"No route providing a controller name with API version '1.1' was found to match request URI."
        }
      }
    }

```