# InventoryTrackings

## Get the specified inventory tracking setting

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryTrackings({inventoryTrackingId})

### <span style="color: #F05D30">Description</span>
Returns the details of the inventory tracking setting specified by ID.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>

|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**inventoryTrackingId**: <br> string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path*  | Enter the ID of the Inventory Tracking here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version. |     
|**Authorization**: string default: <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request. |

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**inventoryTrackingId**: string <br> *(uuid)* | Unique Identifier of the Inventory Item Tracking |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**trackLot**: boolean | Is Tracking performed by Lot Number or not? |
|**trackExpiration**: boolean | Is Tracking performed by Expiration Date or not? |
|**trackSerialNo**: boolean | Is Tracking performed by Serial Number or not? |
|**isOptional**: boolean | Is Tracking optional or not? |
|**dateAdded**: string *(date-time)* | Date when the Inventory Item Tracking was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Inventory Item Tracking |
|**addedByName**: string | Name of the user who added the Inventory Item Tracking |
|**lastUpdated**: string *(date-time)* | Last Date when the Inventory Item Tracking was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated Inventory Item Tracking |
|**lastUpdatedByName**: string | Name of the last user who updated Inventory Item Tracking |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
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
```