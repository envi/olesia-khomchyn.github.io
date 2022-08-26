# Retrieving Data using cURL
The cURL is a command line tool and library for transferring data with URL syntax. The cURL provides easy access to the HTTP protocol (among others) directly from the command line and therefore an ideal way of interacting with the database over the HTTP REST API.

Use the cURL of Envi OData API to make the requests, as well as get, send, and retrieve the data. The cURL sends the request that contains a method (POST, GET, PUT, or PATCH), a number of request headers, parameters, and a URL. The cURL provides a generic, language-agnostic way to demonstrate HTTP requests and responses with a status line (indicating whether things went well), response headers, and also a response body. The body part is the plain data you requested, like the actual HTML.

For example, if you want to use the cURL command line tool to retrieve the entities list, use the GET method:

``` title="Example"
curl -X GET --header 'Accept: application/json' --header 'api-
version: 1.0' --header 'Authorization: ' 'https:///odata/Inventory'
    
```