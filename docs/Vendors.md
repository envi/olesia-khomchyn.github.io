# Vendors

## Get the list of vendors

### <span style="color: #F05D30">Path</span>
GET /odata/Vendors

### <span style="color: #F05D30">Description</span>
Returns the paged list of existing vendors within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).


### <span style="color: #F05D30">Request parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition. |  
|**$orderby**: string <br> *in query* | Sorts the results.|
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>

| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**400 Bad Request** | The limit for the ```$top``` query has been exceeded. The value from the incoming request is 'N' (N is your value from the request). You can find the data on the current limit [here](Options_and_Limitations.md#top-and-skip).
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|


### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**organizationId**: string *(uuid)* | Unique Identifier of the Organization |
|**organizationNo**: string | Indentification Number of the Organization |
|**organizationName**: string | Name of the Organization |
|**vendorNotes**: string | Comments concerning the Vendor |
|**dateAdded**: string *(date-time)* | Date when the Vendor was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Vendor |
|**addedByName**: string | Name of the user who added the Vendor |
|**lastUpdated**: string *(date-time)* | Last Date when the Vendor was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Vendor |
|**lastUpdatedByName**: string | Name of the last user who updated the Vendor |
|**activeStatus**: boolean | Is the Vendor active or not? |
|**url**: string | Uniform Resource Locator |
|**systemVendorName**: string | Name of the System Vendor |
|**ediVendorNo**: string | Code of the Supplier EDI who sells products |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "vendorId": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "organizationId": "00000000-0000-0000-0000-000000000000",
      "organizationNo": "string",
      "organizationName": "string",
      "vendorNotes": "string",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "addedByName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByName": "string",
      "activeStatus": "boolean",
      "url": "string",
      "systemVendorName": "string",
      "ediVendorNo": "string"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```

## Get the specified vendor

### <span style="color: #F05D30">Path</span>
GET /odata/Vendors({vendorId})

### <span style="color: #F05D30">Description</span>
Returns the details of the vendor specified by ID.

### <span style="color: #F05D30">Request body</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:420px">Explanation</div>  |                      
|-----:|:-------|
|**vendorId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Vendor here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**404 Not Found**| Specified ID is absent in the system. |
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request. |

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**organizationId**: string *(uuid)* | Unique Identifier of the Organization |
|**organizationNo**: string | Indentification Number of the Organization |
|**organizationName**: string | Name of the Organization |
|**vendorNotes**: string | Comments concerning the Vendor |
|**dateAdded**: string *(date-time)* | Date when the Vendor was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Vendor |
|**addedByName**: string | Name of the user who added the Vendor |
|**lastUpdated**: string *(date-time)* | Last Date when the Vendor was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Vendor |
|**lastUpdatedByName**: string | Name of the last user who updated the Vendor |
|**activeStatus**: boolean | Is the Vendor active or not? |
|**url**: string | Uniform Resource Locator |
|**systemVendorName**: string | Name of the System Vendor |
|**ediVendorNo**: string | Code of the Supplier EDI who sells products |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
   "vendorId": "00000000-0000-0000-0000-000000000000",
   "vendorNo": "string",
   "vendorName": "string",
   "organizationId": "00000000-0000-0000-0000-000000000000",
   "organizationNo": "string",
   "organizationName": "string",
   "vendorNotes": "string",
   "dateAdded": "string (date-time)",
   "addedBy": "00000000-0000-0000-0000-000000000000",
   "addedByName": "string",
   "lastUpdated": "string (date-time)",
   "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
   "lastUpdatedByName": "string",
   "activeStatus": "boolean",
   "url": "string",
   "systemVendorName": "string",
   "ediVendorNo": "string"
}
```

## Get the list of vendors

### <span style="color: #F05D30">Path</span>
POST /odata/Vendors/GetVendorsInfo(facilityId={facilityId})

### <span style="color: #F05D30">Description</span>
Returns the details of the predefined vendor(s) within the facility specified by ID.

### <span style="color: #F05D30">Request body</span>
Enter the value of the vendor(s) from the existing template.

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:420px">Explanation</div>  |                      
|-----:|:-------|
|**facilityId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Facility. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |


``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML <br> Request Example"
[
"value": ["00000000-0000-0000-0000-000000000000"]
]
```

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request. |

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorName**: string | Name of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**address1**: string | The first Address for shipping or billing purposes |
|**address2**: string | The second Address for shipping or billing purposes |
|**city**: string | City |
|**state**: string | State |
|**zip**: string | Zip |
|**country**: string | Country |
|**url**: string | Uniform Resource Locator |
|**accountNumber**: string | Number of the Vendor Account |
|**activeStatus**: boolean | Is the Vendor active or not? |
|**lastUpdated**: string *(date-time)* | Last Date when the Vendor was updated |
|**leadTime**: integer *(int32)* | Allowed Time for the Completion |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
[
  {
    "vendorId": "00000000-0000-0000-0000-000000000000",
    "vendorName": "string",
    "vendorNo": "string",
    "address1": "string",
    "address2": "string",
    "city": "string",
    "state": "string",
    "zip": "string",
    "country": "string",
    "url": "string",
    "accountNumber": "string",
    "activeStatus": "boolean",
    "lastUpdated": "string (date-time)",
    "leadTime": "integer (int32)"
  }
]
```









