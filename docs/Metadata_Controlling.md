In general, there are three levels of metadata specification: ```none```, ```minimal```, and ```full```. ```Default``` metadata level is minimal, so the service removes metadata information from the payload wherever possible.

Taking into account your need of application, you can request the needed amount of metadata information included in the payload.

If you want to specify the amount of included metadata information in the response, use ```format``` query option of an OData request as a part of URL with specified ```odata.metadata``` parameter. For example, to specify none level, which means no metadata at all, URL should look like the following:

**```https://<HOSTNAME>/<resource>?$format=application/json;odata.metadata=none```**

for example, ```<HOSTNAME> = api-demo.envi.net```

The example shows that $format option should also include expected content type of the response (in this case application/json).

## <span style="color: #F05D30">none</span>

If you do not need metadata information, use ```odata.metadata=none```. It means that the service omits metadata information other than ```odata.nextLink``` and ```odata.count```. The following example shows the request/response for the case based on the Inventory module:


<span style="color: ##4F5FBB">Request Example </span>

``` json title="Example"
https://<HOSTNAME>/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)?$format=application/json;odata.metadata=none
    
```
(for example, ```<HOSTNAME> = api-demo.envi.net```)