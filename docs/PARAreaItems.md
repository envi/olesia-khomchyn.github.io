# PARAreaItems

## Get the list of PAR Area items

### <span style="color: #F05D30">Path</span>
GET /odata/parAreaLineItems

### <span style="color: #F05D30">Description</span>
Returns the list of PAR Area items within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request Parameters</span>
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
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
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
|**parAreaItemId**: string *(uuid)* | Unique Identifier of the PAR Area Item |
|**parAreaId**: string *(uuid)* | Unique Identifier of the PAR Area |
|**parAreaNo**: string | Identification Number of the PAR Area |
|**parAreaName**: string | Name of the PAR Area |
|**inventoryLocationId**: string *(uuid)* | Unique Identifier of the Inventory Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**lineItemNo**: integer *(int32)* | Number of the Line Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**inventoryDescription**: string | Description of the Inventory Item |
|**notes**: string | Comments about the PAR Area Item |
|**minQuantity**: integer <br> *(int32)*  | Minimal Items Quantity for this PAR Area |
|**maxQuantity**: integer <br> *(int32)* | Maximal Items Quantity for this PAR Area |
|**uom**: string | Unit of Measure |
|**conversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure |
|**binShelf**: string | Level of storage within PAR Area |
|**lastCountDate**: string <br> *(date-time)* | Date when last PAR Count was created for this PAR Area Item |
|**gtin**: string | Global Trade Item Number |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**activeStatus**: boolean | Is the status of the PAR Area Item active or not? |
|**dateCreated**: string <br> *(date-time)* | Date when PAR Area Item the was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the PAR Area Item |
|**createdByName**: string | First Name and Last Name of the user who added PAR Area Item |
|**lastUpdated**: string *(date-time)* | Last Date when the PAR Area Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the PAR Area Item |
|**lastUpdatedByName**: string | First Name and Last Name of the last user who updated the PAR Area Item |



``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "parAreaItemId": "00000000-0000-0000-0000-000000000000",
      "parAreaId": "00000000-0000-0000-0000-000000000000",
      "parAreaNo": "string",
      "parAreaName": "string",
      "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
      "locationNo": "string",
      "locationName": "string",
      "lineItemNo": "integer (int32)",
      "inventoryNo": "string",
      "inventoryDescription": "string",
      "notes": "string",
      "minQuantity": "integer (int32)",
      "maxQuantity": "integer (int32)",
      "uom": "string",
      "conversionFactor": "integer (int32)",
      "binShelf": "string",
      "lastCountDate": "string (date-time)",
      "gtin": "string",
      "manufacturerItemNo": "string",
      "activeStatus": "boolean",
      "dateCreated": "string (date-time)",
      "createdBy": "00000000-0000-0000-0000-000000000000",
      "createdByName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByName": "string"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```

## Get the specified PAR Area Item

### <span style="color: #F05D30">Path</span>
GET /odata/parAreaLineItems({parAreaItemId})

### <span style="color: #F05D30">Description</span>
Returns the details of the PAR Area item specified by ID.

### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**parAreaItemId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the PAR Area Item here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |

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
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**parAreaItemId**: string *(uuid)* | Unique Identifier of the PAR Area Item |
|**parAreaId**: string *(uuid)* | Unique Identifier of the PAR Area |
|**parAreaNo**: string | Identification Number of the PAR Area |
|**parAreaName**: string | Name of the PAR Area |
|**inventoryLocationId**: string *(uuid)* | Unique Identifier of the Inventory Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**lineItemNo**: integer *(int32)* | Number of the Line Item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**inventoryDescription**: string | Description of the Inventory Item |
|**notes**: string | Comments about the PAR Area Item |
|**minQuantity**: integer <br> *(int32)*  | Minimal Items Quantity for this PAR Area |
|**maxQuantity**: integer <br> *(int32)* | Maximal Items Quantity for this PAR Area |
|**uom**: string | Unit of Measure |
|**conversionFactor**: integer <br> *(int32)* | Number of Stock Keeping Units in another Unit of Measure |
|**binShelf**: string | Level of storage within PAR Area |
|**lastCountDate**: string <br> *(date-time)* | Date when last PAR Count was created for this PAR Area Item |
|**gtin**: string | Global Trade Item Number |
|**manufacturerItemNo**: string | Item Number of the Manufacturer |
|**activeStatus**: boolean | Is the status of the PAR Area Item active or not? |
|**dateCreated**: string <br> *(date-time)* | Date when PAR Area Item the was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the PAR Area Item |
|**createdByName**: string | First Name and Last Name of the user who added PAR Area Item |
|**lastUpdated**: string *(date-time)* | Last Date when the PAR Area Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the PAR Area Item |
|**lastUpdatedByName**: string | First Name and Last Name of the last user who updated the PAR Area Item |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "parAreaItemId": "00000000-0000-0000-0000-000000000000",
  "parAreaId": "00000000-0000-0000-0000-000000000000",
  "parAreaNo": "string",
  "parAreaName": "string",
  "inventoryLocationId": "00000000-0000-0000-0000-000000000000",
  "locationNo": "string",
  "locationName": "string",
  "lineItemNo": "integer (int32)",
  "inventoryNo": "string",
  "inventoryDescription": "string",
  "notes": "string",
  "minQuantity": "integer (int32)",
  "maxQuantity": "integer (int32)",
  "uom": "string",
  "conversionFactor": "integer (int32)",
  "binShelf": "string",
  "lastCountDate": "string (date-time)",
  "gtin": "string",
  "manufacturerItemNo": "string",
  "activeStatus": "boolean",
  "dateCreated": "string (date-time)",
  "createdBy": "00000000-0000-0000-0000-000000000000",
  "createdByName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByName": "string"
}  
```