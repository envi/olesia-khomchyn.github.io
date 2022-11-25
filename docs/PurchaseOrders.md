# PurchaseOrders

## Get the list of purchase orders

### <span style="color: #F05D30">Path</span>
GET /odata/PurchaseOrders

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing purchase orders within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

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
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**purchaseOrderNo**: string | Number of the Purchase Order |
|**sequenceNo**: integer *(int32)* | Number of the Sequence |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**poTypeId**: integer *(int32)* | Unique Identifier of the Purchase Order Type |
|**poType**: string | Type of the Purchase Order |
|**buyerId**: string *(uuid)* | Unique Identifier of the Buyer |
|**buyerUserName**: string | Name of the Buyer |
|**expectedDeliveryDate**: string <br> *(date-time)* | Expected Delivery Date of the Purchase Order |
|**reference**: string | Information concerning the Transaction |
|**orderDate**: string *(date-time)* | Date when the Order was made |
|**sentBy**: string *(uuid)* | Unique Identifier of the user who sent the Purchase Order |
|**sentByUserName**: string | Name of the user who sent the Purchase Order |
|**returnTypeId**: integer *(int32)* | Unique Identifier of the Return Type |
|**returnType**: string | Type of the Return |
|**returnDate**: string *(date-time)* | Date of the Return |
|**returnedBy**: string *(uuid)* | Unique Identifier of the user who returned the Purchase Order |
|**returnedByUserName**: string | Name of the user who returned the Purchase Order |
|**poStatusId**: integer *(int32)* | Unique Identifier of Purchase Order Status |
|**poStatus**: string | Status of the Purchase Order |
|**invoiceStatusId**: integer *(int32)* | Unique Identifier of the Invoice Status |
|**invoiceStatus**: string | Status of the Invoice |
|**poSourceId**: integer *(int32)* | Unique Identifier of the Purchase Order Source |
|**poSource**: string | Source of the Purchase Order |
|**sendMethodId**: integer *(int32)* | Unique Identifier of the Sending Method |
|**sendMethod**: string | Method of Sending |
|**poConfirmationFlag**: boolean | Is the Purchase Order confirmed or not? |
|**poConfirmationDate**: string <br> *(date-time)* | Date when the Purchase Order was confirmed |
|**poConfirmationName**: string | Name of the Purchase Order Confirmation |
|**poConfirmationNumber**: string | Number of the Purchase Order Confirmation |
|**cerId**: string *(uuid)* | Unique Identifier of the Capital Expenditure Request |
|**cerNo**: string | Number of the Capital Expenditure Request |
|**cerNoDescription**: string | Description of the Capital Expenditure Request Number |
|**paymentTerms**: string | Purchase Order Payment Terms |
|**paymentMethod**: string | Purchase Order Payment Method |
|**billToAccountNo**: string | Number of the Account for sending the Invoice |
|**shipToAccountNo**: string | Number of the Account for sending the Item |
|**fob**: string | Free On Board (Destination or Ship Point) |
|**shipMethod**: string | Method of the Shipment |
|**shipVia**: string | Way of the Shipment |
|**shippingName**: string | Name of the Shipping |
|**shippingAddress1**: string | First Address for sending the product |
|**shippingAddress2**: string | Second Address for sending the product |
|**shippingCity**: string | City for sending the product |
|**shippingState**: string | State for sending the product |
|**shippingZip**: string | Zip for sending the product |
|**shippingContactName**: string | Name of the main contact point for sending the product |
|**shippingContactPhone**: string | Phone of the main contact point for sending the product |
|**shippingContactExt**: string | External phone of the main contact point for sending the product |
|**shippingContactEmail**: string | Email of the main contact point for sending the product |
|**shippingContactFax**: string | Fax of the main contact point for sending the product |
|**billingName**: string | Name of the Billing |
|**billingAddress1**: string | First Address for sending the Invoice |
|**billingAddress2**: string | Second Address for sending the Invoice |
|**billingCity**: string | City for sending the Invoice |
|**billingState**: string | State for sending the Invoice |
|**billingZip**: string | Zip for sending the Invoice |
|**billingContactName**: string | Name of the main contact point for sending the Invoice |
|**billingContactPhone**: string | Phone of the main contact point for sending the Invoice |
|**billingContactExt**: string | External phone of the main contact point for sending the Invoice |
|**billingContactEmail**: string | Email of the main contact point for sending the Invoice |
|**billingContactFax**: string | Fax of the main contact point for sending the Invoice |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**lastUpdated**: string *(date-time)* | Last Date when the Purchase Order was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Purchase Order |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Purchase Order |
|**dateCreated**: string *(date-time)* | Date when the Purchase Order was created |
|**discount**: number *(double)* | Discount for the Purchase Order |
|**discountTypeId**: integer *(int32)* | Unique Identifier of the Discount Type for the Purchase Order |
|**discountType**: string | Type of the discount for the Purchase Order |
|**salesTax**: number *(double)* | Tax for the Sales |
|**salesTaxId**: integer *(int32)* | Unique Identifier of the Tax for the Sales |
|**salesTaxType**: string | Type of the Tax for the Sales |
|**shipping**: number *(double)* | Number of the Shipping |
|**shippingTypeId**: integer *(int32)* | Unique Identifier of the Shipping Type |
|**shippingType**: string | Type of the Shipping |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "purchaseOrderId": "00000000-0000-0000-0000-000000000000",
      "purchaseOrderNo": "string",
      "sequenceNo": "integer (int32)",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "facilityNo": "string",
      "facilityName": "string",
      "locationId": "00000000-0000-0000-0000-000000000000",
      "locationNo": "string",
      "locationName": "string",
      "poTypeId": "integer (int32)",
      "poType": "string",
      "buyerId": "00000000-0000-0000-0000-000000000000",
      "buyerUserName": "string",
      "expectedDeliveryDate": "string (date-time)",
      "reference": "string",
      "orderDate": "string (date-time)",
      "sentBy": "00000000-0000-0000-0000-000000000000",
      "sentByUserName": "string",
      "returnTypeId": "integer (int32)",
      "returnType": "string",
      "returnDate": "string (date-time)",
      "returnedBy": "00000000-0000-0000-0000-000000000000",
      "returnedByUserName": "string",
      "poStatusId": "integer (int32)",
      "poStatus": "string",
      "invoiceStatusId": "integer (int32)",
      "invoiceStatus": "string",
      "poSourceId": "integer (int32)",
      "poSource": "string",
      "sendMethodId": "integer (int32)",
      "sendMethod": "string",
      "poConfirmationFlag": "boolean",
      "poConfirmationDate": "string (date-time)",
      "poConfirmationName": "string",
      "poConfirmationNumber": "string",
      "cerId": "00000000-0000-0000-0000-000000000000",
      "cerNo": "string",
      "cerNoDescription": "string",
      "paymentTerms": "string",
      "paymentMethod": "string",
      "billToAccountNo": "string",
      "shipToAccountNo": "string",
      "fob": "string",
      "shipMethod": "string",
      "shipVia": "string",
      "shippingName": "string",
      "shippingAddress1": "string",
      "shippingAddress2": "string",
      "shippingCity": "string",
      "shippingState": "string",
      "shippingZip": "string",
      "shippingContactName": "string",
      "shippingContactPhone": "string",
      "shippingContactExt": "string",
      "shippingContactEmail": "string",
      "shippingContactFax": "string",
      "billingName": "string",
      "billingAddress1": "string",
      "billingAddress2": "string",
      "billingCity": "string",
      "billingState": "string",
      "billingZip": "string",
      "billingContactName": "string",
      "billingContactPhone": "string",
      "billingContactExt": "string",
      "billingContactEmail": "string",
      "billingContactFax": "string",
      "vendorId": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByUserName": "string",
      "dateCreated": "string (date-time)",
      "discount": "number (double)",
      "discountTypeId": "integer (int32)",
      "discountType": "string",
      "salesTax": "number (double)",
      "salesTaxId": "integer (int32)",
      "salesTaxType": "string",
      "shipping": "number (double)",
      "shippingTypeId": "integer (int32)",
      "shippingType": "string"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```
## Get the specified purchase order

### <span style="color: #F05D30">Path</span>
GET /odata/PurchaseOrders({purchaseOrderId})

### <span style="color: #F05D30">Description</span>
Returns the details of the purchase order specified by ID.

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**purchaseOrderId**: string *(uuid)*  <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Purchase Order here. |
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
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**purchaseOrderNo**: string | Number of the Purchase Order |
|**sequenceNo**: integer *(int32)* | Number of the Sequence |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**poTypeId**: integer *(int32)* | Unique Identifier of the Purchase Order Type |
|**poType**: string | Type of the Purchase Order |
|**buyerId**: string *(uuid)* | Unique Identifier of the Buyer |
|**buyerUserName**: string | Name of the Buyer |
|**expectedDeliveryDate**: string <br> *(date-time)* | Expected Delivery Date of the Purchase Order |
|**reference**: string | Information concerning the Transaction |
|**orderDate**: string *(date-time)* | Date when the Order was made |
|**sentBy**: string *(uuid)* | Unique Identifier of the user who sent the Purchase Order |
|**sentByUserName**: string | Name of the user who sent the Purchase Order |
|**returnTypeId**: integer *(int32)* | Unique Identifier of the Return Type |
|**returnType**: string | Type of the Return |
|**returnDate**: string *(date-time)* | Date of the Return |
|**returnedBy**: string *(uuid)* | Unique Identifier of the user who returned the Purchase Order |
|**returnedByUserName**: string | Name of the user who returned the Purchase Order |
|**poStatusId**: integer *(int32)* | Unique Identifier of Purchase Order Status |
|**poStatus**: string | Status of the Purchase Order |
|**invoiceStatusId**: integer *(int32)* | Unique Identifier of the Invoice Status |
|**invoiceStatus**: string | Status of the Invoice |
|**poSourceId**: integer *(int32)* | Unique Identifier of the Purchase Order Source |
|**poSource**: string | Source of the Purchase Order |
|**sendMethodId**: integer *(int32)* | Unique Identifier of the Sending Method |
|**sendMethod**: string | Method of Sending |
|**poConfirmationFlag**: boolean | Is the Purchase Order confirmed or not? |
|**poConfirmationDate**: string <br> *(date-time)* | Date when the Purchase Order was confirmed |
|**poConfirmationName**: string | Name of the Purchase Order Confirmation |
|**poConfirmationNumber**: string | Number of the Purchase Order Confirmation |
|**cerId**: string *(uuid)* | Unique Identifier of the Capital Expenditure Request |
|**cerNo**: string | Number of the Capital Expenditure Request |
|**cerNoDescription**: string | Description of the Capital Expenditure Request Number |
|**paymentTerms**: string | Purchase Order Payment Terms |
|**paymentMethod**: string | Purchase Order Payment Method |
|**billToAccountNo**: string | Number of the Account for sending the Invoice |
|**shipToAccountNo**: string | Number of the Account for sending the Item |
|**fob**: string | Free On Board (Destination or Ship Point) |
|**shipMethod**: string | Method of the Shipment |
|**shipVia**: string | Way of the Shipment |
|**shippingName**: string | Name of the Shipping |
|**shippingAddress1**: string | First Address for sending the product |
|**shippingAddress2**: string | Second Address for sending the product |
|**shippingCity**: string | City for sending the product |
|**shippingState**: string | State for sending the product |
|**shippingZip**: string | Zip for sending the product |
|**shippingContactName**: string | Name of the main contact point for sending the product |
|**shippingContactPhone**: string | Phone of the main contact point for sending the product |
|**shippingContactExt**: string | External phone of the main contact point for sending the product |
|**shippingContactEmail**: string | Email of the main contact point for sending the product |
|**shippingContactFax**: string | Fax of the main contact point for sending the product |
|**billingName**: string | Name of the Billing |
|**billingAddress1**: string | First Address for sending the Invoice |
|**billingAddress2**: string | Second Address for sending the Invoice |
|**billingCity**: string | City for sending the Invoice |
|**billingState**: string | State for sending the Invoice |
|**billingZip**: string | Zip for sending the Invoice |
|**billingContactName**: string | Name of the main contact point for sending the Invoice |
|**billingContactPhone**: string | Phone of the main contact point for sending the Invoice |
|**billingContactExt**: string | External phone of the main contact point for sending the Invoice |
|**billingContactEmail**: string | Email of the main contact point for sending the Invoice |
|**billingContactFax**: string | Fax of the main contact point for sending the Invoice |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**lastUpdated**: string *(date-time)* | Last Date when the Purchase Order was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Purchase Order |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Purchase Order |
|**dateCreated**: string *(date-time)* | Date when the Purchase Order was created |
|**discount**: number *(double)* | Discount for the Purchase Order |
|**discountTypeId**: integer *(int32)* | Unique Identifier of the Discount Type for the Purchase Order |
|**discountType**: string | Type of the discount for the Purchase Order |
|**salesTax**: number *(double)* | Tax for the Sales |
|**salesTaxId**: integer *(int32)* | Unique Identifier of the Tax for the Sales |
|**salesTaxType**: string | Type of the Tax for the Sales |
|**shipping**: number *(double)* | Number of the Shipping |
|**shippingTypeId**: integer *(int32)* | Unique Identifier of the Shipping Type |
|**shippingType**: string | Type of the Shipping |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "purchaseOrderId": "00000000-0000-0000-0000-000000000000",
  "purchaseOrderNo": "string",
  "sequenceNo": "integer (int32)",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "facilityNo": "string",
  "facilityName": "string",
  "locationId": "00000000-0000-0000-0000-000000000000",
  "locationNo": "string",
  "locationName": "string",
  "poTypeId": "integer (int32)",
  "poType": "string",
  "buyerId": "00000000-0000-0000-0000-000000000000",
  "buyerUserName": "string",
  "expectedDeliveryDate": "string (date-time)",
  "reference": "string",
  "orderDate": "string (date-time)",
  "sentBy": "00000000-0000-0000-0000-000000000000",
  "sentByUserName": "string",
  "returnTypeId": "integer (int32)",
  "returnType": "string",
  "returnDate": "string (date-time)",
  "returnedBy": "00000000-0000-0000-0000-000000000000",
  "returnedByUserName": "string",
  "poStatusId": "integer (int32)",
  "poStatus": "string",
  "invoiceStatusId": "integer (int32)",
  "invoiceStatus": "string",
  "poSourceId": "integer (int32)",
  "poSource": "string",
  "sendMethodId": "integer (int32)",
  "sendMethod": "string",
  "poConfirmationFlag": "boolean",
  "poConfirmationDate": "string (date-time)",
  "poConfirmationName": "string",
  "poConfirmationNumber": "string",
  "cerId": "00000000-0000-0000-0000-000000000000",
  "cerNo": "string",
  "cerNoDescription": "string",
  "paymentTerms": "string",
  "paymentMethod": "string",
  "billToAccountNo": "string",
  "shipToAccountNo": "string",
  "fob": "string",
  "shipMethod": "string",
  "shipVia": "string",
  "shippingName": "string",
  "shippingAddress1": "string",
  "shippingAddress2": "string",
  "shippingCity": "string",
  "shippingState": "string",
  "shippingZip": "string",
  "shippingContactName": "string",
  "shippingContactPhone": "string",
  "shippingContactExt": "string",
  "shippingContactEmail": "string",
  "shippingContactFax": "string",
  "billingName": "string",
  "billingAddress1": "string",
  "billingAddress2": "string",
  "billingCity": "string",
  "billingState": "string",
  "billingZip": "string",
  "billingContactName": "string",
  "billingContactPhone": "string",
  "billingContactExt": "string",
  "billingContactEmail": "string",
  "billingContactFax": "string",
  "vendorId": "00000000-0000-0000-0000-000000000000",
  "vendorNo": "string",
  "vendorName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByUserName": "string",
  "dateCreated": "string (date-time)",
  "discount": "number (double)",
  "discountTypeId": "integer (int32)",
  "discountType": "string",
  "salesTax": "number (double)",
  "salesTaxId": "integer (int32)",
  "salesTaxType": "string",
  "shipping": "number (double)",
  "shippingTypeId": "integer (int32)",
  "shippingType": "string"
}
```

