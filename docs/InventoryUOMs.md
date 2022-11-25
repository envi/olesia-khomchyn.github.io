# InventoryUOMs
## Get the specified inventory UOM

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryUOMs({inventoryUOMId})

### <span style="color: #F05D30">Description</span>
Returns the details of the inventory UOM specified by ID.

### <span style="color: #F05D30">Request parameters</span>
<style>
td, th {
   border: none!important;
}
</style>

|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**inventoryUOMId**: string *(uuid)*  <br> <span style="color: #F05D30">**required**</span> <br> *in path*  | Enter the ID of the inventory UOM here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version. |     
|**Authorization**: string default: <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**inventoryUOMId**: string *(uuid)* | Unique Identifier of the Inventory Item Unit of Measure |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**uom**: string | Unit of Measure |
|**conversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure |
|**dateAdded**: string *(date-time)* | Date when the Inventory Item Unit of Measure was added |
|**addedId**: string *(uuid)* | Unique Identifier of the user who added the Inventory Item Unit of Measure |
|**lastUpdated**: string *(date-time)* | Last Date when the Inventory Item Unit of Measure was updated |
|**lastUpdatedId**: string *(uuid)* | Unique Identifier of the last user who updated the Inventory Item Unit of Measure |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
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
```