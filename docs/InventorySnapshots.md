# InventorySnapshots
## Get the list of inventory snapshots

### <span style="color: #F05D30">Path</span>
GET /odata/InventorySnapshots

### <span style="color: #F05D30">Description</span>
Returns the list of inventory snapshots within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|     
|**$filter**: string <br> *in query* | Restricts the set of Items returned. The maximum number of expressions is 100.|  
|**$orderby**: string <br> *in query* | Specifies the order in which items are returned. The maximum number of expressions is 5.|
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
|**inventorySnapshotId**: string *(uuid)* |  Unique Identifier of the Inventory Snapshot |
|**organizationId**: string *(uuid)* | Unique Identifier of the Organization |
|**organizationName**: string | Name of the Organization |
|**snapshotDate**: string *(date-time)* | Date when the Snapshot was created |
|**reference**: string | Information concerning the Snapshot |
|**dateCreated**: string *(date-time)* | Date when the Snapshot was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Snapshot |
|**createdByName**: string | Name of the user who created the Snapshot |
|**isFiltered**: boolean *(uuid)* | Is the data for Inventory Snapshot filtered or not? |
|**isAutoExecuted**: boolean | Is the Inventory Snapshot autoexecuted or not? |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "inventorySnapshotId": "00000000-0000-0000-0000-000000000000",
      "organizationId": "00000000-0000-0000-0000-000000000000",
      "organizationName": "string",
      "snapshotDate": "string (date-time)",
      "reference": "string",
      "dateCreated": "string (date-time)",
      "createdBy": "00000000-0000-0000-0000-000000000000",
      "createdByName": "string",
      "isFiltered": "boolean",
      "isAutoExecuted": "boolean"
    }
  ],
"nextPageLink": "string",
"count": "integer (int64)"
}
```

## Get the specified inventory snapshot

### <span style="color: #F05D30">Path</span>
GET /odata/InventorySnapshots({inventorySnapshotId})

### <span style="color: #F05D30">Description</span>
Returns the details of the inventory snapshot specified by ID.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**inventorySnapshotId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path*  | Enter the ID of the Inventory Snapshot here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version. |     
|**Authorization**: string default: <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |

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
|**inventorySnapshotId**: string *(uuid)* |  Unique Identifier of the Inventory Snapshot |
|**organizationId**: string *(uuid)* | Unique Identifier of the Organization |
|**organizationName**: string | Name of the Organization |
|**snapshotDate**: string *(date-time)* | Date when the Snapshot was created |
|**reference**: string | Information concerning the Snapshot |
|**dateCreated**: string *(date-time)* | Date when the Snapshot was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Snapshot |
|**createdByName**: string | Name of the user who created the Snapshot |
|**isFiltered**: boolean *(uuid)* | Is the data for Inventory Snapshot filtered or not? |
|**isAutoExecuted**: boolean | Is the Inventory Snapshot autoexecuted or not? |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "inventorySnapshotId": "00000000-0000-0000-0000-000000000000",
  "organizationId": "00000000-0000-0000-0000-000000000000",
  "organizationName": "string",
  "snapshotDate": "string (date-time)",
  "reference": "string",
  "dateCreated": "string (date-time)",
  "createdBy": "00000000-0000-0000-0000-000000000000",
  "createdByName": "string",
  "isFiltered": "boolean",
  "isAutoExecuted": "boolean"
}
```

## Get the list of inventory snapshot items for specific inventory snapshot

### <span style="color: #F05D30">Path</span>
GET /odata/InventorySnapshots({inventorySnapshotId})/inventorySnapshotItems

### <span style="color: #F05D30">Description</span>
Returns the list of items of the inventory snapshot specified by ID within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**inventorySnapshotId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path*  | Enter the ID of the Inventory Snapshot here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|     
|**$filter**: string <br> *in query* | Restricts the set of Items returned. The maximum number of expressions is 100.|  
|**$orderby**: string <br> *in query* | Specifies the order in which items are returned. The maximum number of expressions is 5.|
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
|**inventorySnapshotItemId**: <br> string *(uuid)* | Unique Identifier of the Inventory Snapshot Item |
|**inventorySnapshotId**: string *(uuid)* |  Unique Identifier of the Inventory Snapshot |
|**reference**: string | Information concerning the Inventory Snapshot |
|**inventoryId**: string *(uuid)*  | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**inventoryDescription**: string | Description of the Inventory Item |
|**inventoryLocationId**: string *(uuid)* | Unique Identifier of the Inventory Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**cost**: number *(double)* | Cost for the Inventory Item |
|**quantity**: integer *(int32)* | Quantity on hand of the Inventory Location when the Inventory Snapshot was created |
|**itemTypeId**: integer *(int32)* | Unique identifier of the Item type |
|**itemTypeName**: string | Name of the Item type |
|**dateCreated**: string <br> *(date-time)* | Date when the Inventory Snapshot Item was created |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
 "items": [
 {
  "inventorySnapshotItemId": "00000000-0000-0000-0000-000000000000",
  "inventorySnapshotId": "00000000-0000-0000-0000-000000000000",
  "reference": "string",
  "inventoryId": "00000000-0000-0000-0000-000000000000",
  "inventoryNo": "string",
  "inventoryDescription": "string",
  "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
  "locationNo": "string",
  "locationName": "string",
  "cost": "number (double)",
  "quantity": "integer (int32)",
  "itemTypeId": "integer (int32)",
  "itemTypeName": "string",
  "dateCreated": "string (date-time)"
 }
 ],
"nextPageLink": "string",
"count": "integer (int64)"
}
```




