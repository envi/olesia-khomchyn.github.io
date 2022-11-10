# Locations

## Get the list of locations

### <span style="color: #F05D30">Path</span>
GET /odata/Locations

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing locations within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

!!! note 

    This endpoint does not support logical operators (**and**, **or**, **in**, **gt**, **ge**, **lt**, **le**) for data filtering.

### <span style="color: #F05D30">Request Parameters</span>
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
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**400 Bad Request** | The limit for the ```$top``` query has been exceeded. The value from the incoming request is 'N' (N is your value from the request). You can find the data on the current limit [here](Options_and_Limitations.md#top-and-skip). |
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>

|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**defaultBillingAddressId**: <br> string *(uuid)* | Unique Identifier of the Default Address for billing purposes |
|**defaultBillingAddressNo**: string | Identification Number of the Default Address for billing purposes |
|**defaultBillingAddressName**: <br> string | Name of the Default Address for billing purposes |
|**defaultShippingAddressId**: <br> string *(uuid)* | Unique Identifier of the Default Address for shipping purposes |
|**defaultShippingAddressNo**: <br> string | Identification Number of the Default Address for shipping purposes |
|**defaultShippingAddressName**: <br> string | Name of the Default Address for shipping purposes |
|**glCode**: string | General Ledger Code |
|**activeStatus**: boolean | Is the Location active or not? |
|**defaultSyncFlag**: boolean | Is Inventory Location marked with Default Synchronization Flag or not? |
|**dateCreated**: string *(date-time)* | Date when the Location was added |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who added the Location |
|**createdByName**: string | Name of the user who added Location |
|**lastUpdated**: string *(date-time)* | Last Date when the Location was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Location |
|**lastUpdatedByName**: string | Name of the last user who updated the Location |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "locationId": "00000000-0000-0000-0000-000000000000",
      "locationNo": "string",
      "locationName": "string",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "facilityNo": "string",
      "facilityName": "string",
      "defaultBillingAddressId": "00000000-0000-0000-0000-000000000000",
      "defaultBillingAddressNo": "string",
      "defaultBillingAddressName": "string",
      "defaultShippingAddressId": "00000000-0000-0000-0000-000000000000",
      "defaultShippingAddressNo": "string",
      "defaultShippingAddressName": "string",
      "glCode": "string",
      "activeStatus": "boolean",
      "defaultSyncFlag": "boolean",
      "dateCreated": "string (date-time)",
      "createdBy": "00000000-0000-0000-0000-000000000000",
      "createdByName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByName": "string"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```

## Get the specified location

### <span style="color: #F05D30">Path</span>
GET /odata/Locations({locationId})

### <span style="color: #F05D30">Description</span>
Returns the details of the location specified by ID.

### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**locationId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Location here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**404 Not Found** | Specified ID is absent in the system. |
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**defaultBillingAddressId**: <br> string *(uuid)* | Unique Identifier of the Default Address for billing purposes |
|**defaultBillingAddressNo**: string | Identification Number of the Default Address for billing purposes |
|**defaultBillingAddressName**: <br> string | Name of the Default Address for billing purposes |
|**defaultShippingAddressId**: <br> string *(uuid)* | Unique Identifier of the Default Address for shipping purposes |
|**defaultShippingAddressNo**: <br> string | Identification Number of the Default Address for shipping purposes |
|**defaultShippingAddressName**: <br> string | Name of the Default Address for shipping purposes |
|**glCode**: string | General Ledger Code |
|**activeStatus**: boolean | Is the Location active or not? |
|**defaultSyncFlag**: boolean | Is Inventory Location marked with Default Synchronization Flag or not? |
|**dateCreated**: string *(date-time)* | Date when the Location was added |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who added the Location |
|**createdByName**: string | Name of the user who added Location |
|**lastUpdated**: string *(date-time)* | Last Date when the Location was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Location |
|**lastUpdatedByName**: string | Name of the last user who updated the Location |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "locationId": "00000000-0000-0000-0000-000000000000",
  "locationNo": "string",
  "locationName": "string",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "facilityNo": "string",
  "facilityName": "string",
  "defaultBillingAddressId": "00000000-0000-0000-0000-000000000000",
  "defaultBillingAddressNo": "string",
  "defaultBillingAddressName": "string",
  "defaultShippingAddressId": "00000000-0000-0000-0000-000000000000",
  "defaultShippingAddressNo": "string",
  "defaultShippingAddressName": "string",
  "glCode": "string",
  "activeStatus": "boolean",
  "defaultSyncFlag": "boolean",
  "dateCreated": "string (date-time)",
  "createdBy": "00000000-0000-0000-0000-000000000000",
  "createdByName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByName": "string"
}
```
