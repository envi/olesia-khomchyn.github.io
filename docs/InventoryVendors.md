# InventoryVendors
## Get the cost history for the specified inventory vendor

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryVendors({inventoryVendorId})/costHistory

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing cost history records within inventory vendor specified by ID.

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>

|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**inventoryVendorId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory Vendor here.|
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
|**400 Bad Request** | The limit for the ```$top``` query has been exceeded. The value from the incoming request is 'N' (N is your value from the request). You can find the data on the current limit [here](Options_and_Limitations.md#top-and-skip).
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**inventoryVendorCostHistoryId**: <br> string *(uuid)* | Unique Identifier of the Inventory Vendor Cost History |
|**inventoryVendorId**: string *(uuid)* | Unique Identifier of the Inventory Vendor |
|**vendorName**: string | Name of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**inventoryVendorCostId**: <br> string *(uuid)*  | Unique Identifier of the Inventory Vendor Cost |
|**vendorCost**: number *(double)* | Cost of the Vendor |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**costUpdated**: string *(date-time)* | Last Date when the Cost was updated |
|**costUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Cost |
|**costUpdatedByName**: string | Name of the last user who updated the Cost |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "inventoryVendorCostHistoryId": "00000000-0000-0000-0000-000000000000",
      "inventoryVendorId": "00000000-0000-0000-0000-000000000000",
      "vendorName": "string",
      "vendorNo": "string",
      "inventoryVendorCostId": "00000000-0000-0000-0000-000000000000",
      "vendorCost": "number (double)",
      "vendorUOM": "string",
      "vendorConversionFactor": "integer (int32)",
      "costUpdated": "string (date-time)",
      "costUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "costUpdatedByName": "string"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```

## Get the list of purchasing units for the specified inventory vendor

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryVendors({inventoryVendorId})/purchasingUnits

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing purchasing units within inventory vendor specified by ID.

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.


### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**inventoryVendorId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory Vendor here.|
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
|**400 Bad Request** | The limit for the ```$top``` query has been exceeded. The value from the incoming request is 'N' (N is your value from the request). You can find the data on the current limit [here](Options_and_Limitations.md#top-and-skip).
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**inventoryVendorPurchasing<br>UnitId**: <br> string *(uuid)* | Unique Identifier of the Inventory Vendor Purchasing Unit |
|**inventoryVendorId**: string *(uuid)* | Unique Identifier of the Inventory Vendor |
|**vendorName**: string | Name of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**vendorCost**: number *(double)* | Cost of the Vendor |
|**activeStatus**: boolean | Is the status of Purchasing Unit active or not? |
|**lastVendorCost**: number *(double)* | Last Cost of the Vendor |
|**costLastUpdated**: string <br> *(date-time)* | Last Date when the Cost was updated |
|**costLastUpdatedBy**: <br> string *(uuid)* | Unique Identifier of the last user who updated the Cost |
|**costLastUpdatedByName**: <br> string | Name of the last user who updated the Cost |
|**dateAdded**: string *(date-time)* | Date when the Purchasing Unit was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Purchasing Unit |
|**addedByName**: string | Name of the last user who added the Purchasing Unit |
|**lastUpdated**: string *(date-time)* | Last Date when the Purchasing Unit was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Purchasing Unit |
|**lastUpdatedByName**: string | Name of the last user who updated the Purchasing Unit |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "inventoryVendorPurchasingUnitId": "00000000-0000-0000-0000-000000000000",
      "inventoryVendorId": "00000000-0000-0000-0000-000000000000",
      "vendorName": "string",
      "vendorNo": "string",
      "vendorUOM": "string",
      "vendorConversionFactor": "integer (int32)",
      "vendorCost": "number (double)",
      "activeStatus": "boolean",
      "lastVendorCost": "number (double)",
      "costLastUpdated": "string (date-time)",
      "costLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "costLastUpdatedByName": "string",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "addedByName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByName": "string"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```

## Get the list of all inventory vendors

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryVendors

### <span style="color: #F05D30">Description</span>
Returns the paged list of the all existing inventory vendors. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request Parameters</span>
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
|**400 Bad Request** | The limit for the ```$top``` query has been exceeded. The value from the incoming request is 'N' (N is your value from the request). You can find the data on the current limit [here](Options_and_Limitations.md#top-and-skip).
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:450px">Explanation</div>|                      
|-----:|:-------|
|**inventoryVendorId**: string *(uuid)* | Unique Identifier of the Inventory Item Vendor |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**vendorCost**: number *(double)* | Item Cost of the Vendor |
|**vendorPriority**: integer *(int32)* | Priority of the Vendor |
|**contractNo**: string | Number of the Contract |
|**contractExpDate**: string *(date-time)* | Expiration Date of the Contract |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**manufacturerId**: string *(uuid)* | Unique Identifier of the Manufacturer |
|**manufacturerNo**: string | Number of the Manufacturer |
|**manufacturerName**: string | Name of the Manufacturer |
|**gtin**: string | Global Trade Item Number |
|**costLastUpdated**: string *(date-time)* | Last Date when the Cost was updated |
|**costLastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Cost |
|**dateAdded**: string *(date-time)* | Date when the Vendor of Inventory Item was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added Inventory Item Vendor |
|**lastUpdated**: string *(date-time)* | Last Date when the Inventory Item Vendor was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the user who updated Inventory Item Vendor |
|**activeStatus**: boolean | Is the Status of the Inventory Item Vendor active or not? |
|**ndcNumber**: string | National Drug Code number |
|**lockCost**: boolean | Is the Cost of the Inventory Item Vendor locked or not? |
|**costLastUpdatedByUserName**: string | Name of the last user who updated the Cost |
|**addedByUserName**: string | Name of the user who added the Inventory Item Vendor |
|**lastUpdatedByUserName**: string | Name of the last user who updated Inventory Item Vendor |
|**pimKey**: string | Product Information Management Key |
|**altItemNo**: string | Alternative Item Number |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "inventoryVendorId": "00000000-0000-0000-0000-000000000000",
      "inventoryId": "00000000-0000-0000-0000-000000000000",
      "inventoryNo": "string",
      "vendorId": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "facilityNo": "string",
      "facilityName": "string",
      "vendorItemNo": "string",
      "vendorUOM": "string",
      "vendorConversionFactor": "integer (int32)",
      "vendorCost": "number (double)",
      "vendorPriority": "integer (int32)",
      "contractNo": "string",
      "contractExpDate": "string (date-time)",
      "manufacturerItemNo": "string",
      "manufacturerId": "00000000-0000-0000-0000-000000000000",
      "manufacturerNo": "string",
      "manufacturerName": "string",
      "gtin": "string",
      "costLastUpdated": "string (date-time)",
      "costLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "activeStatus": "boolean",
      "ndcNumber": "string",
      "lockCost": "boolean",
      "costLastUpdatedByUserName": "string",
      "addedByUserName": "string",
      "lastUpdatedByUserName": "string",
      "pimKey": "string",
      "altItemNo": "string"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}  
```

## Get the specified inventory vendor

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryVendors({inventoryVendorId})

### <span style="color: #F05D30">Description</span>
Returns the details of the inventory vendor specified by ID.

### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**inventoryVendorId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory Vendor here.|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**inventoryVendorId**: string *(uuid)* | Unique Identifier of the Inventory Item Vendor |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**vendorCost**: number *(double)* | Item Cost of the Vendor |
|**vendorPriority**: integer *(int32)* | Priority of the Vendor |
|**contractNo**: string | Number of the Contract |
|**contractExpDate**: string *(date-time)* | Expiration Date of the Contract |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**manufacturerId**: string *(uuid)* | Unique Identifier of the Manufacturer |
|**manufacturerNo**: string | Number of the Manufacturer |
|**manufacturerName**: string | Name of the Manufacturer |
|**gtin**: string | Global Trade Item Number |
|**costLastUpdated**: string *(date-time)* | Last Date when the Cost was updated |
|**costLastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Cost |
|**dateAdded**: string *(date-time)* | Date when the Vendor of Inventory Item was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added Inventory Item Vendor |
|**lastUpdated**: string *(date-time)* | Last Date when the Inventory Item Vendor was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the user who updated Inventory Item Vendor |
|**activeStatus**: boolean | Is the Status of the Inventory Item Vendor active or not? |
|**ndcNumber**: string | National Drug Code number |
|**lockCost**: boolean | Is the Cost of the Inventory Item Vendor locked or not? |
|**costLastUpdatedByUserName**: string | Name of the last user who updated the Cost |
|**addedByUserName**: string | Name of the user who added the Inventory Item Vendor |
|**lastUpdatedByUserName**: string | Name of the last user who updated Inventory Item Vendor |
|**pimKey**: string | Product Information Management Key |
|**altItemNo**: string | Alternative Item Number |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "inventoryVendorId": "00000000-0000-0000-0000-000000000000",
  "inventoryId": "00000000-0000-0000-0000-000000000000",
  "inventoryNo": "string",
  "vendorId": "00000000-0000-0000-0000-000000000000",
  "vendorNo": "string",
  "vendorName": "string",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "facilityNo": "string",
  "facilityName": "string",
  "vendorItemNo": "string",
  "vendorUOM": "string",
  "vendorConversionFactor": "integer (int32)",
  "vendorCost": "number (double)",
  "vendorPriority": "integer (int32)",
  "contractNo": "string",
  "contractExpDate": "string (date-time)",
  "manufacturerItemNo": "string",
  "manufacturerId": "00000000-0000-0000-0000-000000000000",
  "manufacturerNo": "string",
  "manufacturerName": "string",
  "gtin": "string",
  "costLastUpdated": "string (date-time)",
  "costLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "dateAdded": "string (date-time)",
  "addedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "activeStatus": "boolean",
  "ndcNumber": "string",
  "lockCost": "boolean",
  "costLastUpdatedByUserName": "string",
  "addedByUserName": "string",
  "lastUpdatedByUserName": "string",
  "pimKey": "string",
  "altItemNo": "string"
}   
```


## Partially update the specified inventory vendor

### <span style="color: #F05D30">Path</span>
PATCH /odata/InventoryVendors({inventoryVendorId})

### <span style="color: #F05D30">Description</span>
Partially updates the details of the inventory vendor specified by InventoryVendorId.

### <span style="color: #F05D30">Request Body</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryVendorId**: string *(uuid)* | Unique Identifier of the Inventory Item Vendor |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**vendorCost**: number *(double)* | Item Cost of the Vendor |
|**vendorPriority**: integer *(int32)* | Priority of the Vendor <br> <br> **Note**: Inventory Vendor that had the priority equal or less than specified value is moved down for one step. <br> <br> In case ```vendorPriority``` in the Request Body contains a value larger than quantity of Inventory Vendors for a specific facility, then the Inventory Vendor priority is changed to the lowest priority for an appropriate facility. <br> <br> In case a specified Inventory Vendor has the Inactive status, then the Inventory Vendor priority is changed only within inactive Inventory Vendors.
|**contractNo**: string | Number of the Contract |
|**contractExpDate**: string *(date-time)* | Expiration Date of the Contract |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**manufacturerId**: string *(uuid)* | Unique Identifier of the Manufacturer |
|**manufacturerNo**: string | Number of the Manufacturer |
|**manufacturerName**: string | Name of the Manufacturer |
|**gtin**: string | Global Trade Item Number |
|**costLastUpdated**: string *(date-time)* | Last Date when the Cost was updated |
|**costLastUpdatedBy**: string (uuid) | Unique Identifier of the last user who updated the Cost |
|**dateAdded**: string *(date-time)* | Date when the Vendor of Inventory Item was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added Inventory Item Vendor |
|**lastUpdated**: string *(date-time)* |Last Date when the Inventory Item Vendor was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the user who updated Inventory Item Vendor |
|**activeStatus**: boolean | Is the Status of the Inventory item Vendor active or not?|
|**ndcNumber**: string | National Drug Code number |
|**lockCost**: boolean | Is the Cost of the Inventory Item Vendor locked or not? |
|**costLastUpdatedByUserName**: <br> string | Name of the last user who updated the Cost |
|**addedByUserName**: string | Name of the user who added the Inventory Item Vendor |
|**lastUpdatedByUserName**: string | Name of the last user who updated Inventory Item Vendor |
|**pimKey**: string | Product Information Management Key |
|**altItemNo**: string | Alternative Item Number |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML<br>Request Example"
{
  "inventoryVendorId": "00000000-0000-0000-0000-000000000000",
  "inventoryId": "00000000-0000-0000-0000-000000000000",
  "inventoryNo": "string",
  "vendorId": "00000000-0000-0000-0000-000000000000",
  "vendorNo": "string",
  "vendorName": "string",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "facilityNo": "string",
  "facilityName": "string",
  "vendorItemNo": "string",
  "vendorUOM": "string",
  "vendorConversionFactor": "integer (int32)",
  "vendorCost": "number (double)",
  "vendorPriority": "integer (int32)",
  "contractNo": "string",
  "contractExpDate": "string (date-time)",
  "manufacturerItemNo": "string",
  "manufacturerId": "00000000-0000-0000-0000-000000000000",
  "manufacturerNo": "string",
  "manufacturerName": "string",
  "gtin": "string",
  "costLastUpdated": "string (date-time)",
  "costLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "dateAdded": "string (date-time)",
  "addedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "activeStatus": "boolean",
  "ndcNumber": "string",
  "lockCost": "boolean",
  "costLastUpdatedByUserName": "string",
  "addedByUserName": "string",
  "lastUpdatedByUserName": "string",
  "pimKey": "string",
  "altItemNo": "string"
}
```

### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**inventoryVendorId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory Vendor here. |
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

### <span style="color: #F05D30">Custom Errors</span>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**403 Forbidden** | User without the Update Locked Cost privilege sends the request with a valid ```vendorCost``` for Inventory Vendor that has Lock Cost.|

``` json title="Response Example"
vendorCost: You do not have sufficient privileges to perform this action.
```

| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**403 Forbidden** | User without the Update Locked Cost privilege sends the request for the ```lockCost``` field updating.|

``` json title="Response Example"
lockCost: You do not have sufficient privileges to perform this action.
```

| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**403 Forbidden** | User with cleared Managing Enterprise fields sends the request with a valid ```pimKey```.|

``` json title="Response Example"
pimKey: You do not have sufficient privileges to perform this action.
```

| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | User requested is not existing / from another Organization or restricted/inactive Facility.|

``` json title="Response Example"
Specified facilityId does not exist within organization.
```

| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | User requested is not existing/inactive or from another Organization Manufacturer.|

``` json title="Response Example"
Specified manufacturerNo does not exist within the organization.
```

| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | User updates Inventory Vendor to not unique values within Vendor, Vendor Item No, UOM, and Facility. |

``` json title="Response Example"
Inventory Vendor already exists within the specified Vendor Item No, Vendor UOM, and Facility.
```


| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Combination of ```vendorUOM``` and ```vendorConversionFactor``` is not matched with existing Inventory UOM (UOM and CF) |

``` json title="Response Example"
Specified vendorConversionFactor and vendorUOM do not exist for Inventory Vendor.
```

| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | ```vendorUOM``` is specified without ```vendorConversionFactor``` or VCF is specified without ```vendorUOM```.|

``` json title="Response Example"
vendorConversionFactor and vendorUOM should be specified simultaneously.
```

| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | User specifies Facility that belongs to another Inventory Group in the Request Body.|

``` json title="Response Example"
Inventory and specified Facility belong to different inventory groups.
```

| <div style="width:200px"> </div>|<div style="width:480px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | ```contractExpDate``` contains value that is less than 2009-01-26 date.|

``` json title="Response Example"
ContractExpDate must be greater than 2009-01-25.
```

## Get the list of inventory vendors changed from the specified date

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryVendors/GetAllFromDate(from={from},facilityId={facilityId},syncFlag={syncFlag})

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing inventory vendors changed from the specified date within a facility specified by ID.

The empty GUID ```00000000-0000-0000-0000-000000000000``` is taken into account for inventory vendor with the Master facility retrieving. After sending the GET request ```{{url}}/odata/InventoryVendors/GetAllFromDate(from={{from}},facilityId=00000000-0000-0000-0000-000000000000,syncFlag={{syncFlag}})```, the response contains the list of all active inventory vendors for the Master facility.

### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**from**: string *(date-time)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the Start Date here. |
|**facilityId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Facility here. |
|**syncFlag**: boolean <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Identifies if Location is synced with an external system. |
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


### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**inventoryVendorId**: string *(uuid)* | Unique Identifier of the Inventory Item Vendor |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**vendorCost**: number *(double)* | Item Cost of the Vendor |
|**vendorPriority**: integer *(int32)* | Priority of the Vendor |
|**contractNo**: string | Number of the Contract |
|**contractExpDate**: string <br> *(date-time)* | Expiration Date of the Contract |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**manufacturerId**: string *(uuid)* | Unique Identifier of the Manufacturer |
|**manufacturerNo**: string | Number of the Manufacturer |
|**manufacturerName**: string | Name of the Manufacturer |
|**gtin**: string | Global Trade Item Number |
|**costLastUpdated**: string <br> *(date-time)* | Last Date when the Cost was updated |
|**costLastUpdatedBy**: <br> string *(uuid)* | Unique Identifier of the last user who updated the Cost |
|**dateAdded**: string *(date-time)* | Date when the Vendor of Inventory Item was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added Inventory Item Vendor |
|**lastUpdated**: string *(date-time)* | Last Date when the Inventory Item Vendor was updated |
|**lastUpdatedBy**: string <br> *(uuid)* | Unique Identifier of the user who updated Inventory Item Vendor |
|**activeStatus**: boolean | Is the Status of the Inventory Item Vendor active or not? |
|**ndcNumber**: string | National Drug Code number |
|**lockCost**: boolean | Is the Cost of the Inventory Item Vendor locked or not? |
|**costLastUpdatedBy<br>UserName**: string | Name of the last user who updated the Cost |
|**addedByUserName**: string | Name of the user who added the Inventory Item Vendor |
|**lastUpdatedBy<br>UserName**: string | Name of the last user who updated Inventory Item Vendor |
|**pimKey**: string | Product Information Management Key |
|**altItemNo**: string | Alternative Item Number |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
[
  {
    "inventoryVendorId": "00000000-0000-0000-0000-000000000000",
    "inventoryId": "00000000-0000-0000-0000-000000000000",
    "inventoryNo": "string",
    "vendorId": "00000000-0000-0000-0000-000000000000",
    "vendorNo": "string",
    "vendorName": "string",
    "facilityId": "00000000-0000-0000-0000-000000000000",
    "facilityNo": "string",
    "facilityName": "string",
    "vendorItemNo": "string",
    "vendorUOM": "string",
    "vendorConversionFactor": "integer (int32)",
    "vendorCost": "number (double)",
    "vendorPriority": "integer (int32)",
    "contractNo": "string",
    "contractExpDate": "string (date-time)",
    "manufacturerItemNo": "string",
    "manufacturerId": "00000000-0000-0000-0000-000000000000",
    "manufacturerNo": "string",
    "manufacturerName": "string",
    "gtin": "string",
    "costLastUpdated": "string (date-time)",
    "costLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
    "dateAdded": "string (date-time)",
    "addedBy": "00000000-0000-0000-0000-000000000000",
    "lastUpdated": "string (date-time)",
    "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
    "activeStatus": "boolean",
    "ndcNumber": "string",
    "lockCost": "boolean",
    "costLastUpdatedByUserName": "string",
    "addedByUserName": "string",
    "lastUpdatedByUserName": "string",
    "pimKey": "string",
    "altItemNo": "string"
  }
]

```