# VendorAddresses

## Get the list of vendor addresses

### <span style="color: #F05D30">Path</span>
GET /odata/VendorAddresses

### <span style="color: #F05D30">Description</span>
Returns the list of vendor addresses within a logged organization.  You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).


### <span style="color: #F05D30">Request parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**includeInactiveVendors** <br> boolean default: false <br> *in query* | Include inactive Vendors. |
|**includeInactiveFacilities** <br> boolean default: false <br> *in query* | Include inactive Facilities. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.| 
|**$filter**: string <br> *in query* | Restricts the set of items returned. The maximum number of expressions is 100. | 
|**$orderby**: string <br> *in query* | Specifies the order in which items are returned. The maximum number of expressions is 5. | 
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string default: <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|


### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
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
|**vendorAddressId**: string *(uuid)* | Unique Identifier of the Vendor Address |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**description**: string | Description of the Vendor Address |
|**address**: string | The first Address for shipping or billing purposes |
|**address2**: string | The second Address for shipping or billing purposes |
|**city**: string | City |
|**state**: string | State |
|**zip**: string | Zip |
|**country**: string | Country |
|**url**: string | URL |
|**dateAdded**: string *(date-time)* | Date when the Vendor Address was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Vendor Address |
|**addedByName**: string | Name of the user who added the Vendor Address |
|**lastUpdated**: string *(date-time)* | Last Date when the Vendor Address was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Vendor Address |
|**lastUpdatedByName**: string | Name of the last user who updated the Vendor Address |
|**activeStatus**: boolean | Is the Status of the Vendor Address active or not? |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "vendorAddressId": "00000000-0000-0000-0000-000000000000",
      "vendorId": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "facilityNo": "string",
      "facilityName": "string",
      "description": "string",
      "address": "string",
      "address2": "string",
      "city": "string",
      "state": "string",
      "zip": "string",
      "country": "string",
      "url": "string",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "addeddByName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByName": "string",
      "activeStatus": "boolean"
      }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```

## Create a new vendor address

### <span style="color: #F05D30">Path</span>
POST /odata/Vendors({VendorId})/VendorAddresses

### <span style="color: #F05D30">Description</span>
Creates a new vendor address within a logged organization and a specified vendor only for active vendors and active facilities.

### <span style="color: #F05D30">Request body</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**description**: string <br> <span style="color: #F05D30">**required**</span> | Description of the Vendor Address |
|**facilityId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> | Unique Identifier of the Facility |
|**address**: string <br> <span style="color: #F05D30">**required**</span> | The first Address for shipping or billing purposes |
|**address2**: string | The second Address for shipping or billing purposes |
|**city**: string <br> <span style="color: #F05D30">**required**</span> | City |
|**state**: string <br> <span style="color: #F05D30">**required**</span> | State |
|**zip**: string <br> <span style="color: #F05D30">**required**</span>| Zip |
|**country**: string | Country |
|**url**: string | URL |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML<br>Request Example"
{
  "description": "string",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "address": "string",
  "address2": "string",
  "city": "string",
  "state": "string",
  "zip": "string",
  "country": "string",
  "url": "string"
}
```

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|   
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request.|

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
"00000000-0000-0000-0000-000000000000"

```

## Get the specified vendor asddress

### <span style="color: #F05D30">Path</span>
GET /odata/VendorAddresses({vendorAddressId})

### <span style="color: #F05D30">Description</span>
Returns the details of the vendor address specified by ID within a logged organization.

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**includeInactiveVendors** <br> boolean default: false <br> *in query* | Include inactive Vendors. |
|**includeInactiveFacilities** <br> boolean default: false <br> *in query* | Include inactive Facilities. |
|**vendorAddressId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Vendor Address here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version. |   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |


### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**404 Not Found** | Specified ID is absent in the system. |
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request. |


### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**vendorAddressId**: string *(uuid)* | Unique Identifier of the Vendor Address |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**description**: string | Description of the Vendor Address |
|**address**: string | The first Address for shipping or billing purposes |
|**address2**: string | The second Address for shipping or billing purposes |
|**city**: string | City |
|**state**: string | State |
|**zip**: string | Zip |
|**country**: string | Country |
|**url**: string | URL |
|**dateAdded**: string *(date-time)* | Date when the Vendor Address was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Vendor Address |
|**addedByName**: string | Name of the user who added the Vendor Address |
|**lastUpdated**: string *(date-time)* | Last Date when the Vendor Address was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Vendor Address |
|**lastUpdatedByName**: string | Name of the last user who updated the Vendor Address |
|**activeStatus**: boolean | Is the Status of the Vendor Address active or not? |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "vendorAddressId": "00000000-0000-0000-0000-000000000000",
  "vendorId": "00000000-0000-0000-0000-000000000000",
  "vendorNo": "string",
  "vendorName": "string",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "facilityNo": "string",
  "facilityName": "string",
  "description": "string",
  "address": "string",
  "address2": "string",
  "city": "string",
  "state": "string",
  "zip": "string",
  "country": "string",
  "url": "string",
  "dateAdded": "string (date-time)",
  "addedBy": "00000000-0000-0000-0000-000000000000",
  "addeddByName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByName": "string",
  "activeStatus": "boolean"
}
```
