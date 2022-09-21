# InventoryActivity
## Get the list of inventory activities

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryActivity

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing inventory activity. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

!!! note 

    This endpoint does not support logical operators ( **gt**, **ge**, **lt**, **le**) for data filtering.
    

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
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition.|  
|**$orderby**: string <br> *in query* | Sorts the results.|
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
|<div style="width:200px">Property </div> |<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryActivityId**: string *(uuid)* | Unique Identifier of the Inventory Item activity |
|**activityType**: integer *(int32)* | Type of the Activity |
|**activityTypeName**: string | Name of the Activity Type |
|**organizationId**: string *(uuid)* | Unique Identifier of the Organization |
|**organizationNo**: string | Number of the Organization |
|**organizationName**: string | Name of the Organization |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**inventoryGroupId**: string *(uuid)* | Unique Identifier of the Group that contains related Inventory Items |
|**inventoryGroupName**: string | Name of the Group that contains related Inventory Items |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**inventoryDescription**: string | Description of the Inventory Item |
|**inventoryLocationId**: string <br> *(uuid)* | Unique Identifier of the Inventory Location |
|**locationNo**: string | Identification Key of the Location |
|**locationName**: string | Name of the Location |
|**inventoryVendorId**: string *(uuid)* | Unique Identifier of the Inventory Vendor |
|**vendorNo**: string | A code that identifies a supplier who sells you goods or services |
|**vendorName**: string | Name of the Vendor |
|**referenceNo**: string | Number of the Reference |
|**patientId**: string *(uuid)* | Unique Identifier of the Patient |
|**patientNo**: string | Number of the Patient |
|**departmentId**: string *(uuid)*  | Unique Identifier of the Department |
|**departmentNo**: string | Number of the Department |
|**departmentName**: string | Name of the Department |
|**impactQuantity**: integer *(int32)* | Unit that is used for differentiation of the quantity change |
|**stockUOM**: string | Unit of Measure to track Inventory Balance |
|**unitCost**: number *(double)* | Cost of the one unit of Item |
|**unitPrice**: number *(double)*  | The vendor's price for the Inventory Item |
|**expenseLedgerNo**: string | General Ledger Account Code for the Inventory Expense at the locations |
|**assetLedgerNo**: string | General Ledger Account Code for the Inventory Asset at the Locations |
|**glCode**: string | General Ledger Code |
|**lotNo**: string | Identification number assigned to a particular quantity or lot of material from a single manufacturer |
|**serialNo**: string | Unique Identifier assigned incrementally or sequentially to an Item, to identify it |
|**expDate**: string *(date-time)* | Previously determined date after which item should no longer be used |
|**lastUpdated**: string *(date-time)* | Last Date when the Inventory Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the user who updated the Inventory Item |
|**lastUpdatedByName**: string | Name of the user who updated the Inventory Item |
|**userName**: string | Name of the user who performed the operation |
|**quantityOnHand**: integer *(int32)* | The total number of stock-keeping Inventory items that are physically located in the Location |
|**sourceEntityId**: string *(uuid)*  | Unique Identifier of the Source Entity |
|**submittedEntityId**: string *(uuid)*  | Unique Identifier of the Submitted Entity |
|**classification**: string | Classification of the Inventory Item |
|**classification2**: string | Additional classification of the Inventory Item |
|**arBillingCode**: string | Code for interfacing billing codes in a patient billing system |
|**hcpcsCode**: string | Code for interfacing billing codes in a patient billing system |
|**unspscCode**: string | Code for interfacing billing codes in a patient billing system |
|**isLatex**: boolean | Is the item latex or not? |
|**defaultIssueUOM**: string | Unit Of Measure used when issuing the Inventory Item to a Department or Patient |
|**defaultIssueConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure when issuing the Inventory Item to a Department or Patient |
|**defaultCountUOM**: string | Unit Of Measure used when counting the Inventory Item to a Department or Patient |
|**defaultCountConversionFactor**: string <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure when counting the Inventory Item |
|**defaultExpenseLedgerNo**: string | Default General Ledger Account Code for the Inventory Item |
|**defaultAssetLedgerNo**: string | Default General Ledger Account Code for the Inventory Item |
|**locationUOM**: string | Unit of Measure of the Location |
|**locationConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure for the location |
|**itemTypeId**: integer *(int32)* | Unique identifier of the Item type |
|**itemTypeName**: string | Name of the Item type (Stock, Non-Stock, Service, Consignment, Capital)|
|**priceMarkup**: number *(double)* | Markup of the Price |
|**priceMarkupType**: string | Type of the Price Markup (% or $) |
|**minQuantity**: integer *(int32)* | Prefered Minimum quantity of the Item on the Location |
|**maxQuantity**: integer *(int32)* | Prefered Maximum quantity of the Item on the Location |
|**safetyStock**: integer *(int32)* | Level of extra Stock that is maintained to mitigate the risk of stockouts |
|**binShelf**: string | Level of storage within the Location |
|**syncFlag**: boolean | Is Inventory Location marked with Synchronization Flag or not? |
|**disablePurchasing**: boolean | Is Purchasing disabled for the Location |
|**isBillable**: boolean | Is Location Billable or not? |
|**isTaxable**: boolean | Is Location Taxable or not? |
|**vendorItemNo**: string | Code that vendor uses for the Item identification |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**priority**: integer *(int32)* | Priority of the Inventory Item |
|**contractNo**: string | Identification Number of the Contract |
|**contractExpirationDate**: string <br> *(date-time)* | Expiration Date of the Contract |
|**manufacturerId**: string *(uuid)* | Unique Identifier of the Manufacturer |
|**manufacturerNo**: string | Code that identifies a manufacturer |
|**manufacturerName**: string | Name of the Manufacturer |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**gtin**: string | Global Trade Item Number |
|**ndcNo**: string | National Drug Code number |
|**departmentGlcode**: string | General Ledger Code of the Department |
|**transactionQuantity**: integer *(int32)* | Quantity used for the transaction the Inventory Item |
|**transactionUOM**: string | Unit Of Measure used for the transaction the Inventory Item |
|**transactionCF**: integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure for the transaction |
|**extendedCost**: number *(double)* | Total Cost of the Line |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
      "items": [
        {
          "inventoryActivityId": "00000000-0000-0000-0000-000000000000",
          "activityType": "integer (int32)",
          "activityTypeName": "string",
          "organizationId": "00000000-0000-0000-0000-000000000000",
          "organizationNo": "string",
          "organizationName": "string",
          "facilityId": "00000000-0000-0000-0000-000000000000",
          "facilityNo": "string",
          "facilityName": "string",
          "inventoryGroupId": "00000000-0000-0000-0000-000000000000",
          "inventoryGroupName": "string",
          "inventoryId": "00000000-0000-0000-0000-000000000000",
          "inventoryNo": "string",
          "inventoryDescription": "string",
          "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
          "locationNo": "string",
          "locationName": "string",
          "inventoryVendorId": "00000000-0000-0000-0000-000000000000",
          "vendorNo": "string",
          "vendorName": "string",
          "referenceNo": "string",
          "patientId": "00000000-0000-0000-0000-000000000000",
          "patientNo": "string",
          "departmentId": "00000000-0000-0000-0000-000000000000",
          "departmentNo": "string",
          "departmentName": "string",
          "impactQuantity": "integer (int32)",
          "stockUOM": "string",
          "unitCost": "number (double)",
          "unitPrice": "number (double)",
          "expenseLedgerNo": "string",
          "assetLedgerNo": "string",
          "glCode": "string",
          "lotNo": "string",
          "serialNo": "string",
          "expDate": "string (date-time)",
          "lastUpdated": "string (date-time)",
          "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
          "lastUpdatedByName": "string",
          "userName": "string",
          "quantityOnHand": "integer (int32)",
          "sourceEntityId": "00000000-0000-0000-0000-000000000000",
          "submittedEntityId": "00000000-0000-0000-0000-000000000000",
          "classification": "string",
          "classification2": "string",
          "arBillingCode": "string",
          "hcpcsCode": "string",
          "unspscCode": "string",
          "isLatex": "boolean",
          "defaultIssueUOM": "string",
          "defaultIssueConversionFactor": "integer (int32)",
          "defaultCountUOM": "string",
          "defaultCountConversionFactor": "integer (int32)",
          "defaultExpenseLedgerNo": "string",
          "defaultAssetLedgerNo": "string",
          "locationUOM": "string",
          "locationConversionFactor": "integer (int32)",
          "itemTypeId": "integer (int32)",
          "itemTypeName": "string",
          "priceMarkup": "number (double)",
          "priceMarkupType": "string",
          "minQuantity": "integer (int32)",
          "maxQuantity": "integer (int32)",
          "safetyStock": "integer (int32)",
          "binShelf": "string",
          "syncFlag": "boolean",
          "disablePurchasing": "boolean",
          "isBillable": "boolean",
          "isTaxable": "boolean",
          "vendorItemNo": "string",
          "vendorUOM": "string",
          "vendorConversionFactor": "integer (int32)",
          "priority": "integer (int32)",
          "contractNo": "string",
          "contractExpirationDate": "string (date-time)",
          "manufacturerId": "00000000-0000-0000-0000-000000000000",
          "manufacturerNo": "string",
          "manufacturerName": "string",
          "manufacturerItemNo": "string",
          "gtin": "string",
          "ndcNo": "string",
          "departmentGlcode": "string",
          "transactionQuantity": "integer (int32)",
          "transactionUOM": "string",
          "transactionCF": "integer (int32)",
          "extendedCost": "number (double)"
        }
      ],
      "nextPageLink": "string",
      "count": "integer (int64)"
    }
```
