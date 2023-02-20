# Inventory

## Get the list of inventory items

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing inventory within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request parameters</span>
<style>
td, th {
   border: none!important;
}
</style>

| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
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
| <div style="width:200px">Property </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryId**: string *(uuid)*| Unique Identifier of the Inventory Item |
|**organizationId**: string *(uuid)*| Unique Identifier of the Organization|
|**organizationName**: string | Name of the Organization|
|**inventoryGroupId**: string *(uuid)* | Unique Identifier of the Group that contains related Inventory Items |
|**inventoryNo**: string| Identification code of the Inventory Item |
|**inventoryGroupName**: string | Name of the Group that contains related Inventory Items|
|**inventoryDescription**: string |Description of the Inventory Item |
|**inventoryDescription2**: string | Additional Description of the Inventory Item |
|**stockUOM**: string | Unit of Measure to track Inventory Balance |
|**arBillingCode**: string | Code for interfacing billing codes in a patient billing system |
|**hcpcsCode**: string | Code for interfacing billing codes in a patient billing system |
|**notes**: string | Comments about the Inventory Item |
|**dateAdded**: string *(date-time)* | Date when the Inventory Item was added |
|**addedId**: string *(uuid)* | Unique Identifier of the user who added the Inventory Item |
|**addedByName**: string | Name of the user who added Inventory Item |
|**lastUpdated**: string (date-time) | Last Date when the Inventory Item was updated |
|**lastUpdatedBy**: string (uuid) | Unique Identifier of the last user who updated the Inventory Item |
|**lastUpdatedByName**: string | Name of the last user who updated the Inventory Item |
|**activeStatus**: boolean | Is the Status of the Inventory Item active or not? |
|**unspscCode**: string | Code for categorizing the Inventory Items |
|**isLatex**: boolean |Is the Item latex or not? |
|**classificationId**: string *(uuid)* | Unique Identifier of the Inventory Category defined on the Organization level |
|**classificationName**: string | Name of the Category of the Inventory defined on the Organization level |
|**classification2Id**: string *(uuid)* | Unique Identifier of the second Inventory Category defined on the Organization level |
|**classification2Name**: string | Name of the second Inventory Category defined on the Organization level |
|**defaultExpenseLedgerNo**: string | Default General Ledger Account Code for the Inventory Item at specific locations |
|**defaultAssetLedgerNo**: string | Default General Ledger Account Code for the Inventory Item at specific locations |
|**periopCategoryId**: string *(uuid)* | Unique Identifier of the Perioperative Category |
|**periopItemCategory**: string | Category of the Perioperative Item |
|**systemTypeId**: integer *(int32)* | Unique Identifier of the System Type |
|**systemType**: string | Type of the Inventory Item in the scope of the system (Standard or Implant) |
|**defaultIsBillable**: boolean | Is Inventory billable by default or not? |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
{
  "items": [
    {
      "inventoryId": "00000000-0000-0000-0000-000000000000",
      "organizationId": "00000000-0000-0000-0000-000000000000",
      "organizationName": "string",
      "inventoryGroupId": "00000000-0000-0000-0000-000000000000",
      "inventoryNo": "string",
      "inventoryGroupName": "string",
      "inventoryDescription": "string",
      "inventoryDescription2": "string",
      "stockUOM": "string",
      "arBillingCode": "string",
      "hcpcsCode": "string",
      "notes": "string",
      "dateAdded": "string (date-time)",
      "addedId": "00000000-0000-0000-0000-000000000000",
      "addedByName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByName": "string",
      "activeStatus": "boolean",
      "unspscCode": "string",
      "isLatex": "boolean",
      "classificationId": "00000000-0000-0000-0000-000000000000",
      "classificationName": "string",
      "classification2Id": "00000000-0000-0000-0000-000000000000",
      "classification2Name": "string",
      "defaultExpenseLedgerNo": "string",
      "defaultAssetLedgerNo": "string",
      "periopCategoryId": "00000000-0000-0000-0000-000000000000",
      "periopItemCategory": "string",
      "systemTypeId": "integer (int32)",
      "systemType": "string",
      "defaultIsBillable": "boolean"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}

```
## Create a new inventory

### <span style="color: #F05D30">Path</span>
POST /odata/Inventory

### <span style="color: #F05D30">Description</span>
Creates a new inventory within a logged organization.

### <span style="color: #F05D30">Request body</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryGroupId**: string *(uuid)* | Unique Identifier of the Group that contains related Inventory Items |
|**inventoryNo**: string| Identification code of the Inventory Item |
|**inventoryDescription**: string |Description of the Inventory Item |
|**inventoryDescription2**: string | Additional Description of the Inventory Item |
|**stockUOM**: string | Unit of Measure to track Inventory Balance |
|**arBillingCode**: string | Code for interfacing billing codes in a patient billing system |
|**hcpcsCode**: string | Code for interfacing billing codes in a patient billing system |
|**notes**: string | Comments about the Inventory Item |
|**activeStatus**: boolean | Is the Status of the Inventory Item active or not? |
|**unspscCode**: string | Code for categorizing the Inventory Items |
|**isLatex**: boolean |Is the Item latex or not? |
|**classificationId**: string *(uuid)* | Unique Identifier of the Inventory Category defined on the Organization level |
|**classification2Id**: string *(uuid)* | Unique Identifier of the second Inventory Category defined on the Organization level |
|**defaultExpenseLedgerNo**: string | Default General Ledger Account Code for the Inventory Item at specific locations |
|**defaultAssetLedgerNo**: string | Default General Ledger Account Code for the Inventory Item at specific locations |
|**periopCategoryId**: string *(uuid)* | Unique Identifier of the Perioperative Category |
|**systemTypeId**: integer *(int32)* | Unique Identifier of the System Type |
|**defaultIsBillable**: boolean | Is Inventory billable by default or not? |


``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML<br>Request Example"
{
  "inventoryGroupId": "00000000-0000-0000-0000-000000000000",
  "inventoryNo": "string",
  "inventoryDescription": "string",
  "inventoryDescription2": "string",
  "stockUOM": "string",
  "arBillingCode": "string",
  "hcpcsCode": "string",
  "notes": "string",
  "activeStatus": "boolean",
  "unspscCode": "string",
  "isLatex": "boolean",
  "classificationId": "00000000-0000-0000-0000-000000000000",
  "classification2Id": "00000000-0000-0000-0000-000000000000",
  "defaultExpenseLedgerNo": "string",
  "defaultAssetLedgerNo": "string",
  "periopCategoryId": "00000000-0000-0000-0000-000000000000",
  "systemTypeId": "integer (int32)",
  "defaultIsBillable": "boolean"
}
```

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|   
|type|string *(uuid)*|    
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request.|


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
"00000000-0000-0000-0000-000000000000"

```

## Get the specified inventory

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory({inventoryId})

### <span style="color: #F05D30">Description</span>
Returns the details of the inventory specified by ID.

### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|      
|**Authorization**: string default: <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|


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
| <div style="width:200px">Property</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryId**: string *(uuid)*| Unique Identifier of the Inventory Item|
|**organizationId**: string *(uuid)*| Unique Identifier of the Organization|
|**organizationName**: string | Name of the Organization|
|**inventoryGroupId**: string *(uuid)* | Unique Identifier of the Group that contains related Inventory Items |
|**inventoryNo**: string| Identification code of the Inventory Item |
|**inventoryGroupName**: string | Name of the Group that contains related Inventory Items|
|**inventoryDescription**: string |Description of the Inventory Item |
|**inventoryDescription2**: string | Additional Description of the Inventory Item |
|**stockUOM**: string | Unit of Measure to track Inventory Balance |
|**arBillingCode**: string | Code for interfacing billing codes in a patient billing system |
|**hcpcsCode**: string | Code for interfacing billing codes in a patient billing system |
|**notes**: string | Comments about the Inventory Item |
|**dateAdded**: string *(date-time)* | Date when the Inventory Item was added |
|**addedId**: string *(uuid)* | Unique Identifier of the user who added the Inventory Item |
|**addedByName**: string | Name of the user who added Inventory Item |
|**lastUpdated**: string (date-time) | Last Date when the Inventory Item was updated |
|**lastUpdatedBy**: string (uuid) | Unique Identifier of the last user who updated the Inventory Item |
|**lastUpdatedByName**: string | Name of the last user who updated the Inventory Item |
|**activeStatus**: boolean | Is the Status of the Inventory Item active or not? |
|**unspscCode**: string | Code for categorizing the Inventory Items |
|**isLatex**: boolean |Is the Item latex or not? |
|**classificationId**: string *(uuid)* | Unique Identifier of the Inventory Category defined on the Organization level |
|**classificationName**: string | Name of the Category of the Inventory defined on the Organization level |
|**classification2Id**: string *(uuid)* | Unique Identifier of the second Inventory Category defined on the Organization level |
|**classification2Name**: string | Name of the second Inventory Category defined on the Organization level |
|**defaultExpenseLedgerNo**: string | Default General Ledger Account Code for the Inventory Item at specific locations |
|**defaultAssetLedgerNo**: string | Default General Ledger Account Code for the Inventory Item at specific locations |
|**periopCategoryId**: string *(uuid)* | Unique Identifier of the Perioperative Category |
|**periopItemCategory**: string | Category of the Perioperative Item |
|**systemTypeId**: integer *(int32)* | Unique Identifier of the System Type |
|**systemType**: string | Type of the Inventory Item in the scope of the system (Standard or Implant) |
|**defaultIsBillable**: boolean | Is Inventory billable by default or not? |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
{
  "inventoryId": "00000000-0000-0000-0000-000000000000",
  "organizationId": "00000000-0000-0000-0000-000000000000",
  "organizationName": "string",
  "inventoryGroupId": "00000000-0000-0000-0000-000000000000",
  "inventoryNo": "string",
  "inventoryGroupName": "string",
  "inventoryDescription": "string",
  "inventoryDescription2": "string",
  "stockUOM": "string",
  "arBillingCode": "string",
  "hcpcsCode": "string",
  "notes": "string",
  "dateAdded": "string (date-time)",
  "addedId": "00000000-0000-0000-0000-000000000000",
  "addedByName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByName": "string",
  "activeStatus": "boolean",
  "unspscCode": "string",
  "isLatex": "boolean",
  "classificationId": "00000000-0000-0000-0000-000000000000",
  "classificationName": "string",
  "classification2Id": "00000000-0000-0000-0000-000000000000",
  "classification2Name": "string",
  "defaultExpenseLedgerNo": "string",
  "defaultAssetLedgerNo": "string",
  "periopCategoryId": "00000000-0000-0000-0000-000000000000",
  "periopItemCategory": "string",
  "systemTypeId": "integer (int32)",
  "systemType": "string",
  "defaultIsBillable": "boolean"
}           
```
## Fully update the specified inventory

### <span style="color: #F05D30">Path</span>
PUT /odata/Inventory({inventoryId})

### <span style="color: #F05D30">Description</span>
Fully updates the details of the inventory specified by ID.

### <span style="color: #F05D30">Request body</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryId**: string *(uuid)*| Unique Identifier of the Inventory Item |
|**organizationId**: string *(uuid)*| Unique Identifier of the Organization|
|**organizationName**: string | Name of the Organization|
|**inventoryGroupId**: string *(uuid)* | Unique Identifier of the Group that contains related Inventory Items |
|**inventoryNo**: string| Identification code of the Inventory Item |
|**inventoryGroupName**: string | Name of the Group that contains related Inventory Items|
|**inventoryDescription**: string |Description of the Inventory Item |
|**inventoryDescription2**: string | Additional Description of the Inventory Item |
|**stockUOM**: string | Unit of Measure to track Inventory Balance |
|**arBillingCode**: string | Code for interfacing billing codes in a patient billing system |
|**hcpcsCode**: string | Code for interfacing billing codes in a patient billing system |
|**notes**: string | Comments about the Inventory Item |
|**dateAdded**: string *(date-time)* | Date when the Inventory Item was added |
|**addedId**: string *(uuid)* | Unique Identifier of the user who added the Inventory Item |
|**addedByName**: string | Name of the user who added Inventory Item |
|**lastUpdated**: string (date-time) | Last Date when the Inventory Item was updated |
|**lastUpdatedBy**: string (uuid) | Unique Identifier of the last user who updated the Inventory Item |
|**lastUpdatedByName**: string | Name of the last user who updated the Inventory Item |
|**activeStatus**: boolean | Is the Status of the Inventory Item active or not? |
|**unspscCode**: string | Code for categorizing the Inventory Items |
|**isLatex**: boolean |Is the Item latex or not? |
|**classificationId**: string *(uuid)* | Unique Identifier of the Inventory Category defined on the Organization level |
|**classificationName**: string | Name of the Category of the Inventory defined on the Organization level |
|**classification2Id**: string *(uuid)* | Unique Identifier of the second Inventory Category defined on the Organization level |
|**classification2Name**: string | Name of the second Inventory Category defined on the Organization level |
|**defaultExpenseLedgerNo**: string | Default General Ledger Account Code for the Inventory Item at specific locations |
|**defaultAssetLedgerNo**: string | Default General Ledger Account Code for the Inventory Item at specific locations |
|**periopCategoryId**: string *(uuid)* | Unique Identifier of the Perioperative Category |
|**periopItemCategory**: string | Category of the Perioperative Item |
|**systemTypeId**: integer *(int32)* | Unique Identifier of the System Type |
|**systemType**: string | Type of the Inventory Item in the scope of the system (Standard or Implant) |
|**defaultIsBillable**: boolean | Is Inventory billable by default or not? |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML<br>Request Example"
{
  "inventoryId": "00000000-0000-0000-0000-000000000000",
  "organizationId": "00000000-0000-0000-0000-000000000000",
  "organizationName": "string",
  "inventoryGroupId": "00000000-0000-0000-0000-000000000000",
  "inventoryNo": "string",
  "inventoryGroupName": "string",
  "inventoryDescription": "string",
  "inventoryDescription2": "string",
  "stockUOM": "string",
  "arBillingCode": "string",
  "hcpcsCode": "string",
  "notes": "string",
  "dateAdded": "string (date-time)",
  "addedId": "00000000-0000-0000-0000-000000000000",
  "addedByName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByName": "string",
  "activeStatus": "boolean",
  "unspscCode": "string",
  "isLatex": "boolean",
  "classificationId": "00000000-0000-0000-0000-000000000000",
  "classificationName": "string",
  "classification2Id": "00000000-0000-0000-0000-000000000000",
  "classification2Name": "string",
  "defaultExpenseLedgerNo": "string",
  "defaultAssetLedgerNo": "string",
  "periopCategoryId": "00000000-0000-0000-0000-000000000000",
  "periopItemCategory": "string",
  "systemTypeId": "integer (int32)",
  "systemType": "string",
  "defaultIsBillable": "boolean"
}           
```
### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
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

## Partially update the specified inventory

### <span style="color: #F05D30">Path</span>
PATCH /odata/Inventory({inventoryId})

### <span style="color: #F05D30">Description</span>
Partially updates the details of the inventory specified by ID.

### <span style="color: #F05D30">Request body</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item|
|**organizationId**: string *(uuid)*| Unique Identifier of the Organization|
|**organizationName**: string | Name of the Organization|
|**inventoryGroupId**: string *(uuid)*| Unique Identifier of the Group that contains related Inventory Items |
|**inventoryNo**: string| Identification code of the Inventory Item |
|**inventoryGroupName**: string | Name of the Group that contains related Inventory Items|
|**inventoryDescription**: string |Description of the Inventory Item |
|**inventoryDescription2**: string | Additional Description of the Inventory Item |
|**stockUOM**: string | Unit of Measure to track Inventory Balance |
|**arBillingCode**: string | Code for interfacing billing codes in a patient billing system |
|**hcpcsCode**: string | Code for interfacing billing codes in a patient billing system |
|**notes**: string | Comments about the Inventory Item |
|**dateAdded**: string *(date-time)* | Date when the Inventory Item was added |
|**addedId**: string *(uuid)* | Unique Identifier of the user who added the Inventory Item |
|**addedByName**: string | Name of the user who added Inventory Item |
|**lastUpdated**: string (date-time) | Last Date when the Inventory Item was updated |
|**lastUpdatedBy**: string (uuid) | Unique Identifier of the last user who updated the Inventory Item |
|**lastUpdatedByName**: string | Name of the last user who updated the Inventory Item |
|**activeStatus**: boolean | Is the Status of the Inventory Item active or not? |
|**unspscCode**: string | Code for categorizing the Inventory Items |
|**isLatex**: boolean |Is the Item latex or not? |
|**classificationId**: string *(uuid)* | Unique Identifier of the Inventory Category defined on the Organization level |
|**classificationName**: string | Name of the Category of the Inventory defined on the Organization level |
|**classification2Id**: string *(uuid)* | Unique Identifier of the second Inventory Category defined on the Organization level |
|**classification2Name**: string | Name of the second Inventory Category defined on the Organization level |
|**defaultExpenseLedgerNo**: string | Default General Ledger Account Code for the Inventory Item at specific locations |
|**defaultAssetLedgerNo**: string | Default General Ledger Account Code for the Inventory Item at specific locations |
|**periopCategoryId**: string *(uuid)* | Unique Identifier of the Perioperative Category |
|**periopItemCategory**: string | Category of the Perioperative Item |
|**systemTypeId**: integer *(int32)* | Unique Identifier of the System Type |
|**systemType**: string | Type of the Inventory Item in the scope of the system (Standard or Implant) |
|**defaultIsBillable**: boolean | Is Inventory billable by default or not? |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML<br>Request Example"
{
  "inventoryId": "00000000-0000-0000-0000-000000000000",
  "organizationId": "00000000-0000-0000-0000-000000000000",
  "organizationName": "string",
  "inventoryGroupId": "00000000-0000-0000-0000-000000000000",
  "inventoryNo": "string",
  "inventoryGroupName": "string",
  "inventoryDescription": "string",
  "inventoryDescription2": "string",
  "stockUOM": "string",
  "arBillingCode": "string",
  "hcpcsCode": "string",
  "notes": "string",
  "dateAdded": "string (date-time)",
  "addedId": "00000000-0000-0000-0000-000000000000",
  "addedByName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByName": "string",
  "activeStatus": "boolean",
  "unspscCode": "string",
  "isLatex": "boolean",
  "classificationId": "00000000-0000-0000-0000-000000000000",
  "classificationName": "string",
  "classification2Id": "00000000-0000-0000-0000-000000000000",
  "classification2Name": "string",
  "defaultExpenseLedgerNo": "string",
  "defaultAssetLedgerNo": "string",
  "periopCategoryId": "00000000-0000-0000-0000-000000000000",
  "periopItemCategory": "string",
  "systemTypeId": "integer (int32)",
  "systemType": "string",
  "defaultIsBillable": "boolean"
}
```
### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
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

## Get future pricing items for the specified inventory

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory({inventoryId})/futurePricing

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing future pricing items within inventory specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.


### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
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
| <div style="width:200px">Property</div>|<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**futurePricingId**: string *(uuid)* | Unique Identifier of the Future Pricing record |
|**inventoryId**: string *(uuid)*| Unique Identifier of the Inventory Item|
|**inventoryNo**: string | Identification code of the Inventory Item
|**vendorItemNo**: string | Code that is used by the vendor for the Item identification |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**organizationId**: string *(uuid)* | Unique Identifier of the Organization |
|**organizationNo**: string | Identification Number of the Organization |
|**organizationName**: string | Name of the Organization |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**contractNo**: string | Number of Contract |
|**contractExpDate**: string *(date-time)* | Expiration Date of the Contract |
|**priceChangeDate**: string <br> *(date-time)* | Date of the Price Changing |
|**newPrice**: number *(double)* | New Price value |
|**priceChangeStatus**: integer <br> *(int32)* | Status of the Price Changing |
|**priceChangeStatusName**: string | Status Name of the Price Changing |
|**dateAdded**: string *(date-time)* | Date when the Future Pricing was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Future Pricing |
|**lastUpdated**: string *(date-time)* | Last Date when the Future Pricing was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Future Pricing |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**addedByName**: string | Name of the user who added the Future Pricing |
|**lastUpdatedByName**: string | Name of the last user who updated the Future Pricing |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
{
  "items": [
    {
      "futurePricingId": "00000000-0000-0000-0000-000000000000",
      "inventoryId": "00000000-0000-0000-0000-000000000000",
      "inventoryNo": "string",
      "vendorItemNo": "string",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "vendorId": "00000000-0000-0000-0000-000000000000",
      "organizationId": "00000000-0000-0000-0000-000000000000",
      "organizationNo": "string",
      "organizationName": "string",
      "vendorUOM": "string",
      "vendorConversionFactor": "integer (int32)",
      "contractNo": "string",
      "contractExpDate": "string (date-time)",
      "priceChangeDate": "string (date-time)",
      "newPrice": "number (double)",
      "priceChangeStatus": "integer (int32)",
      "priceChangeStatusName": "string",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "facilityNo": "string",
      "facilityName": "string",
      "addedByName": "string",
      "lastUpdatedByName": "string"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}  
```

## Get the list of inventory UOMs for the specified inventory

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory({inventoryId})/inventoryUOMs

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing inventory UOMs within inventory specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.


### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
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
| <div style="width:200px">Property</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryUOMId**: string *(uuid)* | Unique Identifier of the Inventory Item Unit of Measure |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**uom**: string | Unit of Measure |
|**conversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure |
|**dateAdded**: string *(date-time)* | Date when the Inventory Item Unit of Measure was added |
|**addedId**: string (uuid) | Unique Identifier of the user who added Inventory Item Unit of Measure |
|**lastUpdated**: string *(date-time)* | Last Date when the Inventory Item Unit of Measure was updated |
|**lastUpdatedId**: string *(uuid)* | Unique Identifier of the last user who updated the Inventory Item Unit of Measure |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
{
  "items": [
    {
      "inventoryUOMId": "00000000-0000-0000-0000-000000000000",
      "inventoryId": "00000000-0000-0000-0000-000000000000",
      "inventoryNo": "string",
      "uom": "string",
      "conversionFactor": "integer (int32)",
      "dateAdded": "string (date-time)",
      "addedId": "00000000-0000-0000-0000-000000000000",
      "lastUpdated": "string (date-time)",
      "lastUpdatedId": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}   
```

## Get the list of inventory locations for the specified inventory

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory({inventoryId})/inventoryLocations

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing inventory locations within inventory specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
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
| <div style="width:200px">Property</div>|<div style="width:380px">Explanation</div>|                      
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
|**defaultIssueConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure when issuing the Inventory Item to a Department or Patient |
|**defaultCountUOM**: string | Unit Of Measure used when counting the Inventory Item to a Department or Patient |
|**defaultCountConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure when counting the Inventory Item |
|**cost**: number *(double)* | Cost for the Location |
|**isBillable**: boolean | Is Location Billable or not? |
|**isTaxable**: boolean | Is Location Taxable or not? |
|**itemType**: integer (int8) | Type of the Item |
|**itemTypeText**: string | Value of the Item Type |
|**priceMarkup**: number *(double)* | The dollar or percent amount added to the Inventory Location Cost amount |
|**priceMarkupType**: integer *(int8)* | Type of the Price Markup |
|**priceMarkupTypeText**: string | Dollar or Percent |
|**disablePurchasing**: boolean | Disable or not Purchasing for the Location? |
|**minQuantity**: integer *(int32)* | Minimal Inventory Items Quantity for this Location |
|**onRequisition**: integer *(int32)* | Quantity of Inventory Items for Requisition |
|**maxQuantity**: integer *(int32)* | Maximal Inventory Items Quantity for this Location |
|**safetyStock**: integer *(int32)* | Level of extra Stock that is maintained to mitigate risk of stockouts |
|**binShelf**: string | Level of storage within the Location |
|**assetLedgerNo**: string | General Ledger Account Code for the Inventory Asset at the Locations |
|**expenseLedgerNo**: string | General Ledger Account Code for the Inventory Expense at the Locations |
|**syncFlag**: boolean | Is Inventory Location marked with Synchronization Flag or not? |
|**costLastUpdated**: string *(date-time)* | Last Date when the Cost was updated |
|**costLastUpdatedBy**: string (uuid) | Unique Identifier of the last user who updated the Cost |
|**dateAdded**: string *(date-time)* | Date when the Inventory Location was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the last user who added Location |
|**lastUpdated**: string *(date-time)* | Date of last Location update |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated Location |
|**activeStatus**: boolean | Is Location active or not?|
|**locationSynchronizationDate**: <br> string *(date-time)* | Date when the Location was synchronized |
|**costSynchronizationDate**: <br> string *(date-time)* | Date when the Cost was synchronized |
|**defaultPurchaseUOM**: string | Default Unit of Measure for Purchasing |
|**valuationMethod**: integer *(int32)* | Method of Valuation |
|**valuationMethodText**: string | Value of the Valuation Method |
|**pendingOrders**: integer *(int32)* | Quantity of the Item in EA from all orders in the Pending status |
|**submittedOrders**: integer *(int32)* | Quantity of the Item that is sent but not received yet |
|**quantityOnHand**: integer *(int32)* | The total number of stock-keeping Inventory Items that are physically located in the Location |
|**lastUpdatedByName**: string | Name of the last user who updated the Inventory Location |
|**addedByName**: string | Name of the user who added the Inventory Location |
|**costLastUpdatedByName**: string | Name of the last user who updated the Cost |
|**crossReferenceNo**: string | Number of the Cross Reference |
|**inventoryActiveStatus**: boolean | Is Inventory Item active or not? |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
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

## Get the list of tracking settings for the specified inventory

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory({inventoryId})/inventoryTrackings

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing inventory tracking settings within inventory specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.
    


### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
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
| <div style="width:200px">Property</div>|<div style="width:480px">Explanation</div>|                      
|-----:|:-------| 
|**inventoryTrackingId**: string *(uuid)* | Unique Identifier of the Inventory Item Tracking |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**trackLot**: boolean | Is Tracking performed by Lot number or not? |
|**trackExpiration**: boolean | Is Tracking performed by Expiration Date or not? |
|**trackSerialNo**: boolean | Is Tracking performed by Serial Number or not? |
|**isOptional**: boolean | Is Tracking optional or not? |
|**dateAdded**: string *(date-time)* | Date when the Inventory Item Tracking was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Inventory Tracking |
|**addedByName**: string | Name of the user who added the Inventory Tracking |
|**lastUpdated**: string *(date-time)* | Last Date when the Inventory Item Tracking was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Inventory Item Tracking |
|**lastUpdatedByName**: string | Name of the last user who updated the Inventory Item Tracking |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
{
  "items": [
    {
      "inventoryTrackingId": "00000000-0000-0000-0000-000000000000",
      "inventoryId": "00000000-0000-0000-0000-000000000000",
      "inventoryNo": "string",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "facilityNo": "string",
      "facilityName": "string",
      "trackLot": "boolean",
      "trackExpiration": "boolean",
      "trackSerialNo": "boolean",
      "isOptional": "boolean",
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

## Get the PO history for the specified inventory

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory({inventoryId})/poHistoryItems

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing purchase order history within inventory specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.

### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
|**facility**: string <br> *in query* | Enter the name of the Facility here. |
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
| <div style="width:200px">Property</div>|<div style="width:480px">Explanation</div>|                      
|-----:|:-------| 
|**id**: string | Unique Identifier of the Inventory Item |
|**monthName**: string | Name of the Month when Purchase Order was made |
|**monthNumber**: integer *(int32)* | Number of the Month when Purchase Order was made |
|**quantityOrdered**: integer *(int64)* | Quantity of the ordered Inventory Items |
|**numberOfPOs**: integer *(int32)* | Number of the Purchase Orders |
|**totalCost**: number *(double)* | Total Cost of the Purchase Orders |
|**facilityName**: string | Name of the Facility |
|**year**: integer *(int32)* | Year when Purchase Order was made |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
{
  "items": [
    {
      "id": "string",
      "monthName": "string",
      "monthNumber": "integer (int32)",
      "quantityOrdered": "integer (int64)",
      "numberOfPOs": "integer (int32)",
      "totalCost": "number (double)",
      "facilityName": "string",
      "year": "integer (int32)"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}   
```

## Get the list of inventory vendors for the specified inventory

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory({inventoryId})/inventoryVendors

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing inventory vendors within inventory specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).


### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
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
| <div style="width:200px">Property</div>|<div style="width:480px">Explanation</div>|                      
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
|**vendorItemNo**: string | Code that is used by the vendor for the Item identification |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
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
|**costLastUpdatedBy**: string <br> *(uuid)* | Unique Identifier of the last user who updated the Cost |
|**dateAdded**: string *(date-time)* | Date when the Vendor of Inventory Item was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added Inventory Item Vendor |
|**lastUpdated**: string *(date-time)* | Last Date when the Inventory Item Vendor was updated
|**lastUpdatedBy**: string (uuid) | Unique Identifier of the user who updated Inventory Item Vendor |
|**activeStatus**: boolean | Is the Status of the Inventory Item Vendor active or not? |
|**ndcNumber**: string | National Drug Code number |
|**lockCost**: boolean | Is the Cost of the Inventory Item Vendor locked or not? |
|**costLastUpdatedByUserName**: <br> string | Name of the last user who updated the Cost |
|**addedByUserName**: string | Name of the user who added the Inventory Item Vendor |
|**lastUpdatedByUserName**: string | Name of the last user who updated Inventory Item Vendor |
|**pimKey**: string | Product Information Management Key |
|**altItemNo**: string | Alternative Item Number |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
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
## Get the list of tracking data

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory({inventoryId})/inventoryTrackingValues

### <span style="color: #F05D30">Description</span>
Returns the details of the inventory tracking values within inventory, facility, and tracking type specified by ID.

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.

### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
|**facilityId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in query* | Enter the ID of the Facility here. |
|**trackingType**: string <br> <span style="color: #F05D30">**required**</span> <br> *in query*  | Specify the type of the Tracking here (Lot/Serial/Expiration). |
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
| <div style="width:200px">Property</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------| 
|**inventoryTrackingItemId**: string <br> *(uuid)* | Unique Identifier of the Inventory Item Tracking |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**stockUOM**: string | Unit of Measure to track Inventory Balance |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**inventoryLocationId**: string <br> *(uuid)* | Unique Identifier of the Inventory Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**lot**: string | Identification number assigned to a particular quantity or lot of material from a single Manufacturer |
|**expirationDate**: string <br> *(date-time)* | Previously determined date after which Item should no longer be used |
|**serialNo**: string | Unique Identifier assigned incrementally or sequentially to an Item to uniquely identify it |
|**quantity**: integer *(int32)* | Quantity specified in the Line Items |
|**dateAdded**: string <br> *(date-time)* | Date when the Inventory Item Tracking was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added Inventory Item Tracking |
|**addedByName**: string | Name of the user who added Inventory Item Tracking |
|**lastUpdated**: string <br> *(date-time)* | Last Date when the Inventory Item Tracking was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Inventory Item Tracking |
|**lastUpdatedByName**: string | Name of the last user who updated the Inventory Item Tracking |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
{
  "items": [
    {
      "inventoryTrackingItemId": "00000000-0000-0000-0000-000000000000",
      "inventoryId": "00000000-0000-0000-0000-000000000000",
      "inventoryNo": "string",
      "stockUOM": "string",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "facilityNo": "string",
      "facilityName": "string",
      "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
      "locationNo": "string",
      "locationName": "string",
      "lot": "string",
      "expirationDate": "string (date-time)",
      "serialNo": "string",
      "quantity": "integer (int32)",
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


## Get the list of inventory locations cost and quantity for the specified inventory

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory({inventoryId})/inventoryLocationsCostAndQuantity

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing inventory locations cost and quantity within inventory specified by Id. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here.|
|**includeInactiveInventory**: boolean <br> default: false <br> *in query* | Include Inactive Inventory Items. |
|**includeInactiveLocations**: boolean <br> default: false <br> *in query* | Include Inactive Locations. |
|**includeInactiveInventoryLocations**: boolean <br> default: false <br> *in query* | Include Inactive Inventory Locations. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.| 
|**$filter**: string <br> *in query* | Restricts the set of items returned. The maximum number of expressions is 100.|
|**$orderby**: string <br> *in query* | Specifies the order in which items are returned. The maximum number of expressions is 5.|
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
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
| <div style="width:200px">Property</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------| 
|**inventoryLocationId**: string *(uuid)* | Unique Identifier of the Inventory Location |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory item |
|**locationNo**: string | Identification Number of the Location |
|**cost**: number *(double)* | Cost for the Location |
|**quantityOnHand**: integer *(int32)* | The total number of stock-keeping Inventory Items that are physically located in the Location |
|**activeStatus**: boolean | Is the Status of the Location active or not? |
|**dateAdded**: string *(date-time)* | Date when the Location was added |
|**addedBy**: string *(uuid)* | Name of the user who added the Location |
|**lastUpdated**: string *(date-time)* | Last Date when the Location was updated |
|**lastUpdatedBy**: string *(uuid)* | Name of the last user who updated the Location |
|**costLastUpdated**: string *(date-time)* | Last Date when the Cost was updated |
|**costLastUpdatedBy**: string *(uuid)* | Name of the last user who updated the Cost |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
{
  "items": [
    {
      "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
      "inventoryId": "00000000-0000-0000-0000-000000000000",
      "inventoryNo": "string",
      "locationNo": "string",
      "cost": "number (double)",
      "quantityOnHand": "integer (int32)",
      "activeStatus": "boolean",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "costLastUpdated": "string (date-time)",
      "costLastUpdatedBy": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}

```

## Get the list of inventory items changed from the specified date

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory/GetAllFromDate(from={from},facilityId={facilityId},syncFlag={syncFlag})

### <span style="color: #F05D30">Description</span>
Returns the paged list of the inventory items changed from the specified date within a facility specified by ID.

### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**from**: string *(date-time)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the Start Date here. |
|**facilityId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Facility here. |
|**syncFlag**: boolean <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Indicates whether only Items flagged with syncFlag should be returned. |
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
| <div style="width:200px">Property</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------| 
|**itemType**: string | Type of the Item |
|**billable**: boolean | Is the item billable or not? |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**organizationId**: string *(uuid)* | Unique Identifier of the Organization |
|**organizationName**: string | Name of the Organization |
|**inventoryGroupId**: string *(uuid)* | Unique Identifier of the Group that contains related Inventory Items |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**inventoryGroupName**: string | Name of the Group that contains related Inventory Items |
|**inventoryDescription**: string | Description of the Inventory Item |
|**inventoryDescription2**: string | Additional Description of the Inventory Item |
|**stockUOM**: string | Unit of Measure to track inventory Item Balance |
|**arBillingCode**: string | Code for interfacing billing codes in a patient billing system |
|**hcpcsCode**: string | Code for interfacing billing codes in a patient billing system |
|**notes**: string | Comments about the Inventory Item |
|**dateAdded**: string *(date-time)* | Date when the Inventory Item was added |
|**addedId**: string *(uuid)* | Unique Identifier of the user who added the Inventory Item |
|**addedByName**: string | Name of the user who added Inventory Item |
|**lastUpdated**: string *(date-time)* | Last Date when the Inventory Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Inventory Item |
|**lastUpdatedByName**: string | Name of the last user who updated the Inventory Item |
|**activeStatus**: boolean | Is the Status of the Inventory Item active or not? |
|**unspscCode**: string | Code for categorizing Inventory Items |
|**isLatex**: boolean | Is the Inventory Item latex or not? |
|**classificationId**: string *(uuid)* | Unique Identifier of the Inventory Category defined on the Organization level |
|**classificationName**: string | Name of the Category of the Inventory defined on the Organization level |
|**classification2Id**: string *(uuid)* | Unique Identifier of the second Inventory Category defined on the Organization level |
|**classification2Name**: string | Name of the second Inventory Category defined on the Organization level |
|**defaultExpenseLedgerNo**: string | Default General Ledger Account Code for the Inventory Item at specific locations |
|**defaultAssetLedgerNo**: string | Default General Ledger Account Code for the Inventory Item at specific locations |
|**periopCategoryId**: string *(uuid)* | Unique Identifier of the Perioperative Category |
|**periopItemCategory**: string | Category of the Perioperative Item |
|**itemType**: string | Type of the Item |
|**systemTypeId**: integer *(int32)* | Unique Identifier of the System Type |
|**systemType**: string | Type of the Inventory Item in the scope of the system (Standard or Implant) |
|**defaultIsBillable**: boolean | Is Inventory billable by default or not? |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
[
  {
    "itemType": "string",
    "billable": "boolean",
    "inventoryId": "00000000-0000-0000-0000-000000000000",
    "organizationId": "00000000-0000-0000-0000-000000000000",
    "organizationName": "string",
    "inventoryGroupId": "00000000-0000-0000-0000-000000000000",
    "inventoryNo": "string",
    "inventoryGroupName": "string",
    "inventoryDescription": "string",
    "inventoryDescription2": "string",
    "stockUOM": "string",
    "arBillingCode": "string",
    "hcpcsCode": "string",
    "notes": "string",
    "dateAdded": "string (date-time)",
    "addedId": "00000000-0000-0000-0000-000000000000",
    "addedByName": "string",
    "lastUpdated": "string (date-time)",
    "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
    "lastUpdatedByName": "string",
    "activeStatus": "boolean",
    "unspscCode": "string",
    "isLatex": "boolean",
    "classificationId": "00000000-0000-0000-0000-000000000000",
    "classificationName": "string",
    "classification2Id": "00000000-0000-0000-0000-000000000000",
    "classification2Name": "string",
    "defaultExpenseLedgerNo": "string",
    "defaultAssetLedgerNo": "string",
    "periopCategoryId": "00000000-0000-0000-0000-000000000000",
    "periopItemCategory": "string",
    "itemType": "string",
    "systemTypeId": "integer (int32)",
    "systemType": "string",
    "defaultIsBillable": "boolean"
  }
]
```

## Save the specified inventory vendor

### <span style="color: #F05D30">Path</span>
POST /odata/Inventory({inventoryId})/InventoryVendor

### <span style="color: #F05D30">Description</span>
Creates a new inventory vendor within a logged organization and specified Inventory.

### <span style="color: #F05D30">Request body</span>
| <div style="width:200px">Parameter</div>|<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**vendorId**: string <br> <span style="color: #F05D30">**required**</span> | Unique Identifier of the Vendor |
|**facilityId**: string <br> <span style="color: #F05D30">**required**</span> | Unique Identifier of the Facility |
|**vendorItemNo**: string <br> <span style="color: #F05D30">**required**</span> | Code that is used by vendor for the Item identification |
|**vendorUOM**: string <br> <span style="color: #F05D30">**required**</span> | Vendor's Unit of Measure |
|**vendorConversionFactor**: integer <br> *(int32)* <br> <span style="color: #F05D30">**required**</span> | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**vendorCost**: number *(double)* <br> <span style="color: #F05D30">**required**</span> | Item Cost of the Vendor |
|**contractNo**: string | Number of Contract |
|**contractExpDate**: string <br> *(date-time)* | Expiration Date of the Contract |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**manufacturerNo**: string | Number of the Manufacturer |
|**ndcNumber**: string | National Drug Code number |
|**lockCost**: boolean | Is the Cost of the Inventory Item Vendor locked or not? |
|**pimKey**: integer *(int10)* | Product Information Management Key |
|**altItemNo**: string | Alternative Item Number |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML<br>Request Example"
{
  "vendorId": "00000000-0000-0000-0000-000000000000",
  "facilityIdd": "00000000-0000-0000-0000-000000000000",
  "vendorItemNo": "string",
  "vendorUOM": "string",
  "vendorConversionFactor": "integer (int32)",
  "VendorCost": "number (double)",
  "contractNo": "string",
  "contractExpDate": "string (date-time)",
  "manufacturerItemNo": "string",
  "manufacturerNo": "string",
  "gtin": "string",
  "ndcNumber": "string",
  "lockCost": "boolean",
  "pimKey": "integer (int10)",
  "altItemNo": "string",
}
```

### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
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

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
"Inventory Vendor is successfully created."
```

## Manage the purchasing option for inventory locations

### <span style="color: #F05D30">Path</span>
POST /odata/Inventory({inventoryId})/ManagePurchasing

### <span style="color: #F05D30">Description</span>
Manages purchasing option for the inventory location specified by inventory ID.

### <span style="color: #F05D30">Request body</span>
| <div style="width:200px">Parameter</div>|<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**disablePurchasing**: boolean | Disable Purchasing for the Inventory Item or not? |
|**facility**: string *(uuid)* | Unique Identifier of the Facility |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML<br>Request Example"
{
  "managePurchasing": {
    "disablePurchasing": "boolean",
     "facility": "00000000-0000-0000-0000-000000000000"
  }
}

```
### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
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


## Save the specified inventory location

### <span style="color: #F05D30">Path</span>
POST /odata/Inventory({inventoryId})/InventoryLocation

### <span style="color: #F05D30">Description</span>
Creates a new inventory location within a logged organization and specified inventory.

### <span style="color: #F05D30">Request body</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**locationId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> | Unique Identifier of the Location |
|**defaultIssueUOM**: string | Unit of Measure used when issuing the Inventory Item |
|**defaultIssueConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure when issuing the Inventory Item |
|**defaultCountUOM**: string | Unit Of Measure used when counting the Inventory Item  |
|**defaultCountConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure when counting the Inventory Item |
|**itemType**: integer *(int8)* | Type of the Item |
|**priceMarkup**: number *(double)* | The dollar or percent amount added to the Inventory Location Cost amount |
|**priceMarkupType**: integer *(int8)* | Type of the Price Markup |
|**cost**: number *(double)* | Cost for the Location |
|**assetLedgerNo**: string | General Ledger Account Code for the Inventory Item at specific Locations |
|**expenseLedgerNo**: string | General Ledger Account Code for the Inventory Expense at the Locations |
|**binShelf**: string | Level of storage within the Location |
|**crossReferenceNo**: string | Number of the Cross Reference |
|**minQuantity**: integer *(int32)* | Minimal Inventory Items Quantity for this Location |
|**maxQuantity**: integer *(int32)* | Prefered Maximum quantity of the Item on the Location |
|**safetyStock**: integer *(int32)* | Level of extra Stock that is maintained to mitigate the risk of stockouts |
|**locationUOM**: string | Unit of Measure of the Location |
|**locationConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Location's Unit of Measure |
|**isBillable**: boolean | Is Location Billable or not? |
|**isTaxable**: boolean | Is Location Taxable or not? |
|**syncFlag**: boolean | Is Inventory Location marked with Synchronization Flag or not? |
|**disablePurchasing**: boolean | Disable or not Purchasing for the Location? |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML<br>Request Example"
{
  "locationId": "00000000-0000-0000-0000-000000000000",
  "defaultIssueUOM": "string",
  "defaultIssueConversionFactor":"integer (int32)",
  "defaultCountUOM": "string",
  "defaultCountConversionFactor": "integer (int32)",
  "itemType":"integer (int8)",
  "priceMarkup": "number (double)",
  "priceMarkupType": "integer (int8)",
  "cost": "number (double)",
  "assetLedgerNo": "string",
  "expenseLedgerNo": "string",
  "binShelf": "string",
  "crossReferenceNo": "string",
  "minQuantity": "integer (int32)",
  "maxQuantity": "integer (int32)",
  "safetyStock": "integer (int32)",
  "locationUOM": "string",
  "locationConversionFactor": "integer (int32)",
  "isBillable": "boolean",
  "isTaxable": "boolean",
  "syncFlag": "boolean",
  "disablePurchasinge": "boolean"
}
```

### <span style="color: #F05D30">Request parameters</span>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory here. |
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

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
"Inventory Location is successfully created."
```