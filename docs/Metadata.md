Envi API contains standard OData metadata endpoint. The metadata describes the types, sets, functions, and actions understood by the OData service. You can find the full list of Entity Data Module here:

```https://<HOSTNAME>/odata/$metadata```

(for example, ```<HOSTNAME> = api-demo.envi.net```)

You can use the metadata to understand how to query and interact with entities in the service. Most OData client libraries use this information to drive the generation of client-side classes to represent server types and aid programmability.

There are some limitations with ```$metadata``` though:

 - Lots of metadata mean a big document.
 - It isn't queryable. So if you want to find Types that have an Address property you have to retrieve the whole EDMX and search the xml, yourself.
OData protocol may include additional metadata information included in a response. Additional metadata appearance in the response can be configured by specifying additional query options in the request.

In general, there are three levels of metadata specification: none, minimal, and full. Default metadata level is minimal, so no metadata information is included in a response.

OData protocol may include additional metadata information included in a response. The metadata describes the types, sets, functions, and actions understood by the OData service.

You can use the metadata to understand how to query and interact with entities in the service. Also, additional metadata appearance in the response can be configured by specifying additional query options in the request.

Most OData client libraries use this information to drive the generation of client-side classes to represent server types and aid programmability.

There are some limitations with ```$metadata``` though:

1. It is all or nothing. Lots of metadata means a big document.
2. It forces the server to prepare metadata for every type in the system, forcing an up front, rather than on demand model upon the service.
3. It isn't queryable. So if you want to find Types that have an Address property you have to retrieve the whole EDMX and search the xml, yourself.








