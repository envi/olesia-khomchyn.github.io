# RequisitionFills

## Get the list of requisition fills

### <span style="color: #F05D30">Path</span>
GET /odata/RequisitionFills

### <span style="color: #F05D30">Description</span>
Returns the list of requisition fills within a logged organization.  You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).


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
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|      
|**400 Bad Request** | The limit for the ```$top``` query has been exceeded. The value from the incoming request is 'N' (N is your value from the request). You can find the data on the current limit [here](Options_and_Limitations.md#top-and-skip).
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|


### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:480px">Explanation</div>|                      
|-----:|:-------|
|**requisitionFillId**: string *(uuid)* | Unique Identifier of the Requisition Fill |
|**requisitionFillNo**: string | Identification code of the Requisition Fill |
|**requisitionId**: string *(uuid)* | Unique Identifier of the Requisition |
|**requisitionNo**: string | Identification code of the Requisition |
|**fillDate**: string *(date-time)* | Date of the Requisition Fill |
|**fillStatus**: string | Status of the Requisition Fill |
|**lastUpdated**: string *(date-time)* | Last Date when the Requisition Fill was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Requisition Fill |
|**lastUpdatedByName**: string | Name of the last user who updated the Requisition Fill |
|**dateCreated**: string *(date-time)* | Date when the Requisition Fill was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Requisition Fill |
|**createdByName**: string | Name of the user who created the Requisition Fill |
|**dateSubmitted**: string *(uuid)* | Date when the Requisition Fill was submitted |
|**submittedBy**: string *(uuid)* | Unique Identifier of the user who submitted the Requisition Fill |
|**submittedByName**: string | Name of the user who submitted the Requisition Fill |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "requisitionFillId": "00000000-0000-0000-0000-000000000000",
       "requisitionFillNo": "string",
       "requisitionId": "00000000-0000-0000-0000-000000000000",
       "requisitionFillNo": "string",
       "fillDate": "string (date-time)",
       "fillStatus": "string",
       "lastUpdated": "string (date-time)",
       "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
       "lastUpdatedByName": "string",
       "dateCreated": "string (date-time)",
       "createdBy": "00000000-0000-0000-0000-000000000000",
       "createdByUserName": "string",
       "dateSubmitted": "string (date-time)",
       "submittedBy": "00000000-0000-0000-0000-000000000000",
       "submittedByName": "string"
      }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```


## Get the specified requisition fill

### <span style="color: #F05D30">Path</span>
GET /odata/RequisitionFills({requisitionFillId})

### <span style="color: #F05D30">Description</span>
Returns the details of the requisition fill specified by ID within a logged organization.

### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**requisitionFillId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Requisition Fill here. |
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
|**requisitionFillId**: string *(uuid)* | Unique Identifier of the Requisition Fill |
|**requisitionFillNo**: string | Identification code of the Requisition Fill |
|**requisitionId**: string *(uuid)* | Unique Identifier of the Requisition |
|**requisitionNo**: string | Identification code of the Requisition |
|**fillDate**: string *(date-time)* | Date of the Requisition Fill |
|**fillStatus**: string | Status of the Requisition Fill |
|**lastUpdated**: string *(date-time)* | Last Date when the Requisition Fill was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Requisition Fill |
|**lastUpdatedByName**: string | Name of the last user who updated the Requisition Fill |
|**dateCreated**: string *(date-time)* | Date when the Requisition Fill was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Requisition Fill |
|**createdByName**: string | Name of the user who created the Requisition Fill |
|**dateSubmitted**: string *(uuid)* | Date when the Requisition Fill was submitted |
|**submittedBy**: string *(uuid)* | Unique Identifier of the user who submitted the Requisition Fill |
|**submittedByName**: string | Name of the user who submitted the Requisition Fill |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "requisitionFillId": "00000000-0000-0000-0000-000000000000",
  "requisitionFillNo": "string",
  "requisitionId": "00000000-0000-0000-0000-000000000000",
  "requisitionFillNo": "string",
  "fillDate": "string (date-time)",
  "fillStatus": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByName": "string",
  "dateCreated": "string (date-time)",
  "createdBy": "00000000-0000-0000-0000-000000000000",
  "createdByUserName": "string",
  "dateSubmitted": "string (date-time)",
  "submittedBy": "00000000-0000-0000-0000-000000000000",
  "submittedByName": "string"
}
```
