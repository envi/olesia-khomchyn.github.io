# ReceiptItems

## Get the list of PO receipt items

### <span style="color: #F05D30">Path</span>
GET /odata/ReceiptItems

### <span style="color: #F05D30">Description</span>
Returns the list of PO receipt items within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

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
|**400 Bad Request** | The limit for the ```$top``` query has been exceeded. The value from the incoming request is 'N' (N is your value from the request). You can find the data on the current limit [here](Options_and_Limitations.md#top-and-skip).
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**receiptId**: string *(uuid)* | Unique Identifier of the Receipt |
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**purchaseOrderItemId**: string *(uuid)* | Unique Identifier of the Purchase Order Item |
|**purchaseOrderNo**: string | Number of the Purchase Order |
|**sequenceNo**: integer *(int32)* | Number of the Sequence |
|**receiptItemId**: string *(uuid)* | Unique Identifier of the Receipt Item |
|**lineItemNo**: integer *(int32)* | Number of the Line Items |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**inventoryDescription**: string | Description of the Inventory Item |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**manufacturerId**: string *(uuid)* | Unique Identifier of the Manufacturer |
|**manufacturerNo**: string | Number of the Manufacturer |
|**manufacturerName**: string | Name of the Manufacturer |
|**manufacturerItemNo**: string | Number of the Manufacturer Item |
|**lotNo**: string | Identification Number assigned to a particular Quantity or Lot of material from a single Manufacturer |
|**serialNo**: string | Unique Identifier assigned incrementally or sequentially to an Item to uniquely identify it |
|**expirationDate**: string *(date-time)* | Previously determined date after which Item should no longer be used |
|**purchaseOrderItemNotes**: string | Comments about the Purchase Order Item |
|**departmentGLCode**: string | General Ledger Code of the Department |
|**glCode**: string | General Ledger Code |
|**classification**: string | Category of the Item defined on the Organization level |
|**classification2**: string | Additional Category of the Item defined on the Organization level |
|**cost**: number *(double)* | Cost for the Receipt Item |
|**orderedQuantity**: integer *(int32)* | Quantity of the Ordered Receipt Items |
|**orderedUOM**: string | Unit of Measure of the Ordered Receipt Items |
|**orderedConversionFactor**: <br> integer *(int32)* | Number of ordered Stock Keeping Units in another Unit of Measure |
|**receivedQuantity**: integer *(int32)* | Quantity of the Received Receipt Items |
|**receivedUOM**: string | Unit of Measure of the Received Receipt Items |
|**receivedConversionFactor**: <br> integer *(int32)* | Number of received Stock Keeping Units in another Unit of Measure |
|**dateAdded**: string *(date-time)* | Date when the Receipt Item was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Receipt Item |
|**addedByUserName**: string | Name of the user who added the Receipt Item |
|**lastUpdated**: string *(date-time)* | Last Date when the Receipt Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the user who updated the Receipt Item |
|**lastUpdatedByUserName**: string | Name of the user who updated the Receipt Item |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"

{
  "items": [
    {
      "receiptId": "00000000-0000-0000-0000-000000000000",
      "purchaseOrderId": "00000000-0000-0000-0000-000000000000",
      "purchaseOrderItemId": "00000000-0000-0000-0000-000000000000",
      "purchaseOrderNo": "string",
      "sequenceNo": "integer (int32)",
      "receiptItemId": "00000000-0000-0000-0000-000000000000",
      "lineItemNo": "integer (int32)",
      "inventoryNo": "string",
      "inventoryDescription": "string",
      "vendorItemNo": "string",
      "manufacturerId": "00000000-0000-0000-0000-000000000000",
      "manufacturerNo": "string",
      "manufacturerName": "string",
      "manufacturerItemNo": "string",
      "lotNo": "string",
      "serialNo": "string",
      "expirationDate": "string (date-time)",
      "purchaseOrderItemNotes": "string",
      "departmentGLCode": "string",
      "glCode": "string",
      "classification": "string",
      "classification2": "string",
      "cost": "number (double)",
      "orderedQuantity": "integer (int32)",
      "orderedUOM": "string",
      "orderedConversionFactor": "integer (int32)",
      "receivedQuantity": "integer (int32)",
      "receivedUOM": "string",
      "receivedConversionFactor": "integer (int32)",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "addedByUserName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByUserName": "string"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```

## Get the specified receipt item

### <span style="color: #F05D30">Path</span>
GET /odata/ReceiptItems({receiptItemId})

### <span style="color: #F05D30">Description</span>
Returns the details of the receipt item specified by ID.

### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**receiptItemId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Receipt Item here. |
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
|**receiptId**: string *(uuid)* | Unique Identifier of the Receipt |
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**purchaseOrderItemId**: string *(uuid)* | Unique Identifier of the Purchase Order Item |
|**purchaseOrderNo**: string | Number of the Purchase Order |
|**sequenceNo**: integer *(int32)* | Number of the Sequence |
|**receiptItemId**: string *(uuid)* | Unique Identifier of the Receipt Item |
|**lineItemNo**: integer *(int32)* | Number of the Line Items |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**inventoryDescription**: string | Description of the Inventory Item |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**manufacturerId**: string *(uuid)* | Unique Identifier of the Manufacturer |
|**manufacturerNo**: string | Number of the Manufacturer |
|**manufacturerName**: string | Name of the Manufacturer |
|**manufacturerItemNo**: string | Number of the Manufacturer Item |
|**lotNo**: string | Identification Number assigned to a particular Quantity or Lot of material from a single Manufacturer |
|**serialNo**: string | Unique Identifier assigned incrementally or sequentially to an Item to uniquely identify it |
|**expirationDate**: string *(date-time)* | Previously determined date after which Item should no longer be used |
|**purchaseOrderItemNotes**: string | Comments about the Purchase Order Item |
|**departmentGLCode**: string | General Ledger Code of the Department |
|**glCode**: string | General Ledger Code |
|**classification**: string | Category of the Item defined on the Organization level |
|**classification2**: string | Additional Category of the Item defined on the Organization level |
|**cost**: number *(double)* | Cost for the Receipt Item |
|**orderedQuantity**: integer *(int32)* | Quantity of the Ordered Receipt Items |
|**orderedUOM**: string | Unit of Measure of the Ordered Receipt Items |
|**orderedConversionFactor**: <br> integer *(int32)* | Number of ordered Stock Keeping Units in another Unit of Measure |
|**receivedQuantity**: integer *(int32)* | Quantity of the Received Receipt Items |
|**receivedUOM**: string | Unit of Measure of the Received Receipt Items |
|**receivedConversionFactor**: <br> integer *(int32)* | Number of received Stock Keeping Units in another Unit of Measure |
|**dateAdded**: string *(date-time)* | Date when the Receipt Item was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Receipt Item |
|**addedByUserName**: string | Name of the user who added the Receipt Item |
|**lastUpdated**: string *(date-time)* | Last Date when the Receipt Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the user who updated the Receipt Item |
|**lastUpdatedByUserName**: string | Name of the user who updated the Receipt Item |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "receiptId": "00000000-0000-0000-0000-000000000000",
  "purchaseOrderId": "00000000-0000-0000-0000-000000000000",
  "purchaseOrderItemId": "00000000-0000-0000-0000-000000000000",
  "purchaseOrderNo": "string",
  "sequenceNo": "integer (int32)",
  "receiptItemId": "00000000-0000-0000-0000-000000000000",
  "lineItemNo": "integer (int32)",
  "inventoryNo": "string",
  "inventoryDescription": "string",
  "vendorItemNo": "string",
  "manufacturerId": "00000000-0000-0000-0000-000000000000",
  "manufacturerNo": "string",
  "manufacturerName": "string",
  "manufacturerItemNo": "string",
  "lotNo": "string",
  "serialNo": "string",
  "expirationDate": "string (date-time)",
  "purchaseOrderItemNotes": "string",
  "departmentGLCode": "string",
  "glCode": "string",
  "classification": "string",
  "classification2": "string",
  "cost": "number (double)",
  "orderedQuantity": "integer (int32)",
  "orderedUOM": "string",
  "orderedConversionFactor": "integer (int32)",
  "receivedQuantity": "integer (int32)",
  "receivedUOM": "string",
  "receivedConversionFactor": "integer (int32)",
  "dateAdded": "string (date-time)",
  "addedBy": "00000000-0000-0000-0000-000000000000",
  "addedByUserName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByUserName": "string"
}
```
