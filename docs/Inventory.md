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
Returns the paged list of the existing future pricing items within inventory specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter – contains(entity, ‘string’).

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