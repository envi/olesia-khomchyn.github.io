# UsageItems

## Get the list of usage items

### <span style="color: #F05D30">Path</span>
GET /odata/UsageItems

### <span style="color: #F05D30">Description</span>
Returns the paged list of existing items within all usages. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

!!! note 

    This endpoint does not support logical operators (**and**, **or**, **in**, **gt**, **ge**, **lt**, **le**) for data filtering.


### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**summary**: string default: false <br> *in query* | Set to **true** if you want to apply Grouping. |
|**from**: string *(date-time)* <br> *in query* | Enter the start date here. |
|**to**: string *(date-time)* <br> *in query* | Enter the end date here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.| 
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition. | 
|**$orderby**: string <br> *in query* | Sorts the results. | 
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|      
|**400 Bad Request** | The limit for the ```$top``` query has been exceeded. The value from the incoming request is 'N' (N is your value from the request). You can find the data on the current limit [here](Options_and_Limitations.md#top-and-skip).
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Properties</span>
<style>
td, th {
   border: none!important;
}
</style>
|<div style="width:200px">Property </div> |<div style="width:450px">Explanation</div>|                      
|-----:|:-------|
|**usageItemId**: string *(uuid)* | Unique Identifier of the Usage |
|**procedureCode1**: string | First Code of the Procedure |
|**procedureName1**: string | First Name of the Procedure |
|**procedureCode2**: string | Second Code of the Procedure |
|**procedureName2**: string | Second Name of the Procedure |
|**procedure1Id**: string *(uuid)* | Unique Identifier of the first Procedure |
|**procedure2Id**: string *(uuid)* | Unique Identifier of the second Procedure |
|**date**: string *(date-time)* | Usage Date |
|**caseNo**: string | Number of the Case |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**departmentName**: string | Name of the Department |
|**departmentId**: string *(uuid)* | Unique Identifier of the Department |
|**extendedPrice**: number *(double)* | Extended Price |
|**cost**: number *(double)* | Cost |
|**extendedCost**: number *(double)* | Extended Cost |
|**patient**: string | Patient Details |
|**facilityName**: string | Name of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**doctorName**: string | Name of the Doctor |
|**doctorId**: string *(uuid)* | Unique Identifier of the Doctor |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**inventoryDescription**: string | Description of the Inventory Item |
|**classification**: string | Category of the Item defined on the Organization level |
|**classification2**: string | Additional Category of the Item defined on the Organization level |
|**quantity**: integer *(int32)* | Quantity of the Usage Item |
|**uom**: string | Unit of Measure |
|**price**: number *(double)* | Price of the Usage Item |
|**conversionFactor**: integer *(int32)* | Number of Stock Keeping Units in another Unit of Measure |
|**locationNo**: string | Identification Number of the Location |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**manufacturerNo**: string | Number of the Manufacturer |
|**manufacturerItemNo**: string | Number of the Manufacturer Item |
|**lotNo**: string | Identification Number assigned to a particular Quantity or Lot of material from a single Manufacturer |
|**serialNo**: string | Unique Identifier assigned incrementally or sequentially to an Item to uniquely identify it |
|**expirationDate**: string <br> *(date-time)* | Previously determined date after which Item should no longer be used |
|**itemNotes**: string | Comments about the Item |
|**lineNo**: integer *(int32)* | Number of the Line |
|**usageOrdinalNo**: integer *(int32)* | Ordinal Number of the Usage |
|**usageId**: string (uuid) | Unique Identifier of the Usage |
|**usageNo**: string | Identification Number of the Location |
|**dateSubmitted**: string *(date-time)* | Date when Usage was submitted |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
"items": [
{
  "usageItemId": "00000000-0000-0000-0000-000000000000",
  "procedureCode1": "string",
  "procedureName1": "string",
  "procedureCode2": "string",
  "procedureName2": "string",
  "procedure1Id": "00000000-0000-0000-0000-000000000000",
  "procedure2Id": "00000000-0000-0000-0000-000000000000",
  "date": "string (date-time)",
  "caseNo": "string",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "departmentName": "string",
  "departmentId": "00000000-0000-0000-0000-000000000000",
  "extendedPrice": "number (double)",
  "cost": "number (double)",
  "extendedCost": "number (double)",
  "patient": "string",
  "facilityName": "string",
  "facilityNo": "string",
  "doctorName": "string",
  "doctorId": "00000000-0000-0000-0000-000000000000",
  "vendorItemNo": "string",
  "inventoryDescription": "string",
  "classification": "string",
  "classification2": "string",
  "quantity": "integer (int32)",
  "uom": "string",
  "price": "number (double)",
  "conversionFactor": "integer (int32)",
  "locationNo": "string",
  "inventoryNo": "string",
  "manufacturerNo": "string",
  "manufacturerItemNo": "string",
  "lotNo": "string",
  "serialNo": "string",
  "expirationDate": "string (date-time)",
  "itemNotes": "string",
  "lineNo": "integer (int32)",
  "usageOrdinalNo": "integer (int32)",
  "usageId": "00000000-0000-0000-0000-000000000000"
  "usageNo": "string"
  "dateSubmitted": "string (date-time)"
}
],
"nextPageLink": "string",
"count": "integer (int64)"
}
```

## Add new items to existing usages

### <span style="color: #F05D30">Path</span>
POST /odata/UsageItems/BulkAdd

### <span style="color: #F05D30">Description</span>
Adds new items to existing usages within a logged organization.

### <span style="color: #F05D30">Request Body</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:480px">Explanation</div>  |                      
|-----:|:-------|
|**usageId**: string <br> <span style="color: #F05D30">**required**</span> <br>  *in formData* | Unique Identifier of the Usage. <br> **If not provided**: 400 Bad Request. |
|**lineItemNo**: string <br> *in formData* | Number of the Line Item. <br> It is generated automatically and recalculated within active Usage Line Items. <br> **If not provided**: Auto-populated.
|**inventoryNo**: string <br> *in formData* | Identification code of the Inventory Item. <br> It is validated by Facility (Inventory Group). <br> **If not provided**: Empty. |
|**inventoryDescription**: string <br> *in formData* | Description of the Inventory Item. <br> It is populated from the existing Inventory if it is mapped by the Inventory No and Inventory Locations values. <br> **If not provided**: Empty. |
|**locationNo**: string <br> <span style="color: #F05D30">**required**</span> <br> *in formData* | Identification Number of the Location. <br> It is populated from ```locationNo``` if the specified Location exists within Usage Facility. <br> **If not provided**: Usage Default Location. |
|**vendorItemNo**: string <br> *in formData* | Code that is used by the Vendor for the Item identification. <br> It is matched with appropriate Inventory Vendor data. <br> **If not provided**: Empty. |
|**manufacturerNo**: string <br> *in formData* | Number of the Manufacturer. <br> It is populated from Inventory Vendor if Item is matched by ```vendorItemNo```. <br> **If not provided**: ```none```. |
|**manufacturerItemNo**: string <br> *in formData* | Item Number of the Manufacturer. <br> It is populated from Inventory Vendor if Item is matched by ```vendorItemNo```. <br> **If not provided**: Empty. |
|**lotNo**: string <br> *in formData* | Identification Number assigned to a particular Quantity or Lot of material from a single Manufacturer. <br> It is populated from ```lotNo```. <br> **If not provided**: Empty. |
|**serialNo**: string <br> *in formData* | Unique Identifier assigned incrementally or sequentially to an Item to uniquely identify it. <br> It is populated from ```serialNo``` . <br> **If not provided**: Empty. |
|**expirationDate**: string <br> *in formData* | Previously determined date after which Item should no longer be used. <br> It is populated from ```expirationDate``` .<br> **If not provided**: Empty. |
|**quantity**: string <br> *in formData* | Quantity specified in the Line Items. <br> **If not provided**: 1. |
|**uom**: string <br> *in formData* | Unit of Measure. <br> It can be matched with Inventory UOM. <br> **If not provided**: EA. |
|**conversionFactor**: string <br> *in formData* | Number of Stock Keeping Units in another Unit of Measure. <br> It is populated from appropriate Inventory UOM Conversion Factor if Item is added as Inventory Item, and the specified UOM value is matched with Inventory UOM <br> **If not provided**: 1. 
|**itemNotes**: string <br> *in formData* | Comments about the Item. <br> It is populated from Item Notes <br> **If not provided**: Empty. |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML <br> Request Example"
{
  "usageId": "string(uuid)",
  "lineItemNo": "string",
  "inventoryNo": "string",
  "inventoryDescription": "string",
  "locationNo": "string",
  "vendorItemNo": "string",
  "manufacturerItemNo": "string",
  "lotNo": "string",
  "serialNo": "string",
  "expirationDate": "string",
  "quantity": "string",
  "uom": "string",
  "conversionFactor": "string",
  "itemNotes": "string"
}
```

``` json title="Request Example"
{
 "usageItems":[
  {
    "usageId": "UsageId1"
  },
  {
    "usageId": "UsageId2"
  },
  {
    "usageId": "UsageId3"
  }
 ]
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
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |

### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
"object"

```