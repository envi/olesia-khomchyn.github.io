# InventoryLocations

## Get the list of Inventory Locations

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryLocations

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing Inventory Locations within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

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
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition.|  
|**$orderby**: string <br> *in query* | Sorts the results.|
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in. |
|**400 Bad Request** | The limit for the ```$top``` query has been exceeded. The value from the incoming request is 'N' (N is your value from the request). You can find the data on the current limit [here](Options_and_Limitations.md#top-and-skip). |
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryLocationId**: string *(uuid)* | Unique Identifier of the Inventory Item Location |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityName**: string | Name of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationName**: string | Name of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationUOM**: string | Unit of Measure of the Location |
|**locationConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Location's Unit of Measure |
|**inventoryStockUOM**: string | Unit of Measure to track Inventory Balance |
|**defaultIssueUOM**: string | Unit Of Measure used when issuing the Inventory Item to a Department or Patient |
|**defaultIssueConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure when issuing the Inventory Item to a Department or Patient |
|**defaultCountUOM**: string | Unit Of Measure used when counting the Inventory Item to a Department or Patient |
|**defaultCountConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure when counting the Inventory Item |
|**cost**: number *(double)* | Cost for the Location |
|**isBillable**: boolean | Is Location Billable or not? |
|**isTaxable**: boolean | Is Location Taxable or not? |
|**itemType**: integer *(int8)* | Type of the Item |
|**itemTypeText**: string | Value of the Item Type |
|**priceMarkup**: number *(double)* | The dollar or percent amount added to the Inventory Location Cost amount |
|**priceMarkupType**: integer *(int8)*  | Type of the Price Markup (% or $) |
|**priceMarkupTypeText**: string | Dollar or Percent |
|**disablePurchasing**: boolean | Disable or not Purchasing for the Location |
|**minQuantity**: integer *(int32)* | Minimal Inventory Items Quantity for this Location |
|**onRequisition**: integer *(int32)* | Quantity of Inventory Items for Requisition |
|**maxQuantity**: integer *(int32)* | Maximal Inventory Items Quantity for this Location |
|**safetyStock**: integer *(int32)* | Level of extra Stock that is maintained to mitigate the risk of stockouts |
|**binShelf**: string | Level of storage within the Location |
|**assetLedgerNo**: string | General Ledger Account Code for the Inventory Asset at the Location |
|**expenseLedgerNo**: string | General Ledger Account Code for the Inventory Expense at the Location |
|**syncFlag**: boolean | Is Inventory Location marked with Synchronization Flag or not? |
|**costLastUpdated**: string <br> *(date-time)*  | Last Date when the Cost was updated |
|**costLastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Cost |
|**dateAdded**: string *(date-time)* | Date when the Inventory Location was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the last user who added Location |
|**lastUpdated**: string *(date-time)* | Date of last Location update |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated Location |
|**activeStatus**: boolean | Is Location active or not? |
|**locationSynchronizationDate**: string <br> *(date-time)* | Date when the Location was synchronized |
|**costSynchronizationDate**: string *(date-time)* | Date when the Cost was synchronized |
|**defaultPurchaseUOM**: string | Default Unit of Measure for Purchasing |
|**valuationMethod**: integer <br> *(int32)* | Method of Valuation |
|**valuationMethodText**: string | Value of the Valuation Method |
|**pendingOrders**: integer <br> *(int32)* | Quantity of the Item in EA from all orders in the Pending status |
|**submittedOrders**: integer <br> *(int32)* | Quantity of the Item that are sent but not received yet |
|**quantityOnHand**: integer *(int32)*  | The total number of stock-keeping Inventory Items that are physically located in the Location |
|**lastUpdatedByName**: string | Name of the last user who updated the Inventory Location |
|**addedByName**: string | Name of the user who added the Inventory Location |
|**costLastUpdatedByName**: string | Name of the last user who updated the Cost |
|**crossReferenceNo**: string | Number of the Cross Reference |
|**inventoryActiveStatus**: boolean | Is Inventory Item active or not? |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
      "inventoryId": "00000000-0000-0000-0000-000000000000",
      "inventoryNo": "string",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "facilityName": "string",
      "facilityNo": "string",
      "locationId": "00000000-0000-0000-0000-000000000000",
      "locationName": "string",
      "locationNo": "string",
      "locationUOM": "string",
      "locationConversionFactor": "integer (int32)",
      "inventoryStockUOM": "string",
      "defaultIssueUOM": "string",
      "defaultIssueConversionFactor": "integer (int32)",
      "defaultCountUOM": "string",
      "defaultCountConversionFactor": "integer (int32)",
      "cost": "number (double)",
      "isBillable": "boolean",
      "isTaxable": "boolean",
      "itemType": "integer (int8)",
      "itemTypeText": "string",
      "priceMarkup": "number (double)",
      "priceMarkupType": "integer (int8)",
      "priceMarkupTypeText": "string",
      "disablePurchasing": "boolean",
      "minQuantity": "integer (int32)",
      "onRequisition": "integer (int32)",
      "maxQuantity": "integer (int32)",
      "safetyStock": "integer (int32)",
      "binShelf": "string",
      "assetLedgerNo": "string",
      "expenseLedgerNo": "string",
      "syncFlag": "boolean",
      "costLastUpdated": "string (date-time)",
      "costLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "activeStatus": "boolean",
      "locationSynchronizationDate": "string (date-time)",
      "costSynchronizationDate": "string (date-time)",
      "defaultPurchaseUOM": "string",
      "valuationMethod": "integer (int32)",
      "valuationMethodText": "string",
      "pendingOrders": "integer (int32)",
      "submittedOrders": "integer (int32)",
      "quantityOnHand": "integer (int32)",
      "lastUpdatedByName": "string",
      "addedByName": "string",
      "costLastUpdatedByName": "string",
      "crossReferenceNo": "string",
      "inventoryActiveStatus": "boolean"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
    
```


## Get the specified Inventory Location

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryLocations({inventoryLocationId})

### <span style="color: #F05D30">Description</span>
Returns the details of the Inventory Location specified by ID.

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**inventoryLocationId**: string *(uuid)* <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory Location here. |
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
|<div style="width:200px">Property </div> |<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryLocationId**: string *(uuid)* | Unique Identifier of the Inventory Item Location |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityName**: string | Name of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationName**: string | Name of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationUOM**: string | Unit of Measure of the Location |
|**locationConversionFactor**: integer *(int32)* | Number of Stock Keeping Units in another Location's Unit of Measure |
|**inventoryStockUOM**: string | Unit of Measure to track Inventory Balance |
|**defaultIssueUOM**: string | Unit Of Measure used when issuing the Inventory Item to a Department or Patient |
|**defaultIssueConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure when issuing the Inventory Item to a Department or Patient |
|**defaultCountUOM**: string | Unit Of Measure used when counting the Inventory Item to a Department or Patient |
|**defaultCountConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure when counting the Inventory Item |
|**cost**: number *(double)* | Cost for the Location |
|**isBillable**: boolean | Is Location Billable or not? |
|**isTaxable**: boolean | Is Location Taxable or not? |
|**itemType**: integer *(int8)* | Type of the Item |
|**itemTypeText**: string | Value of the Item Type |
|**priceMarkup**: number *(double)* | The dollar or percent amount added to the Inventory Location Cost amount |
|**priceMarkupType**: integer *(int8)*  | Type of the Price Markup (% or $) |
|**priceMarkupTypeText**: string | Dollar or Percent |
|**disablePurchasing**: boolean | Disable or not Purchasing for the Location |
|**minQuantity**: integer *(int32)* | Minimal Inventory Items Quantity for this Location |
|**onRequisition**: integer *(int32)* | Quantity of Inventory Items for Requisition |
|**maxQuantity**: integer *(int32)* | Maximal Inventory Items Quantity for this Location |
|**safetyStock**: integer *(int32)* | Level of extra Stock that is maintained to mitigate the risk of stockouts |
|**binShelf**: string | Level of storage within the Location |
|**assetLedgerNo**: string | General Ledger Account Code for the Inventory Asset at the Location |
|**expenseLedgerNo**: string | General Ledger Account Code for the Inventory Expense at the Location |
|**syncFlag**: boolean | Is Inventory Location marked with Synchronization Flag or not? |
|**costLastUpdated**: string <br> *(date-time)*  | Last Date when the Cost was updated |
|**costLastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Cost |
|**dateAdded**: string *(date-time)* | Date when the Inventory Location was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the last user who added Location |
|**lastUpdated**: string *(date-time)* | Date of last Location update |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated Location |
|**activeStatus**: boolean | Is Location active or not? |
|**locationSynchronizationDate**: string <br> *(date-time)* | Date when the Location was synchronized |
|**costSynchronizationDate**: string *(date-time)* | Date when the Cost was synchronized |
|**defaultPurchaseUOM**: string | Default Unit of Measure for Purchasing |
|**valuationMethod**: integer <br> *(int32)* | Method of Valuation |
|**valuationMethodText**: string | Value of the Valuation Method |
|**pendingOrders**: integer <br> *(int32)* | Quantity of the Item in EA from all orders in the Pending status |
|**submittedOrders**: integer <br> *(int32)* | Quantity of the Item that are sent but not received yet |
|**quantityOnHand**: integer *(int32)*  | The total number of stock-keeping Inventory Items that are physically located in the Location |
|**lastUpdatedByName**: string | Name of the last user who updated the Inventory Location |
|**addedByName**: string | Name of the user who added the Inventory Location |
|**costLastUpdatedByName**: string | Name of the last user who updated the Cost |
|**crossReferenceNo**: string | Number of the Cross Reference |
|**inventoryActiveStatus**: boolean | Is Inventory Item active or not? |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
  "inventoryId": "00000000-0000-0000-0000-000000000000",
  "inventoryNo": "string",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "facilityName": "string",
  "facilityNo": "string",
  "locationId": "00000000-0000-0000-0000-000000000000",
  "locationName": "string",
  "locationNo": "string",
  "locationUOM": "string",
  "locationConversionFactor": "integer (int32)",
  "inventoryStockUOM": "string",
  "defaultIssueUOM": "string",
  "defaultIssueConversionFactor": "integer (int32)",
  "defaultCountUOM": "string",
  "defaultCountConversionFactor": "integer (int32)",
  "cost": "number (double)",
  "isBillable": "boolean",
  "isTaxable": "boolean",
  "itemType": "integer (int8)",
  "itemTypeText": "string",
  "priceMarkup": "number (double)",
  "priceMarkupType": "integer (int8)",
  "priceMarkupTypeText": "string",
  "disablePurchasing": "boolean",
  "minQuantity": "integer (int32)",
  "onRequisition": "integer (int32)",
  "maxQuantity": "integer (int32)",
  "safetyStock": "integer (int32)",
  "binShelf": "string",
  "assetLedgerNo": "string",
  "expenseLedgerNo": "string",
  "syncFlag": "boolean",
  "costLastUpdated": "string (date-time)",
  "costLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "dateAdded": "string (date-time)",
  "addedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "activeStatus": "boolean",
  "locationSynchronizationDate": "string (date-time)",
  "costSynchronizationDate": "string (date-time)",
  "defaultPurchaseUOM": "string",
  "valuationMethod": "integer (int32)",
  "valuationMethodText": "string",
  "pendingOrders": "integer (int32)",
  "submittedOrders": "integer (int32)",
  "quantityOnHand": "integer (int32)",
  "lastUpdatedByName": "string",
  "addedByName": "string",
  "costLastUpdatedByName": "string",
  "crossReferenceNo": "string",
  "inventoryActiveStatus": "boolean"
}  
```

## Partially update the specified Inventory Location

### <span style="color: #F05D30">Path</span>
PATCH /odata/InventoryLocations({inventoryLocationId})

### <span style="color: #F05D30">Description</span>
Partially updates the details of the Inventory Location specified by the Inventory Location ID.

### <span style="color: #F05D30">Request body</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**locationUOM**: string | Unit of Measure of the Location |
|**locationConversionFactor**: integer *(int32)* | Number of Stock Keeping Units in another Location's Unit of Measure |
|**defaultIssueUOM**: string | Unit Of Measure used when issuing the Inventory Item to a Department or Patient |
|**defaultIssueConversionFactor**: integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure when issuing the Inventory Item to a Department or Patient |
|**defaultCountUOM**: string | Unit Of Measure used when counting the Inventory Item to a Department or Patient |
|**defaultCountConversionFactor**: integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure when counting the Inventory Item |
|**cost**: number *(double)* | Cost for the Location |
|**isBillable**: boolean | Is Location Billable or not? |
|**isTaxable**: boolean | Is Location Taxable or not? |
|**itemType**: integer *(int8)* | Type of the Item |
|**priceMarkup**: number *(double)* | The dollar or percent amount added to the Inventory Location Cost amount |
|**priceMarkupType**: integer *(int8)*  | Type of the Price Markup (% or $) |
|**disablePurchasing**: boolean | Disable or not Purchasing for the Location |
|**minQuantity**: integer *(int32)* | Minimal Inventory Items Quantity for this Location |
|**maxQuantity**: integer *(int32)* | Maximal Inventory Items Quantity for this Location |
|**safetyStock**: integer *(int32)* | Level of extra Stock that is maintained to mitigate the risk of stockouts |
|**binShelf**: string | Level of storage within the Location |
|**assetLedgerNo**: string | General Ledger Account Code for the Inventory Asset at the Location |
|**expenseLedgerNo**: string | General Ledger Account Code for the Inventory Expense at the Location |
|**syncFlag**: boolean | Is Inventory Location marked with Synchronization Flag or not? |
|**activeStatus**: boolean | Is Location active or not ? |
|**crossReferenceNo**: string | Number of the Cross Reference |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML<br>Request Example"
{
  "locationUOM": "string",
  "locationConversionFactor": "integer (int32)",
  "defaultIssueUOM": "string",
  "defaultIssueConversionFactor": "integer (int32)",
  "defaultCountUOM": "string",
  "defaultCountConversionFactor": "integer (int32)",
  "cost": "number (double)",
  "isBillable": "boolean",
  "isTaxable": "boolean",
  "itemType": "integer (int8)",
  "priceMarkup": "number (double)",
  "priceMarkupType": "integer (int8)",
  "disablePurchasing": "boolean",
  "minQuantity": "integer (int32)",
  "maxQuantity": "integer (int32)",
  "safetyStock": "integer (int32)",
  "binShelf": "string",
  "assetLedgerNo": "string",
  "expenseLedgerNo": "string",
  "syncFlag": "boolean",
  "activeStatus": "boolean",
  "crossReferenceNo": "string"
}
```

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**inventoryLocationId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory Location here. |
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

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "locationUOM": "string",
  "locationConversionFactor": "integer (int32)",
  "defaultIssueUOM": "string",
  "defaultIssueConversionFactor": "integer (int32)",
  "defaultCountUOM": "string",
  "defaultCountConversionFactor": "integer (int32)",
  "cost": "number (double)",
  "isBillable": "boolean",
  "isTaxable": "boolean",
  "itemType": "integer (int8)",
  "priceMarkup": "number (double)",
  "priceMarkupType": "integer (int8)",
  "disablePurchasing": "boolean",
  "minQuantity": "integer (int32)",
  "maxQuantity": "integer (int32)",
  "safetyStock": "integer (int32)",
  "binShelf": "string",
  "assetLedgerNo": "string",
  "expenseLedgerNo": "string",
  "syncFlag": "boolean",
  "activeStatus": "boolean",
  "crossReferenceNo": "string"
}
```

## Get the list of cost layers for the specified Inventory Location

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryLocations({inventoryLocationId})/costLayers

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing cost layers within the Inventory Location specified by ID.

!!! note 

    This endpoint does not support logical operators (**and**, **or**, **in**, **gt**, **ge**, **lt**, **le**) for data filtering.

### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryLocationId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory Location here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|      
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition.|
|**$orderby**: string <br> *in query* | Sorts the results.|
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string default: <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

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
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**costLayerId**: string *(uuid)* | Unique Identifier of the Cost Layer |
|**inventoryLocationId**: string *(uuid)* | Unique Identifier of the Inventory Location |
|**locationName**: string | Name of the Location |
|**locationNo**: string | Identification Number of the Location |
|**quantity**: integer *(int32)* | Quantity specified in the Line Items |
|**cost**: number *(double)* | Cost for this Location |
|**dateCreated**: string *(date-time)* | Date when the Cost Layer was created |
|**createdByUserName**: string | Name of the user who created the Cost Layer |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Cost Layer |
|**lastUpdatedBy**: string *(uuid)* | Name of the last user who updated the Cost Layer |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Cost Layer |
|**lastUpdated**: string *(date-time)* | Last Date when the Cost Layer was updated |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "costLayerId": "string",
      "inventoryLocationId": "string",
      "locationName": "string",
      "locationNo": "string",
      "quantity": "integer (int32)",
      "cost": "number (double)",
      "dateCreated": "string (date-time)",
      "createdByUserName": "string",
      "lastUpdatedByUserName": "string",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "createdBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdated": "string (date-time)"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```
## Get the list of Inventory Locations changed from the specified date

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryLocations/GetAllFromDate(from={from},facilityId={facilityId},syncFlag={syncFlag})

### <span style="color: #F05D30">Description</span>
Returns the paged list of the Inventory Locations changed from the specified date within the Facility specified by ID.

### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**from**: string *(date-time)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the Start Date here. |
|**facilityId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br>  *in path* | Enter the ID of the Facility here. |
|**syncFlag**: boolean  <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Identifies if the Location is synced with an external system. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|      
|**Authorization**: string default: <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|


### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryLocationId**: string *(uuid)* | Unique Identifier of the Inventory Item Location |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityName**: string | Name of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationName**: string | Name of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationUOM**: string | Unit of Measure of the Location |
|**locationConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Location's Unit of Measure |
|**inventoryStockUOM**: string | Unit of Measure to track Inventory Balance |
|**defaultIssueUOM**: string | Unit Of Measure used when issuing the Inventory Item to a Department or Patient |
|**defaultIssueConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure when issuing the Inventory Item to a Department or Patient |
|**defaultCountUOM**: string | Unit Of Measure used when counting the Inventory Item to a Department or Patient |
|**defaultCountConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure when counting the Inventory Item |
|**cost**: number *(double)* | Cost for the Location |
|**isBillable**: boolean | Is Location Billable or not? |
|**isTaxable**: boolean | Is Location Taxable or not? |
|**itemType**: integer *(int8)* | Type of the Item |
|**itemTypeText**: string | Value of the Item Type |
|**priceMarkup**: number *(double)* | The dollar or percent amount added to the Inventory Location Cost amount |
|**priceMarkupType**: integer *(int8)*  | Type of the Price Markup (% or $) |
|**priceMarkupTypeText**: string | Dollar or Percent |
|**disablePurchasing**: boolean | Disable or not Purchasing for the Location |
|**minQuantity**: integer *(int32)* | Minimal Inventory Items Quantity for this Location |
|**onRequisition**: integer *(int32)* | Quantity of Inventory Items for Requisition |
|**maxQuantity**: integer *(int32)* | Maximal Inventory Items Quantity for this Location |
|**safetyStock**: integer *(int32)* | Level of extra Stock that is maintained to mitigate the risk of stockouts |
|**binShelf**: string | Level of storage within the Location |
|**assetLedgerNo**: string | General Ledger Account Code for the Inventory Asset at the Location |
|**expenseLedgerNo**: string | General Ledger Account Code for the Inventory Expense at the Location |
|**syncFlag**: boolean | Is Inventory Location marked with Synchronization Flag or not? |
|**costLastUpdated**: string <br> *(date-time)*  | Last Date when the Cost was updated |
|**costLastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Cost |
|**dateAdded**: string *(date-time)* | Date when the Inventory Location was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the last user who added Location |
|**lastUpdated**: string *(date-time)* | Date of last Location update |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated Location |
|**activeStatus**: boolean | Is Location active or not? |
|**locationSynchronizationDate**: string <br> *(date-time)* | Date when the Location was synchronized |
|**costSynchronizationDate**: string *(date-time)* | Date when the Cost was synchronized |
|**defaultPurchaseUOM**: string | Default Unit of Measure for Purchasing |
|**valuationMethod**: integer <br> *(int32)* | Method of Valuation |
|**valuationMethodText**: string | Value of the Valuation Method |
|**pendingOrders**: integer <br> *(int32)* | Quantity of the Item in EA from all orders in the Pending status |
|**submittedOrders**: integer <br> *(int32)* | Quantity of the Item that are sent but not received yet |
|**quantityOnHand**: integer *(int32)*  | The total number of stock-keeping Inventory Items that are physically located in the Location |
|**lastUpdatedByName**: string | Name of the last user who updated the Inventory Location |
|**addedByName**: string | Name of the user who added the Inventory Location |
|**costLastUpdatedByName**: string | Name of the last user who updated the Cost |
|**crossReferenceNo**: string | Number of the Cross Reference |
|**inventoryActiveStatus**: boolean | Is Inventory Item active or not? |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
[
  {
    "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
    "inventoryId": "00000000-0000-0000-0000-000000000000",
    "inventoryNo": "string",
    "facilityId": "00000000-0000-0000-0000-000000000000",
    "facilityName": "string",
    "facilityNo": "string",
    "locationId": "00000000-0000-0000-0000-000000000000",
    "locationName": "string",
    "locationNo": "string",
    "locationUOM": "string",
    "locationConversionFactor": "integer (int32)",
    "inventoryStockUOM": "string",
    "defaultIssueUOM": "string",
    "defaultIssueConversionFactor": "integer (int32)",
    "defaultCountUOM": "string",
    "defaultCountConversionFactor": "integer (int32)",
    "cost": "number (double)",
    "isBillable": "boolean",
    "isTaxable": "boolean",
    "itemType": "integer (int8)",
    "itemTypeText": "string",
    "priceMarkup": "number (double)",
    "priceMarkupType": "integer (int8)",
    "priceMarkupTypeText": "string",
    "disablePurchasing": "boolean",
    "minQuantity": "integer (int32)",
    "onRequisition": "integer (int32)",
    "maxQuantity": "integer (int32)",
    "safetyStock": "integer (int32)",
    "binShelf": "string",
    "assetLedgerNo": "string",
    "expenseLedgerNo": "string",
    "syncFlag": "boolean",
    "costLastUpdated": "string (date-time)",
    "costLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
    "dateAdded": "string (date-time)",
    "addedBy": "00000000-0000-0000-0000-000000000000",
    "lastUpdated": "string (date-time)",
    "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
    "activeStatus": "boolean",
    "locationSynchronizationDate": "string (date-time)",
    "costSynchronizationDate": "string (date-time)",
    "defaultPurchaseUOM": "string",
    "valuationMethod": "integer (int32)",
    "valuationMethodText": "string",
    "pendingOrders": "integer (int32)",
    "submittedOrders": "integer (int32)",
    "quantityOnHand": "integer (int32)",
    "lastUpdatedByName": "string",
    "addedByName": "string",
    "costLastUpdatedByName": "string",
    "crossReferenceNo": "string",
    "inventoryActiveStatus": "boolean"
  }
]
```





