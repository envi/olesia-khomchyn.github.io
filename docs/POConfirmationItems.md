# POConfirmationItems
## Get the list of PO confirmation items

### <span style="color: #F05D30">Path</span>
GET /odata/POConfirmationItems

### <span style="color: #F05D30">Description</span>
Returns the list of PO confirmation items within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**$filter**: string <br> *in query* | Restricts the set of items returned. The maximum number of expressions is 100. | 
|**$orderby**: string <br> *in query* | Specifies the order in which items are returned. The maximum number of expressions is 5. | 
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|
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
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>
<style>
td, th {
   border: none!important;
}
</style>
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**poConfirmationItemId**: string *(uuid)* | Unique Identifier of the Purchase Order Confirmation Item |
|**poConfirmationId**: string *(uuid)* | Unique Identifier of the Purchase Order Confirmation |
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**purchaseOrderNo**: string | Number of the Purchase Order |
|**lineItemNo**: integer *(int32)* | Number of the Line Item |
|**quantity**: integer *(int32)* | Quantity specified in the Line Items |
|**uom**: string | Unit of Measure |
|**price**: number *(double)* | Price of the Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**manufacturer**: string | Manufacturer Name |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**inventoryDescription**: string | Description of the Inventory Item |
|**updatedPOPrice**: boolean | Was Purchase Order Price updated or not? |
|**updatedInventoryPrice**: boolean | Was Inventory Item Price updated or not? |
|**dateCreated**: string *(date-time)* | Date when the Purchase Order Confirmation Item was created |
|**lastUpdated**: string *(date-time)* | Last Date when the Purchase Order Confirmation Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Purchase Order Confirmation Item |
|**lastUpdatedByName**: string | Name of the last user who updated the Purchase Order Confirmation Item |
|**notes**: string | Comments about the Purchase Order Confirmation Item |
|**isUnresolved**: string *(boolean)* | Is the Purchase Order Confirmation Item unresolved? |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
"items": [
{
"poConfirmationItemId": "00000000-0000-0000-0000-000000000000",
"poConfirmationId": "00000000-0000-0000-0000-000000000000",
"purchaseOrderId": "00000000-0000-0000-0000-000000000000",
"purchaseOrderNo": "string",
"lineItemNo": "integer (int32)",
"quantity": "integer (int32)",
"uom": "string",
"price": "number (double)",
"inventoryNo": "string",
"vendorItemNo": "string",
"manufacturer": "string",
"manufacturerItemNo": "string",
"inventoryDescription": "string",
"updatedPOPrice": "boolean",
"updatedInventoryPrice": "boolean",
"dateCreated": "string (date-time)",
"lastUpdated": "string (date-time)",
"lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
"lastUpdatedByName": "string",
"notes": "string",
"isUnresolved": "boolean"
}
],
"nextPageLink": "string",
"count": "integer (int64)"
}
```

## Get the specified PO confirmation item

### <span style="color: #F05D30">Path</span>
GET /odata/POConfirmationItems({poConfirmationItemId})

### <span style="color: #F05D30">Description</span>
Returns the details of the PO confirmation item specified by ID.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**poConfirmationItemId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the PO Confirmation Item here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |

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
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**404 Not Found** | Specified ID is absent in the system. |
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>
<style>
td, th {
   border: none!important;
}
</style>
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**poConfirmationItemId**: string *(uuid)* | Unique Identifier of the Purchase Order Confirmation Items |
|**poConfirmationId**: string *(uuid)* | Unique Identifier of the Purchase Order Confirmation |
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**purchaseOrderNo**: string | Number of the Purchase Order |
|**lineItemNo**: integer *(int32)* | Number of the Line Item |
|**quantity**: integer *(int32)* | Quantity specified in the Line Items |
|**uom**: string | Unit of Measure |
|**price**: number *(double)* | Price of the Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**manufacturer**: string | Manufacturer Name |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**inventoryDescription**: string | Description of the Inventory Item |
|**updatedPOPrice**: boolean | Was Purchase Order Price updated or not? |
|**updatedInventoryPrice**: boolean | Was Inventory Item Price updated or not? |
|**dateCreated**: string *(date-time)* | Date when the Purchase Order Confirmation Item was created |
|**lastUpdated**: string *(date-time)* | Last Date when the Purchase Order Confirmation Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Purchase Order Confirmation Item |
|**lastUpdatedByName**: string | Name of the last user who updated the Purchase Order Confirmation Item |
|**notes**: string | Comments about the Purchase Order Confirmation Item |
|**isUnresolved**: string *(boolean)* | Is the Purchase Order Confirmation Item unresolved? |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
"poConfirmationItemId": "00000000-0000-0000-0000-000000000000",
"poConfirmationId": "00000000-0000-0000-0000-000000000000",
"purchaseOrderId": "00000000-0000-0000-0000-000000000000",
"purchaseOrderNo": "string",
"lineItemNo": "integer (int32)",
"quantity": "integer (int32)",
"uom": "string",
"price": "number (double)",
"inventoryNo": "string",
"vendorItemNo": "string",
"manufacturer": "string",
"manufacturerItemNo": "string",
"inventoryDescription": "string",
"updatedPOPrice": "boolean",
"updatedInventoryPrice": "boolean",
"dateCreated": "string (date-time)",
"lastUpdated": "string (date-time)",
"lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
"lastUpdatedByName": "string",
"notes": "string",
"isUnresolved": "boolean"
}
```