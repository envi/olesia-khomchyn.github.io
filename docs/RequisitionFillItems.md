# RequisitionFillItems

## Get the list of Requisition Fill Items

### <span style="color: #F05D30">Path</span>
GET /odata/RequisitionFillItems

### <span style="color: #F05D30">Description</span>
Returns the list of Requisition Fill Items from Fill Requisitions within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).


### <span style="color: #F05D30">Request parameters</span>
<style>
td, th {
   border: none!important;
}
</style>


|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.| 
|**$filter**: string <br> *in query* | Restricts the set of items returned. The maximum number of expressions is 100. | 
|**$orderby**: string <br> *in query* | Specifies the order in which items are returned. The maximum number of expressions is 5. | 
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|


### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|      
|**400 Bad Request** | The limit for the ```$top``` query has been exceeded. The value from the incoming request is 'N' (N is your value from the request). You can find the data on the current limit [here](Options_and_Limitations.md#top-and-skip).
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|


### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**requisitionFillItemId**: string *(uuid)* | Unique Identifier of the Requisition Fill Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**requisitionFillId**: string *(uuid)* | Unique Identifier of the Requisition Fill |
|**requisitionFillNo**: string | Identification code of the Requisition Fill |
|**requisitionItemId**: string *(uuid)* | Unique Identifier of the Requisition Item |
|**receiptItemId**: string *(uuid)* | Unique Identifier of the Receipt Item |
|**lotNo**: string | Identification Number assigned to a particular Quantity or Lot of material from a single Manufacturer |
|**serialNo**: string | Unique Identifier assigned incrementally or sequentially to an Item to uniquely identify it |
|**expDate**: string *(date-time)* | Previously determined date after which Item should no longer be used |
|**notes**: string | Comments about the Requisition Fill |
|**fillQuantity**: integer *(int32)* | Quantity specified in the Requisition Fill |
|**fillUOM**: string | Unit of Measure specified in the Requisition Fill |
|**fillConversionFactor**: integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure specified in the Requisition Fill |
|**dateCreated**: string *(date-time)* | Date when the Requisition Fill Item was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Requisition Fill Item |
|**createdByName**: string | Name of the user who created the Requisition Fill Item |
|**lastUpdated**: string *(date-time)* | Last Date when the Requisition Fill Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Requisition Fill Item |
|**lastUpdatedByName**: string | Name of the last user who updated the Requisition Fill Item |
|**unitCost**: number *(double)* | Cost of the one unit of the Requisition Fill Item |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "requisitionFillItemId": "00000000-0000-0000-0000-000000000000",
      "inventoryNo": "string",
      "requisitionFillId": "00000000-0000-0000-0000-000000000000",
      "requisitionFillNo": "string",
      "requisitionItemId": "00000000-0000-0000-0000-000000000000",
      "receiptItemId": "00000000-0000-0000-0000-000000000000",
      "lotNo": "string",
      "serialNo": "string",
      "expDate": "string (date-time)",
      "notes": "string",
      "fillQuantity": "integer (int32)",
      "fillUOM": "string",
      "fillConversionFactor": "integer (int32)",
      "dateCreated": "string (date-time)",
      "createdBy": "00000000-0000-0000-0000-000000000000",
      "createdByName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByName": "string",
      "unitCost": "number (double)",
      }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```

## Get the specified Requisition Fill Item

### <span style="color: #F05D30">Path</span>
GET /odata/RequisitionFillItems({requisitionFillItemId})

### <span style="color: #F05D30">Description</span>
Returns the details of the Requisition Fill Item specified by ID within a logged organization.


### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**requisitionFillItemId**: string *(uuid)* <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Requisition Fill Item here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version. |   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |


### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**404 Not Found** | Specified ID is absent in the system. |
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request. |


### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**requisitionFillItemId**: string *(uuid)* | Unique Identifier of the Requisition Fill Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**requisitionFillId**: string *(uuid)* | Unique Identifier of the Requisition Fill |
|**requisitionFillNo**: string | Identification code of the Requisition Fill |
|**requisitionItemId**: string *(uuid)* | Unique Identifier of the Requisition Item |
|**receiptItemId**: string *(uuid)* | Unique Identifier of the Receipt Item |
|**lotNo**: string | Identification Number assigned to a particular Quantity or Lot of material from a single Manufacturer |
|**serialNo**: string | Unique Identifier assigned incrementally or sequentially to an Item to uniquely identify it |
|**expDate**: string *(date-time)* | Previously determined date after which Item should no longer be used |
|**notes**: string | Comments about the Requisition Fill |
|**fillQuantity**: integer *(int32)* | Quantity specified in the Requisition Fill |
|**fillUOM**: string | Unit of Measure specified in the Requisition Fill |
|**fillConversionFactor**: integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure specified in the Requisition Fill |
|**dateCreated**: string *(date-time)* | Date when the Requisition Fill Item was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Requisition Fill Item |
|**createdByName**: string | Name of the user who created the Requisition Fill Item |
|**lastUpdated**: string *(date-time)* | Last Date when the Requisition Fill Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Requisition Fill Item |
|**lastUpdatedByName**: string | Name of the last user who updated the Requisition Fill Item |
|**unitCost**: number *(double)* | Cost of the one unit of the Requisition Fill Item |



``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "requisitionFillItemId": "00000000-0000-0000-0000-000000000000",
  "inventoryNo": "string",
  "requisitionFillId": "00000000-0000-0000-0000-000000000000",
  "requisitionFillNo": "string",
  "requisitionItemId": "00000000-0000-0000-0000-000000000000",
  "receiptItemId": "00000000-0000-0000-0000-000000000000",
  "lotNo": "string",
  "serialNo": "string",
  "expDate": "string (date-time)",
  "notes": "string",
  "fillQuantity": "integer (int32)",
  "fillUOM": "string",
  "fillConversionFactor": "integer (int32)",
  "dateCreated": "string (date-time)",
  "createdBy": "00000000-0000-0000-0000-000000000000",
  "createdByName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByName": "string",
  "unitCost": "number (double)",
}
```
