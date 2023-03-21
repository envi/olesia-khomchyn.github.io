# VendorEmailConfigurations

## Get the list of Vendor Email Configurations

### <span style="color: #F05D30">Path</span>
GET /odata/VendorEmailConfigurations

### <span style="color: #F05D30">Description</span>
Returns the list of Vendor Email Configurations within a logged organizations. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).


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
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**vendorEmailId**: string *(uuid)* | Unique Identifier of the Vendor Email |
|**emailDescription**: string | Description of the Vendor Email |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**emailName**: string | Name of the Vendor Email |
|**emailAddress**: string | Address of the Vendor Email |
|**emailCC**: string | Carbon Copy of the Vendor Email |
|**emailBCC**: string | Blind Carbon Copy of the Vendor Email |
|**emailBody**: string | Body of the Vendor Email |
|**replyToTypeId**: string | Reply To Type Identifier |
|**replyToType**: string | Type of the Reply To |
|**replyToAddress**: string | Address of the Reply To |
|**requestReadReceipt**: boolean | Request a read Receipt |
|**activeStatus**: boolean | Is the Status of the Vendor Email active or not? |
|**dateAdded**: string *(date-time)* | Date when the Vendor Email was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Vendor Email |
|**addedByName**: string | Name of the user who added the Vendor Email |
|**lastUpdated**: string *(date-time)* | Last Date when the Vendor Email was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Vendor Email |
|**lastUpdatedByName**: string | Name of the last user who updated the Vendor Email |
|**confirmOrders**: boolean | Orders Confirmation Email |
|**doNotIncludeContactInfo**: boolean | Do Not Include Contact Info |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "vendorEmailId": "00000000-0000-0000-0000-000000000000",
      "emailDescription": "string",
      "vendorId": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "facilityNo": "string",
      "facilityName": "string",
      "emailName": "string",
      "emailAddress": "string",
      "emailCC": "string",
      "emailBCC": "string",
      "emailBody": "string",
      "replyToTypeId": "string",
      "replyToType": "string",
      "replyToAddress": "string",
      "requestReadReceipt": "boolean",
      "activeStatus": "boolean",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "addeddByName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByName": "string",
      "confirmOrders": "boolean",
      "doNotIncludeContactInfo": "boolean"
      }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```


## Get the specified Vendor Email Configuration

### <span style="color: #F05D30">Path</span>
GET odata/VendorEmailConfigurations({VendorEmailId})

### <span style="color: #F05D30">Description</span>
Returns the details of the Vendor Email Configuration specified by ID within a logged organization.

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**includeInactiveVendors** <br> boolean default: false <br> *in query* | Include inactive Vendors. |
|**includeInactiveFacilities** <br> boolean default: false <br> *in query* | Include inactive Facilities. |
|**vendorEmailId**: string *(uuid)*  <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Vendor Email Configuration here. |
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
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**vendorEmailId**: string *(uuid)* | Unique Identifier of the Vendor Email |
|**emailDescription**: string | Description of the Vendor Email |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**emailName**: string | Name of the Vendor Email |
|**emailAddress**: string | Address of the Vendor Email |
|**emailCC**: string | Carbon Copy of the Vendor Email |
|**emailBCC**: string | Blind Carbon Copy of the Vendor Email |
|**emailBody**: string | Body of the Vendor Email |
|**replyToTypeId**: string | Reply To Type Identifier |
|**replyToType**: string | Type of the Reply To |
|**replyToAddress**: string | Address of the Reply To |
|**requestReadReceipt**: boolean | Request a read Receipt |
|**activeStatus**: boolean | Is the Status of the Vendor Email active or not? |
|**dateAdded**: string *(date-time)* | Date when the Vendor Email was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Vendor Email |
|**addedByName**: string | Name of the user who added the Vendor Email |
|**lastUpdated**: string *(date-time)* | Last Date when the Vendor Email was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Vendor Email |
|**lastUpdatedByName**: string | Name of the last user who updated the Vendor Email |
|**confirmOrders**: boolean | Orders Confirmation Email |
|**doNotIncludeContactInfo**: boolean | Do Not Include Contact Info |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "vendorEmailId": "00000000-0000-0000-0000-000000000000",
  "emailDescription": "string",
  "vendorId": "00000000-0000-0000-0000-000000000000",
  "vendorNo": "string",
  "vendorName": "string",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "facilityNo": "string",
  "facilityName": "string",
  "emailName": "string",
  "emailAddress": "string",
  "emailCC": "string",
  "emailBCC": "string",
  "emailBody": "string",
  "replyToTypeId": "string",
  "replyToType": "string",
  "replyToAddress": "string",
  "requestReadReceipt": "boolean",
  "activeStatus": "boolean",
  "dateAdded": "string (date-time)",
  "addedBy": "00000000-0000-0000-0000-000000000000",
  "addeddByName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByName": "string",
  "confirmOrders": "boolean",
  "doNotIncludeContactInfo": "boolean"
}
```
