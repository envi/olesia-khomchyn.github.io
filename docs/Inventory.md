# Inventory

## Get the list of inventory items

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing inventory within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**api-version**: string defaul:t 1.0 <br> *in header*| The requested API version.|      
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition.|
|**$orderby**: string <br> *in query* | Sorts the results.|
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

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
| <div style="width:200px">Property </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryId**: string *(uuid)*| Unique Identifier of the Inventory Item|
|**organizationId**: string *(uuid)*| Unique Identifier of the Organization|
|**organizationName**: string | Name of the Organization|
|**inventoryGroupId**: string| Unique Identifier of the Group that contains related Inventory Items |
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
          "systemType": "string"
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

### <span style="color: #F05D30">Request Body</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> | Unique Identifier of the Inventory Item|
|**organizationId**: string *(uuid)*| Unique Identifier of the Organization|
|**organizationName**: string | Name of the Organization|
|**inventoryGroupId**: string| Unique Identifier of the Group that contains related Inventory Items |
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

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
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

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the inventory here. |
|**api-version**: string defaul:t 1.0 <br> *in header*| The requested API version.|      
|**Authorization**: string <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|


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
| <div style="width:200px">Property</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryId**: string *(uuid)*| Unique Identifier of the Inventory Item|
|**organizationId**: string *(uuid)*| Unique Identifier of the Organization|
|**organizationName**: string | Name of the Organization|
|**inventoryGroupId**: string| Unique Identifier of the Group that contains related Inventory Items |
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

### <span style="color: #F05D30">Request Body</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryId**: string *(uuid)*| Unique Identifier of the Inventory Item|
|**organizationId**: string *(uuid)*| Unique Identifier of the Organization|
|**organizationName**: string | Name of the Organization|
|**inventoryGroupId**: string| Unique Identifier of the Group that contains related Inventory Items |
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
### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the inventory here. |
|**api-version**: string defaul:t 1.0 <br> *in header*| The requested API version.|      
|**Authorization**: string <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

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

## Partially update the specified inventory

### <span style="color: #F05D30">Path</span>
PATCH /odata/Inventory({inventoryId})

### <span style="color: #F05D30">Description</span>
Partially updates the details of the inventory specified by ID.

### <span style="color: #F05D30">Request Body</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item|
|**organizationId**: string *(uuid)*| Unique Identifier of the Organization|
|**organizationName**: string | Name of the Organization|
|**inventoryGroupId**: string| Unique Identifier of the Group that contains related Inventory Items |
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
      "systemType": "string"
      "defaultIsBillable": "boolean"
    }
```
### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the inventory here. |
|**api-version**: string defaul:t 1.0 <br> *in header*| The requested API version.|      
|**Authorization**: string <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|


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

## Get future pricing items for the specified inventory

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory({inventoryId})/futurePricing

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing future pricing items within inventory specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.


### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the inventory here. |
|**api-version**: string defaul:t 1.0 <br> *in header*| The requested API version.|      
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition.|
|**$orderby**: string <br> *in query* | Sorts the results.|
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

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
| <div style="width:200px">Property</div>|<div style="width:380px">Explanation</div>|                      
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


### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the inventory here. |
|**api-version**: string defaul:t 1.0 <br> *in header*| The requested API version.|      
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition.|
|**$orderby**: string <br> *in query* | Sorts the results.|
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|


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

## Get the list of inventory locations for the specified inventory

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory({inventoryId})/inventoryLocations

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing inventory locations within inventory specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the inventory here. |
|**api-version**: string defaul:t 1.0 <br> *in header*| The requested API version.|      
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition.|
|**$orderby**: string <br> *in query* | Sorts the results.|
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|


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
|**disablePurchasing**: boolean | Disable or not Purchasing for the Location |
|**minQuantity**: integer (int32) | Minimal Inventory Items Quantity for this Location |
|**onRequisition**: integer (int32) | Quantity of Inventory items for Requisition |
|**maxQuantity**: integer (int32) | Maximal Inventory Items Quantity for this Location |
|**safetyStock**: integer (int32) | Level of extra Stock that is maintained to mitigate risk of stockouts |
|**binShelf**: string | Level of storage within the Location |
|**assetLedgerNo**: string | General Ledger Account Code for the Inventory Asset at the Locations |
|**expenseLedgerNo**: string | General Ledger Account Code for the Inventory Expense at the locations |
|**syncFlag**: boolean | Is Inventory Location marked with Synchronization Flag or not? |
|**costLastUpdated**: string *(date-time)* | Last Date when the Cost was updated |
|**costLastUpdatedBy**: string (uuid) | Unique Identifier of the last user who updated the Cost |
|**dateAdded**: string *(date-time)* | Date when the Inventory Location was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the last user who added Location |
|**lastUpdated**: string *(date-time)* | Date of last Location update |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated Location |
|**activeStatus**: boolean | Is Location active or not |
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

## Get the list of tracking settings for specified inventory

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory({inventoryId})/inventoryTrackings

### <span style="color: #F05D30">Description</span>
Returns paged the list of the existing inventory tracking settings within inventory specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.
    


### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Parameter</div>|<div style="width:380px">Explanation</div>|                       
|-----:|:-------|
|**inventoryId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the inventory here. |
|**api-version**: string defaul:t 1.0 <br> *in header*| The requested API version.|      
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition.|
|**$orderby**: string <br> *in query* | Sorts the results.|
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

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
| <div style="width:200px">Property</div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------| 
|**inventoryTrackingId**: string *(uuid)* | Unique Identifier of the Inventory Item Tracking |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**trackLot**: boolean | Is Tracking performed by Lot number or not? |
|**trackExpiration**: boolean | Is Tracking performed by Expiration Date or not? |
|**trackSerialNo**: boolean | Is Tracking performed by Serial number or not? |
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