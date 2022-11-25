# PurchaseOrderItems

## Get the list of purchase order items

### <span style="color: #F05D30">Path</span>
GET /odata/PurchaseOrderItems

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing purchase order items within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

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
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**400 Bad Request** | The limit for the ```$top``` query has been exceeded. The value from the incoming request is 'N' (N is your value from the request). You can find the data on the current limit [here](Options_and_Limitations.md#top-and-skip).
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**purchaseOrderItemId**: string *(uuid)* | Unique Identifier of the Purchase Order Item |
|**purchaseOrderNo**: string | Number of the Purchase Order Item |
|**sequenceNo**: integer *(int32)* | Number of the Sequence |
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**lineItemNo**: integer *(int32)* | Number of the Line Item |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**inventoryLocationId**: string *(uuid)* | Unique Identifier of the Inventory Location |
|**inventoryVendorId**: string *(uuid)* | Unique Identifier of the Inventory Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**vendorPriority**: integer *(int32)* | Priority of the Vendor |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**classificationId**: string *(uuid)* | Unique Identifier of the Inventory Category defined on the Organization level |
|**classificationName**: string | Name of the Category of the Inventory defined on the Organization level |
|**classification2Id**: string *(uuid)* | Second Unique Identifier of the Inventory Category defined on the Organization level |
|**classification2Name**: string | Name of the second Category of the Inventory defined on the Organization level |
|**inventoryDescription**: string | Description of the Inventory Item |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**manufacturerId**: string *(uuid)* | Unique Identifier of the Manufacturer |
|**manufacturerNo**: string | Number of the Manufacturer |
|**manufacturerName**: string | Name of the Manufacturer |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**orderQuantity**: integer *(int32)* | Quantity specified in the Order |
|**orderUOM**: string | Unit of Measure specified in the Order |
|**orderConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure specified in the Order |
|**stockUOM**: string | Unit of Measure to track Inventory Balance |
|**unitCost**: number *(double)* | Cost of the one unit of Purchase Order Item |
|**departmentGLCode**: string | General Ledger Code of the Department |
|**glCode**: string | General Ledger Code |
|**lineItemTypeId**: integer *(int32)* | Unique Identifier of the Line Item Type |
|**itemType**: string | Type of the Line Item |
|**lineItemNotes**: string | Comments about the Line Item |
|**contractNo**: string | Number of the Contract |
|**contractExpDate**: string *(date-time)* | Expiration Date of the Contract |
|**lastUpdated**: string *(date-time)* | Last Date when the Purchase Order Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Purchase Order Item |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Purchase Order Item |
|**dateCreated**: string *(date-time)* | Date when the Purchase Order Item was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Purchase Order Item |
|**createdByUserName**: string | Name of the user who created the Purchase Order Item |
|**isTaxable**: boolean | Is Purchase Order Item Taxable or not? |
|**returnPOItemId**: string *(uuid)* | Unique Identifier of the return Purchase Order Item |
|**internalNotes**: string | Internal Comments about the Purchase Order Item |
|**lotNo**: string | Identification Number assigned to a particular Quantity or Lot of material from a single Manufacturer |
|**serialNo**: string | Unique Identifier assigned incrementally or sequentially to an Item to uniquely identify it |
|**expirationDate**: string  <br> *(date-time)* | Previously determined date after which Item should no longer be used |
|**activeStatus**: boolean | Is Purchase Order Item active or not? |
|**activeStatusLastUpdated**: <br> string *(date-time)* | Last Date when the active Status of the Purchase Order Item was updated |
|**activeStatusLastUpdatedBy**: <br> string (uuid) | Unique Identifier of the last user who updated the active Status of the Purchase Order Item |
|**activeStatusLastUpdatedBy<br>UserName**: string | Name of the last user who updated the active Status of the Purchase Order Item |
|**supplierPartAuxiliaryID**: string | Unique Identifier of the Supplier Part Auxiliary |
|**submittedUnitCost**: number *(double)* | Cost of the one unit of Item that was submitted for the Purchase Order Item |
|**departmentId**: string *(uuid)* | Unique Identifier of the Department |
|**departmentNo**: string | Number of the Department |
|**departmentName**: string | Name of the Department |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "purchaseOrderItemId": "00000000-0000-0000-0000-000000000000",
      "purchaseOrderNo": "string",
      "sequenceNo": "integer (int32)",
      "purchaseOrderId": "00000000-0000-0000-0000-000000000000",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "facilityNo": "string",
      "facilityName": "string",
      "lineItemNo": "integer (int32)",
      "locationNo": "string",
      "locationName": "string",
      "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
      "inventoryVendorId": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "vendorPriority": "integer (int32)",
      "inventoryNo": "string",
      "classificationId": "00000000-0000-0000-0000-000000000000",
      "classificationName": "string",
      "classification2Id": "00000000-0000-0000-0000-000000000000",
      "classification2Name": "string",
      "inventoryDescription": "string",
      "vendorItemNo": "string",
      "manufacturerId": "00000000-0000-0000-0000-000000000000",
      "manufacturerNo": "string",
      "manufacturerName": "string",
      "manufacturerItemNo": "string",
      "orderQuantity": "integer (int32)",
      "orderUOM": "string",
      "orderConversionFactor": "integer (int32)",
      "stockUOM": "string",
      "unitCost": "number (double)",
      "departmentGLCode": "string",
      "glCode": "string",
      "lineItemTypeId": "integer (int32)",
      "itemType": "string",
      "lineItemNotes": "string",
      "contractNo": "string",
      "contractExpDate": "string (date-time)",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByUserName": "string",
      "dateCreated": "string (date-time)",
      "createdBy": "00000000-0000-0000-0000-000000000000",
      "createdByUserName": "string",
      "isTaxable": "boolean",
      "returnPOItemId": "00000000-0000-0000-0000-000000000000",
      "internalNotes": "string",
      "lotNo": "string",
      "serialNo": "string",
      "expirationDate": "string (date-time)",
      "activeStatus": "boolean",
      "activeStatusLastUpdated": "string (date-time)",
      "activeStatusLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "activeStatusLastUpdatedByUserName": "string",
      "supplierPartAuxiliaryID": "string",
      "submittedUnitCost": "number (double)",
      "departmentId": "00000000-0000-0000-0000-000000000000",
      "departmentNo": "string",
      "departmentName": "string"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```

## Get the specified purchase order item

### <span style="color: #F05D30">Path</span>
GET /odata/PurchaseOrderItems({purchaseOrderItemId})

### <span style="color: #F05D30">Description</span>
Returns the details of the purchase order item specified by ID.

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**purchaseOrderItemId**: string *(uuid)*  <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Purchase Order Item here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |


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
|<div style="width:200px">Property </div> |<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**purchaseOrderItemId**: string *(uuid)* | Unique Identifier of the Purchase Order Item |
|**purchaseOrderNo**: string | Number of the Purchase Order Item |
|**sequenceNo**: integer *(int32)* | Number of the Sequence |
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**lineItemNo**: integer *(int32)* | Number of the Line Item |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**inventoryLocationId**: string *(uuid)* | Unique Identifier of the Inventory Location |
|**inventoryVendorId**: string *(uuid)* | Unique Identifier of the Inventory Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**vendorPriority**: integer *(int32)* | Priority of the Vendor |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**classificationId**: string *(uuid)* | Unique Identifier of the Inventory Category defined on the Organization level |
|**classificationName**: string | Name of the Category of the Inventory defined on the Organization level |
|**classification2Id**: string *(uuid)* | Second Unique Identifier of the Inventory Category defined on the Organization level |
|**classification2Name**: string | Name of the second Category of the Inventory defined on the Organization level |
|**inventoryDescription**: string | Description of the Inventory Item |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**manufacturerId**: string *(uuid)* | Unique Identifier of the Manufacturer |
|**manufacturerNo**: string | Number of the Manufacturer |
|**manufacturerName**: string | Name of the Manufacturer |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**orderQuantity**: integer *(int32)* | Quantity specified in the Order |
|**orderUOM**: string | Unit of Measure specified in the Order |
|**orderConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure specified in the Order |
|**stockUOM**: string | Unit of Measure to track Inventory Balance |
|**unitCost**: number *(double)* | Cost of the one unit of Purchase Order Item |
|**departmentGLCode**: string | General Ledger Code of the Department |
|**glCode**: string | General Ledger Code |
|**lineItemTypeId**: integer *(int32)* | Unique Identifier of the Line Item Type |
|**itemType**: string | Type of the Line Item |
|**lineItemNotes**: string | Comments about the Line Item |
|**contractNo**: string | Number of the Contract |
|**contractExpDate**: string *(date-time)* | Expiration Date of the Contract |
|**lastUpdated**: string *(date-time)* | Last Date when the Purchase Order Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Purchase Order Item |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Purchase Order Item |
|**dateCreated**: string *(date-time)* | Date when the Purchase Order Item was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Purchase Order Item |
|**createdByUserName**: string | Name of the user who created the Purchase Order Item |
|**isTaxable**: boolean | Is Purchase Order Item Taxable or not? |
|**returnPOItemId**: string *(uuid)* | Unique Identifier of the return Purchase Order Item |
|**internalNotes**: string | Internal Comments about the Purchase Order Item |
|**lotNo**: string | Identification Number assigned to a particular Quantity or Lot of material from a single Manufacturer |
|**serialNo**: string | Unique Identifier assigned incrementally or sequentially to an Item to uniquely identify it |
|**expirationDate**: string  <br> *(date-time)* | Previously determined date after which Item should no longer be used |
|**activeStatus**: boolean | Is Purchase Order Item active or not? |
|**activeStatusLastUpdated**: <br> string *(date-time)* | Last Date when the active Status of the Purchase Order Item was updated |
|**activeStatusLastUpdatedBy**: <br> string (uuid) | Unique Identifier of the last user who updated the active Status of the Purchase Order Item |
|**activeStatusLastUpdatedBy<br>UserName**: string | Name of the last user who updated the active Status of the Purchase Order Item |
|**supplierPartAuxiliaryID**: string | Unique Identifier of the Supplier Part Auxiliary |
|**submittedUnitCost**: number *(double)* | Cost of the one unit of Item that was submitted for the Purchase Order Item |
|**departmentId**: string *(uuid)* | Unique Identifier of the Department |
|**departmentNo**: string | Number of the Department |
|**departmentName**: string | Name of the Department |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "purchaseOrderItemId": "00000000-0000-0000-0000-000000000000",
  "purchaseOrderNo": "string",
  "sequenceNo": "integer (int32)",
  "purchaseOrderId": "00000000-0000-0000-0000-000000000000",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "facilityNo": "string",
  "facilityName": "string",
  "lineItemNo": "integer (int32)",
  "locationNo": "string",
  "locationName": "string",
  "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
  "inventoryVendorId": "00000000-0000-0000-0000-000000000000",
  "vendorNo": "string",
  "vendorName": "string",
  "vendorPriority": "integer (int32)",
  "inventoryNo": "string",
  "classificationId": "00000000-0000-0000-0000-000000000000",
  "classificationName": "string",
  "classification2Id": "00000000-0000-0000-0000-000000000000",
  "classification2Name": "string",
  "inventoryDescription": "string",
  "vendorItemNo": "string",
  "manufacturerId": "00000000-0000-0000-0000-000000000000",
  "manufacturerNo": "string",
  "manufacturerName": "string",
  "manufacturerItemNo": "string",
  "orderQuantity": "integer (int32)",
  "orderUOM": "string",
  "orderConversionFactor": "integer (int32)",
  "stockUOM": "string",
  "unitCost": "number (double)",
  "departmentGLCode": "string",
  "glCode": "string",
  "lineItemTypeId": "integer (int32)",
  "itemType": "string",
  "lineItemNotes": "string",
  "contractNo": "string",
  "contractExpDate": "string (date-time)",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByUserName": "string",
  "dateCreated": "string (date-time)",
  "createdBy": "00000000-0000-0000-0000-000000000000",
  "createdByUserName": "string",
  "isTaxable": "boolean",
  "returnPOItemId": "00000000-0000-0000-0000-000000000000",
  "internalNotes": "string",
  "lotNo": "string",
  "serialNo": "string",
  "expirationDate": "string (date-time)",
  "activeStatus": "boolean",
  "activeStatusLastUpdated": "string (date-time)",
  "activeStatusLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "activeStatusLastUpdatedByUserName": "string",
  "supplierPartAuxiliaryID": "string",
  "submittedUnitCost": "number (double)",
  "departmentId": "00000000-0000-0000-0000-000000000000",
  "departmentNo": "string",
  "departmentName": "string"
}
```





