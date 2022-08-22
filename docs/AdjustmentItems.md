# AdjustmentItems
## Get the specified adjustment item

### <span style="color: #F05D30">Path</span>
GET /odata/AdjustmentItems({adjustmentItemId})

### <span style="color: #F05D30">Description</span>
Returns the details of the adjustment item specified by ID.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> Parameter </div> |<div style="width:380px">Explanation</div> |                      
|-----:|:-------|
|**addressId**: string (uuid) <br> <span style="color: #F05D30">**required**</span> <br> *in path*| Enter the ID of the address here.|
|**adjustmentItemId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path*| Enter the ID of the Adjustment Item here.|
|**api-version**: string 1.0 <br> *in header* | The requested API version. |
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
|**400 Bad Request**|Incorrect input data or organization ID does not match with organization ID user is logged in.|
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
|**adjustmentItemId**: string *(uuid)* | Unique Identifier of the Adjustment Item |
|**adjustmentId**: string *(uuid* | Unique Identifier of the Adjustment |
|**inventoryLocationId**: string *(uuid)* | Unique Identifier of the Inventory Location |
|**notes**: string |Comments about the Adjustment Item |
|**lotNo**: string |Identification number assigned to a particular quantity or lot of material from a single manufacturer |
|**serialNo**: string | Unique Identifier assigned incrementally or sequentially to an item, to identify it |
|**expDate**: string *(date-time)* | Previously determined date after which item should no longer be used |
|**dateCreated**: string *(date-time)* | Date when the Adjustment Item was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Adjustment Item |
|**createdByName**: string | Name of the user who created the Adjustment Item |
|**lastUpdated**: string *(date-time)* | Last Date when the Adjustment Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Adjustment Item |
|**lastUpdatedByName**: string | Name of the last user who updated the Adjustment Item |
|**lineNo**: integer *(int32)* | Sequence number of the Adjustment Item in the Line Items list |
|**facilityName**: string | Name of the Facility |
|**locationName**: string | Name of the Location |
|**dateSubmitted**: string *(date-time)* | Date when the Adjustment Item was submitted |
|**inventoryNo**: string | Identification code of the Inventory item |
|**inventoryDescription**: string | Description of the Inventory item |
|**classificationName**: string | Name of the Category of the item defined on the Organization level |
|**vendorName**: string | Name of the Vendor |
|**vendorItemNo**: string | Code that is used by vendor for the item identification |
|**quantity**: integer *(int32)* | Quantity specified in the Line Items |
|**impactQuantity**: integer *(int32)* | Unit that is used for differentiation of the quantity change |
|**uom**: string | Unit of Measure |
|**conversionFactor**: integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure |
|**adjustmentTypeText**: string | Type of transaction: Increment, Decrement, or Overwrite |
|**unitCost**: number *(double)* | Cost of the one unit of the Adjustment Item |
|**extendedCost**: number *(double)* | Total Cost of the Line |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML <br> Response Example (200 OK)"
{
        "adjustmentItemId": "00000000-0000-0000-0000-000000000000",
        "adjustmentId": "00000000-0000-0000-0000-000000000000",
        "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
        "notes": "string",
        "lotNo": "string",
        "serialNo": "string",
        "expDate": "string (date-time)",
        "dateCreated": "string (date-time)",
        "createdBy": "00000000-0000-0000-0000-000000000000",
        "createdByName": "string",
        "lastUpdated": "string (date-time)",
        "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
        "lastUpdatedByName": "string",
        "lineNo": "integer (int32)",
        "facilityName": "string",
        "locationName": "string",
        "dateSubmitted": "string (date-time)",
        "inventoryNo": "string",
        "inventoryDescription": "string",
        "classificationName": "string",
        "vendorName": "string",
        "vendorItemNo": "string",
        "quantity": "integer (int32)",
        "impactQuantity": "integer (int32)",
        "uom": "string",
        "conversionFactor": "integer (int32)",
        "adjustmentTypeText": "string",
        "unitCost": "number (double)",
        "extendedCost": "number (double)"
      }      
```

## Get list of adjustment items

### <span style="color: #F05D30">Path</span>
GET /odata/AdjustmentItems

### <span style="color: #F05D30">Description</span>
Returns paged list of the existing items within all adjustments. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

!!! note
    
    This endpoint does not support logical operators (**and**, **or**, **in**, **gt**, **ge**, **lt**, **le**) for data filtering.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:420px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default 1.0 <br> *in header*|The requested API version.|      
|**from**: string *(date-time)* <br> *in query* | Enter the start date here. |
|**to**: string *(date-time)* <br> *in query* | Enter the end date here. |
|**api-version**: string default 1.0 <br> *in header*|The requested API version.|      
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
|**$filter**: string <br> *in query* | Filters the results, based on the Boolean condition.|
|**$orderby**: string <br> *in query* | Sorts the results.|
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**|Incorrect input data or organization ID does not match with organization ID user is logged in.|
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
|**adjustmentItemId**: string *(uuid)* | Unique Identifier of the Adjustment Item |
|**adjustmentId**: string *(uuid* | Unique Identifier of the Adjustment |
|**inventoryLocationId**: string *(uuid)* | Unique Identifier of the Inventory Location |
|**notes**: string |Comments about the Adjustment Item |
|**lotNo**: string |Identification number assigned to a particular quantity or lot of material from a single manufacturer |
|**serialNo**: string | Unique Identifier assigned incrementally or sequentially to an item, to identify it |
|**expDate**: string *(date-time)* | Previously determined date after which item should no longer be used |
|**dateCreated**: string *(date-time)* | Date when the Adjustment Item was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Adjustment Item |
|**createdByName**: string | Name of the user who created the Adjustment Item |
|**lastUpdated**: string *(date-time)* | Last Date when the Adjustment Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Adjustment Item |
|**lastUpdatedByName**: string | Name of the last user who updated the Adjustment Item |
|**lineNo**: integer *(int32)* | Sequence number of the Adjustment Item in the Line Items list |
|**facilityName**: string | Name of the Facility |
|**locationName**: string | Name of the Location |
|**dateSubmitted**: string *(date-time)* | Date when the Adjustment Item was submitted |
|**inventoryNo**: string | Identification code of the Inventory item |
|**inventoryDescription**: string | Description of the Inventory item |
|**classificationName**: string | Name of the Category of the item defined on the Organization level |
|**vendorName**: string | Name of the Vendor |
|**vendorItemNo**: string | Code that is used by vendor for the item identification |
|**quantity**: integer *(int32)* | Quantity specified in the Line Items |
|**impactQuantity**: integer *(int32)* | Unit that is used for differentiation of the quantity change |
|**uom**: string | Unit of Measure |
|**conversionFactor**: integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure |
|**adjustmentTypeText**: string | Type of transaction: Increment, Decrement, or Overwrite |
|**unitCost**: number *(double)* | Cost of the one unit of the Adjustment Item |
|**extendedCost**: number *(double)* | Total Cost of the Line |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML <br> Response Example (200 OK)"
{
        "items": [
          {
            "adjustmentItemId": "00000000-0000-0000-0000-000000000000",
            "adjustmentId": "00000000-0000-0000-0000-000000000000",
            "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
            "notes": "string",
            "lotNo": "string",
            "serialNo": "string",
            "expDate": "string (date-time)",
            "dateCreated": "string (date-time)",
            "createdBy": "00000000-0000-0000-0000-000000000000",
            "createdByName": "string",
            "lastUpdated": "string (date-time)",
            "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
            "lastUpdatedByName": "string",
            "lineNo": "integer (int32)",
            "facilityName": "string",
            "locationName": "string",
            "dateSubmitted": "string (date-time)",
            "inventoryNo": "string",
            "inventoryDescription": "string",
            "classificationName": "string",
            "vendorName": "string",
            "vendorItemNo": "string",
            "quantity": "integer (int32)",
            "impactQuantity": "integer (int32)",
            "uom": "string",
            "conversionFactor": "integer (int32)",
            "adjustmentTypeText": "string",
            "unitCost": "number (double)",
            "extendedCost": "number (double)"
          }
        ],
        "nextPageLink": "string",
        "count": "integer (int64)"
      }  
```



