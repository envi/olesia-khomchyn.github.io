# Receipts

## Get the list of PO Receipts

### <span style="color: #F05D30">Path</span>
GET /odata/Receipts

### <span style="color: #F05D30">Description</span>
Returns the list of PO Receipts within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

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
|**receiptId**: string *(uuid)* | Unique Identifier of the Receipt | 
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**purchaseOrderNo**: string | Number of the Purchase Order |
|**sequenceNo**: integer *(int32)* | Number of the Sequence |
|**purchaseOrderReference**: string | Information concerning the Transaction in the Purchase Order |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor|
|**leadTime**: integer *(int32)* | Allowed time for the Completion |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**expectedDeliveryDate**: string <br> *(date-time)* | Expected date of the Item Delivery |
|**purchaseOrderStatusId**: <br> integer *(int32)* | Unique Identifier of the Purchase Order Status |
|**purchaseOrderStatus**: string | Status of the Purchase Order |
|**buyerId**: string *(uuid)* | Unique Identifier of the Buyer |
|**buyerName**: string | Name of the Buyer |
|**buyerUserName**: string | Name of the Buyer |
|**poConfirmationFlag**: boolean | Flag of the Purchase Order Confirmation |
|**poConfirmationDate**: string <br> *(date-time)* | Date when the Purchase Order was confirmed |
|**poConfirmationName**: string | Name of the Purchase Order Confirmation |
|**poConfirmationNumber**: string | Number of the Purchase Order Confirmation |
|**orderDate**: string *(date-time)* | Date when the Order was made |
|**orderBy**: string *(uuid)* | Unique Identifier of the user who made the Order |
|**orderByUserName**: string | Name of the user who made the Order |
|**orderByName**: string | Name of the user who made the Order |
|**packingSlipNumber**: string | Number of the Packing Slip |
|**dateAdded**: string *(date-time)* | Date when the Receipt was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Receipt |
|**addedByName**: string | Name of the user who added the Receipt |
|**addedByUserName**: string | Name of the user who added the Receipt |
|**dateSubmitted**: string *(date-time)* | Date when the Receipt was submitted |
|**receiptDate**: string *(date-time)* | Date specified in the Receipt |
|**receivedBy**: string *(uuid)* | Unique Identifier of the user who received the Receipt |
|**receivedByName**: string | Name of the user who received the Receipt |
|**receivedByUserName**: string | Name of the user who received the Receipt |
|**receiptStatusId**: integer *(int32)* | Unique Identifier of the Receipt Status |
|**receiptStatus**: string | Status of the Receipt |
|**lastUpdated**: string *(date-time)* | Last Date when the Receipt was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Receipt |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Receipt |
|**lastUpdatedByName**: string | Name of the last user who updated the Receipt |
|**receiptFillStatus**: boolean | Status of the Receipt Fill |
|**receiptSourceId**: integer *(int32)* | Unique Identifier of the Receipt Source |
|**receiptSource**: integer *(int32)* | Source of the Receipt |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "receiptId": "00000000-0000-0000-0000-000000000000",
      "purchaseOrderId": "00000000-0000-0000-0000-000000000000",
      "purchaseOrderNo": "string",
      "sequenceNo": "integer (int32)",
      "purchaseOrderReference": "string",
      "vendorId": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "leadTime": "integer (int32)",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "facilityNo": "string",
      "facilityName": "string",
      "locationId": "00000000-0000-0000-0000-000000000000",
      "locationNo": "string",
      "locationName": "string",
      "expectedDeliveryDate": "string (date-time)",
      "purchaseOrderStatusId": "integer (int32)",
      "purchaseOrderStatus": "string",
      "buyerId": "00000000-0000-0000-0000-000000000000",
      "buyerName": "string",
      "buyerUserName": "string",
      "poConfirmationFlag": "boolean",
      "poConfirmationDate": "string (date-time)",
      "poConfirmationName": "string",
      "poConfirmationNumber": "string",
      "orderDate": "string (date-time)",
      "orderBy": "00000000-0000-0000-0000-000000000000",
      "orderByUserName": "string",
      "orderByName": "string",
      "packingSlipNumber": "string",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "addedByName": "string",
      "addedByUserName": "string",
      "dateSubmitted": "string (date-time)",
      "receiptDate": "string (date-time)",
      "receivedBy": "00000000-0000-0000-0000-000000000000",
      "receivedByName": "string",
      "receivedByUserName": "string",
      "receiptStatusId": "integer (int32)",
      "receiptStatus": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByUserName": "string",
      "lastUpdatedByName": "string",
      "receiptFillStatus": "boolean",
      "receiptSourceId": "integer (int32)",
      "receiptSource": "integer (int32)"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```

## Get the specified PO Receipt

### <span style="color: #F05D30">Path</span>
GET /odata/Receipts({receiptId})

### <span style="color: #F05D30">Description</span>
Returns the details of the Receipt specified by ID.

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**receiptId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Receipt here. |
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
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**receiptId**: string *(uuid)* | Unique Identifier of the Receipt | 
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**purchaseOrderNo**: string | Number of the Purchase Order |
|**sequenceNo**: integer *(int32)* | Number of the Sequence |
|**purchaseOrderReference**: string | Information concerning the Transaction in the Purchase Order |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor|
|**leadTime**: integer *(int32)* | Allowed time for the Completion |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**expectedDeliveryDate**: string <br> *(date-time)* | Expected date of the Item Delivery |
|**purchaseOrderStatusId**: <br> integer *(int32)* | Unique Identifier of the Purchase Order Status |
|**purchaseOrderStatus**: string | Status of the Purchase Order |
|**buyerId**: string *(uuid)* | Unique Identifier of the Buyer |
|**buyerName**: string | Name of the Buyer |
|**buyerUserName**: string | Name of the Buyer |
|**poConfirmationFlag**: boolean | Flag of the Purchase Order Confirmation |
|**poConfirmationDate**: string <br> *(date-time)* | Date when the Purchase Order was confirmed |
|**poConfirmationName**: string | Name of the Purchase Order Confirmation |
|**poConfirmationNumber**: string | Number of the Purchase Order Confirmation |
|**orderDate**: string *(date-time)* | Date when the Order was made |
|**orderBy**: string *(uuid)* | Unique Identifier of the user who made the Order |
|**orderByUserName**: string | Name of the user who made the Order |
|**orderByName**: string | Name of the user who made the Order |
|**packingSlipNumber**: string | Number of the Packing Slip |
|**dateAdded**: string *(date-time)* | Date when the Receipt was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Receipt |
|**addedByName**: string | Name of the user who added the Receipt |
|**addedByUserName**: string | Name of the user who added the Receipt |
|**dateSubmitted**: string *(date-time)* | Date when the Receipt was submitted |
|**receiptDate**: string *(date-time)* | Date specified in the Receipt |
|**receivedBy**: string *(uuid)* | Unique Identifier of the user who received the Receipt |
|**receivedByName**: string | Name of the user who received the Receipt |
|**receivedByUserName**: string | Name of the user who received the Receipt |
|**receiptStatusId**: integer *(int32)* | Unique Identifier of the Receipt Status |
|**receiptStatus**: string | Status of the Receipt |
|**lastUpdated**: string *(date-time)* | Last Date when the Receipt was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Receipt |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Receipt |
|**lastUpdatedByName**: string | Name of the last user who updated the Receipt |
|**receiptFillStatus**: boolean | Status of the Receipt Fill |
|**receiptSourceId**: integer *(int32)* | Unique Identifier of the Receipt Source |
|**receiptSource**: integer *(int32)* | Source of the Receipt |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "receiptId": "00000000-0000-0000-0000-000000000000",
  "purchaseOrderId": "00000000-0000-0000-0000-000000000000",
  "purchaseOrderNo": "string",
  "sequenceNo": "integer (int32)",
  "purchaseOrderReference": "string",
  "vendorId": "00000000-0000-0000-0000-000000000000",
  "vendorNo": "string",
  "vendorName": "string",
  "leadTime": "integer (int32)",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "facilityNo": "string",
  "facilityName": "string",
  "locationId": "00000000-0000-0000-0000-000000000000",
  "locationNo": "string",
  "locationName": "string",
  "expectedDeliveryDate": "string (date-time)",
  "purchaseOrderStatusId": "integer (int32)",
  "purchaseOrderStatus": "string",
  "buyerId": "00000000-0000-0000-0000-000000000000",
  "buyerName": "string",
  "buyerUserName": "string",
  "poConfirmationFlag": "boolean",
  "poConfirmationDate": "string (date-time)",
  "poConfirmationName": "string",
  "poConfirmationNumber": "string",
  "orderDate": "string (date-time)",
  "orderBy": "00000000-0000-0000-0000-000000000000",
  "orderByUserName": "string",
  "orderByName": "string",
  "packingSlipNumber": "string",
  "dateAdded": "string (date-time)",
  "addedBy": "00000000-0000-0000-0000-000000000000",
  "addedByName": "string",
  "addedByUserName": "string",
  "dateSubmitted": "string (date-time)",
  "receiptDate": "string (date-time)",
  "receivedBy": "00000000-0000-0000-0000-000000000000",
  "receivedByName": "string",
  "receivedByUserName": "string",
  "receiptStatusId": "integer (int32)",
  "receiptStatus": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByUserName": "string",
  "lastUpdatedByName": "string",
  "receiptFillStatus": "boolean",
  "receiptSourceId": "integer (int32)",
  "receiptSource": "integer (int32)"
}
```

## Get the list of Receipt Items for the specified PO Receipt

### <span style="color: #F05D30">Path</span>
GET /odata/Receipts({receiptId})/receiptItems

### <span style="color: #F05D30">Description</span>
Returns the paged list of existing Receipt Items within the Receipt specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**receiptId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Receipt here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.| 
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition. | 
|**$orderby**: string <br> *in query* | Sorts the results | 
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

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
|**classification**: string | Category of the item defined on the Organization level |
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
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Receipt Item |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Receipt Item |

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