## Get the list of purchase order items for the specified purchase order

### <span style="color: #F05D30">Path</span>
GET /odata/PurchaseOrders({purchaseOrderId})/purchaseOrderItems

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing purchase order items within purchase order specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**purchaseOrderId**: string *(uuid)*  <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Purchase Order here. |
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
|**stockUOM**: | string Unit of Measure to track Inventory Balance |
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
|**dateCreated**: string *(date-time)* | Date when the Purchase Order Item was created 
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Purchase Order Item |
|**createdByUserName**: string | Name of the user who created the Purchase Order Item |
|**isTaxable**: boolean | Is Purchase Order Item Taxable or not? |
|**returnPOItemId**: string *(uuid)* | Unique Identifier of the return Purchase Order Item |
|**internalNotes**: string | Internal Comments about the Purchase Order Item |
|**lotNo**: string | Identification Number assigned to a particular Quantity or Lot of material from a single Manufacturer |
|**serialNo**: string | Unique Identifier assigned incrementally or sequentially to an Item to uniquely identify it |
|**expirationDate**: string <br> *(date-time)* | Previously determined date after which Item should no longer be used |
|**activeStatus**: boolean | Is Purchase Order Item active or not? |
|**activeStatusLastUpdated**: string <br> *(date-time)* | Last Date when the Active Status of the Purchase Order Item was updated |
|**activeStatusLastUpdatedBy**: <br> string *(uuid)* | Unique Identifier of the last user who updated the Active Status of the Purchase Order Item |
|**activeStatusLastUpdatedBy<br>UserName**: string | Name of the last user who updated the Active Status of the Purchase Order Item |
|**supplierPartAuxiliaryID**: string | Unique Identifier of the Supplier Part Auxiliary |
|**submittedUnitCost**: number *(double)* | Cost of the one unit of item that was submitted for the Purchase Order Item |
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