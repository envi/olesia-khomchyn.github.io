# InventoryLocationsExtended

## Get the list of extended inventory location

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryLocationsExtended

### <span style="color: #F05D30">Description</span>
Returns the list of inventory locations within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>

| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|    
|**$filter**: string <br> *in query* | Restricts the set of Items returned. The maximum number of expressions is 100.|
|**$orderby**: string <br> *in query* | Specifies the order in which items are returned. The maximum number of expressions is 5. |
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string default: <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

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
|**inventoryLocationExtended<br>Id**: string *(uuid)* | Unique Identifier of the extended Inventory Location |
|**inventoryId**: string *(uuid)*| Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**inventoryDescription**: string | Description of the Inventory Item |
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**defaultIssueUOM**: string | Unit Of Measure used when issuing the Inventory Item to a Department or Patient |
|**defaultIssueConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure when issuing the Inventory Item to a Department or Patient |
|**defaultCountUOM**: string | Unit Of Measure used when counting the Inventory Item to a Department or Patient |
|**defaultCountConversionFactor**: <br> integer *(int32)*  | Number of Stock Keeping Units in another Unit of Measure when counting the Inventory Item |
|**cost**: number *(double)* | Cost for the Location |
|**isBillable**: boolean | Is Location Billable or not? |
|**isTaxable**: boolean | Is Location Taxable or not? |
|**itemType**: integer <br> *(int8)* | Type of the Item |
|**itemTypeText**: string | Value of the Item Type |
|**priceMarkup**: number *(double)* | The dollar or percent amount added to the Inventory Location Cost amount |
|**priceMarkupType**: integer *(int8)* | Type of the Price Markup |
|**priceMarkupTypeText**: string | Dollar or Percent |
|**disablePurchasing**: boolean | Disable or not Purchasing for the Location? |
|**minQuantity**: integer *(int32)* | Minimal Inventory Items Quantity for this Location |
|**maxQuantity**: integer *(int32)* | Maximum Inventory Items Quantity for this Location |
|**safetyStock**: integer (int32) | Level of extra Stock that is maintained to mitigate risk of stockouts |
|**binShelf**: string | Level of storage within the Location |
|**assetLedgerNo**: string | General Ledger Account Code for the Inventory Asset at the Locations |
|**expenseLedgerNo**: string | General Ledger Account Code for the Inventory Expense at the Locations |
|**syncFlag**: boolean | Is Inventory Location marked with Synchronization Flag or not? |
|**locationUOM**: string | Unit of Measure of the Location |
|**locationConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Location's Unit of Measure |
|**activeStatus**: boolean | Is Location active or not? |
|**crossReferenceNo**: string | Number of the Cross Reference |
|**inventoryGroupId**: string *(uuid)* | Unique Identifier of the Group that contains related Inventory Items |
|**inventoryGroupNo**: string | Number of the Group that contains related Inventory Items |
|**inventoryGroupName**: string | Name of the Group that contains related Inventory Items |
|**stockUOM**: string | Unit of Measure to track Inventory Balance |
|**unspscCode**: string | Code for categorizing the Inventory Items |
|**defaultAssetLedgerNo**: string | Default Asset Ledger Account Code for the Inventory Item at a specific location |
|**defaultExpenseLedger<br>No**: string | Default Expense Ledger Account Code for the Inventory Item at a specific location |
|**classificationId**: string *(uuid)* | Unique Identifier of the Inventory Category defined on the Organization level |
|**classificationName**: string | Name of the Category of the Inventory defined on the Organization level |
|**classification2Id**: string *(uuid)* | Unique Identifier of the second Inventory Category defined on the Organization level |
|**classification2Name**: string | Name of the second Inventory Category defined on the Organization level |
|**periopItemCategoryId**: <br> string *(uuid)* | Unique Identifier of the Perioperative Item Category |
|**periopItemCategory**: string | Category of the Perioperative Item |
|**hcpcsCode**: string | Code for interfacing billing codes in a patient billing system |
|**arBillingCode**: string | Code for interfacing billing codes in a patient billing system |
|**isLatex**: boolean | Is the Item latex or not? |
|**vendorPriority**: integer *(int32)* | Priority of the Vendor |
|**inventoryVendorId**: string *(uuid)* | Unique Identifier of the Inventory Item Vendor |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**vendorItemNo**: string | Code that is used by the vendor for the Item identification |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**vendorCost**: number *(double)* | Item Cost of the Vendor |
|**contractNo**: string | Number of the Contract |
|**contractExpiration**: string <br> *(date-time)* | Expiration Date of the Contract |
|**manufacturerId**: string *(uuid)* | Unique Identifier of the Manufacturer |
|**manufacturerNo**: string | Code that identifies a Manufacturer |
|**manufacturerName**: string | Name of the Manufacturer |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**gtin**: string | Global Trade Item Number |
|**ndcNumber**: string | National Drug Code number |
|**lockCost**: boolean | Is the Cost of the Inventory Item Vendor locked or not? |
|**inventoryActiveStatus**: boolean | Is Inventory Item active or not? |
|**inventoryLastUpdated**: string <br> *(date-time)* | Last Date when the Inventory Item was updated |
|**inventoryLastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Inventory Item |
|**inventoryLastUpdatedBy<br>Name**: string | Name of the last user who updated the Inventory Item |
|**dateAdded**: string *(date-time)* | Date when the Inventory Location was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Inventory Location |
|**addedByName**: string | Name of the user who added the Inventory Location |
|**lastUpdated**: string *(date-time)* | Last Date when the Inventory Location was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Inventory Location |
|**lastUpdatedByName**: string | Name of the last user who updated the Inventory Location |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
{
  "items": [
    {
      "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
      "inventoryId": "00000000-0000-0000-0000-000000000000",
      "inventoryNo": "string",
      "inventoryDescription": "string",
      "locationId": "00000000-0000-0000-0000-000000000000",
      "locationNo": "string",
      "locationName": "string",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "facilityNo": "string",
      "facilityName": "string",
      "defaultIssueUOM": "string",
      "defaultIssueConversionFactor": "integer (int32)",
      "defaultCountUOM": "string",
      "defaultCountConversionFactor": "integer (int32)",
      "cost": "number (double)",
      "isBillable": "boolean",
      "isTaxable": "boolean",
      "itemType": "integer (int32)",
      "itemTypeText": "string",
      "priceMarkup": "number (double)",
      "priceMarkupType": "integer (int8)",
      "priceMarkupTypeText": "string",
      "disablePurchasing": "boolean",
      "minQuantity": "integer (int32)",
      "maxQuantity": "integer (int32)",
      "safetyStock": "integer (int32)",
      "binShelf": "string",
      "assetLedgerNo": "string",
      "expenseLedgerNo": "string",
      "syncFlag": "boolean",
      "locationUOM": "string",
      "locationConversionFactor": "integer (int32)",
      "activeStatus": "boolean",
      "crossReferenceNo": "string",
      "inventoryGroupId": "00000000-0000-0000-0000-000000000000",
      "inventoryGroupNo": "string",
      "inventoryGroupName": "string",
      "stockUOM": "string",
      "unspscCode": "string",
      "defaultAssetLedgerNo": "string",
      "defaultExpenseLedgerNo": "string",
      "classificationId": "00000000-0000-0000-0000-000000000000",
      "classificationName": "string",
      "classification2Id": "00000000-0000-0000-0000-000000000000",
      "classification2Name": "string",
      "periopItemCategoryId": "00000000-0000-0000-0000-000000000000",
      "periopItemCategory": "string",
      "hcpcsCode": "string",
      "arBillingCode": "string",
      "isLatex": "boolean",
      "vendorPriority": "integer (int32)",
      "inventoryVendorId": "00000000-0000-0000-0000-000000000000",
      "vendorId": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "vendorItemNo": "string",
      "vendorUOM": "string",
      "vendorConversionFactor": "integer (int32)",
      "vendorCost": "number (double)",
      "contractNo": "string",
      "contractExpiration": "string (date-time)",
      "manufacturerId": "00000000-0000-0000-0000-000000000000",
      "manufacturerNo": "string",
      "manufacturerName": "string",
      "manufacturerItemNo": "string",
      "gtin": "string",
      "ndcNumber": "string",
      "lockCost": "boolean",
      "inventoryActiveStatus": "boolean",
      "inventoryLastUpdated": "string (date-time)",
      "inventoryLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "inventoryLastUpdatedByName": "string",
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



