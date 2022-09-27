# InventoryVendors
## Get the cost history for specified inventory vendor

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryVendors({inventoryVendorId})/costHistory

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing cost history records within inventory vendor specified by ID.

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**inventoryVendorId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory Vendor here.|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition. |  
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

## <span style="color: #F05D30">Properties</span>
<style>
td, th {
   border: none!important;
}
</style>
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**inventoryVendorCostHistoryId**: <br> string *(uuid)* | Unique Identifier of the Inventory Vendor Cost History |
|**inventoryVendorId**: string *(uuid)* | Unique Identifier of the Inventory Vendor |
|**vendorName**: string | Name of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**inventoryVendorCostId**: <br> string *(uuid)*  | Unique Identifier of the Inventory Vendor Cost |
|**vendorCost**: number *(double)* | Cost of the Vendor |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**costUpdated**: string *(date-time)* | Last Date when the Cost was updated |
|**costUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Cost |
|**costUpdatedByName**: string | Name of the last user who updated the Cost |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
      "items": [
        {
          "inventoryVendorCostHistoryId": "00000000-0000-0000-0000-000000000000",
          "inventoryVendorId": "00000000-0000-0000-0000-000000000000",
          "vendorName": "string",
          "vendorNo": "string",
          "inventoryVendorCostId": "00000000-0000-0000-0000-000000000000",
          "vendorCost": "number (double)",
          "vendorUOM": "string",
          "vendorConversionFactor": "integer (int32)",
          "costUpdated": "string (date-time)",
          "costUpdatedBy": "00000000-0000-0000-0000-000000000000",
          "costUpdatedByName": "string"
        }
      ],
      "nextPageLink": "string",
      "count": "integer (int64)"
    }
```

## Get the list of purchasing units for specified inventory vendor

### <span style="color: #F05D30">Path</span>
GET /odata/InventoryVendors({inventoryVendorId})/purchasingUnits

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing purchasing units within inventory vendor specified by ID.

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.


### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**inventoryVendorId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Inventory Vendor here.|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition. |  
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

## <span style="color: #F05D30">Properties</span>
<style>
td, th {
   border: none!important;
}
</style>
|<div style="width:200px">Property </div> |<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**inventoryVendorPurchasing<br>UnitId**: <br> string *(uuid)* | Unique Identifier of the Inventory Vendor Purchasing Unit |
|**inventoryVendorId**: string *(uuid)* | Unique Identifier of the Inventory Vendor |
|**vendorName**: string | Name of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**vendorCost**: number *(double)* | Cost of the Vendor |
|**activeStatus**: boolean | Is the status of Purchasing Unit active or not? |
|**lastVendorCost**: number *(double)* | Last Cost of the Vendor |
|**costLastUpdated**: string <br> *(date-time)* | Last Date when the Cost was updated |
|**costLastUpdatedBy**: <br> string *(uuid)* | Unique Identifier of the last user who updated the Cost |
|**costLastUpdatedByName**: <br> string | Name of the last user who updated the Cost |
|**dateAdded**: string *(date-time)* | Date when the Purchasing Unit was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Purchasing Unit |
|**addedByName**: string | Name of the last user who added the Purchasing Unit |
|**lastUpdated**: string *(date-time)* | Last Date when the Purchasing Unit was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Purchasing Unit |
|**lastUpdatedByName**: string | Name of the last user who updated the Purchasing Unit |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
      "items": [
        {
          "inventoryVendorPurchasingUnitId": "00000000-0000-0000-0000-000000000000",
          "inventoryVendorId": "00000000-0000-0000-0000-000000000000",
          "vendorName": "string",
          "vendorNo": "string",
          "vendorUOM": "string",
          "vendorConversionFactor": "integer (int32)",
          "vendorCost": "number (double)",
          "activeStatus": "boolean",
          "lastVendorCost": "number (double)",
          "costLastUpdated": "string (date-time)",
          "costLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
          "costLastUpdatedByName": "string",
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

