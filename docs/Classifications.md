# Classifications 

## Get the list of Classifications 

### <span style="color: #F05D30">Path</span>
GET /odata/Classifications

### <span style="color: #F05D30">Description</span>
Returns the list of Classifications within a logged organization.  You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

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
|**Authorization**: string default: <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|


### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|      
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|


### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**classificationId**: string *(uuid)* | Unique Identifier of the Сlassification |
|**classificationName**: string | Name of the Сlassification |
|**classificationTypeId**: integer *(int32)* | Unique Identifier of the Classification Type |
|**classificationTypeValue**: string | Type Value of the Classification |
|**organizationId**: string *(uuid)* | Unique Identifier of the Organization |
|**organizationNo**: string | Identification Number of the Organization |
|**organizationName**: string | Name of the Organization |
|**activeStatus**: boolean | Is the Classification active or not? |
|**dateCreated**: string <br>*(date-time)* | Date when the Classification was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Classification |
|**createdByName**: string | Name of the user who created the Classification |
|**lastUpdated**: string *(date-time)* | Last Date when the Classification was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Classification |
|**lastUpdatedByName**: string | Name of the last user who updated the Classification |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "classificationId": "00000000-0000-0000-0000-000000000000",
      "classificationName": "string",
      "classificationTypeId": "integer (int32)",
      "classificationTypeValue": "string",
      "organizationId": "00000000-0000-0000-0000-000000000000",
      "organizationNo": "string",
      "organizationName": "string",
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

## Create a new Classification

### <span style="color: #F05D30">Path</span>
POST /odata/Classifications

### <span style="color: #F05D30">Description</span>
Creates a new Classification within a logged organization.

### <span style="color: #F05D30">Request body</span>
| <div style="width:200px">Parameter</div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**classificationName**: string <br> <span style="color: #F05D30">**required**</span> | Name of the Сlassification |
|**classificationTypeId**: integer *(int32)* <br> <span style="color: #F05D30">**required**</span> | Unique Identifier of the Classification Type |


``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML<br>Request Example"
{
  "classificationName": "string",
  "classificationTypeId": "integer (int32)",
}
```

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|   
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request.|

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
"00000000-0000-0000-0000-000000000000"

```


## Get the specified Classification

### <span style="color: #F05D30">Path</span>
GET /odata/Classifications({ClassificationId})

### <span style="color: #F05D30">Description</span>
Returns the details of the Classification specified by ID within a logged organization.

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**classificationId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Classification here. |
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
|**classificationId**: string *(uuid)* | Unique Identifier of the Сlassification |
|**classificationName**: string | Name of the Сlassification |
|**classificationTypeId**: integer *(int32)* | Unique Identifier of the Classification Type |
|**classificationTypeValue**: string | Type Value of the Classification |
|**organizationId**: string *(uuid)* | Unique Identifier of the Organization |
|**organizationNo**: string | Identification Number of the Organization |
|**organizationName**: string | Name of the Organization |
|**activeStatus**: boolean | Is the Classification active or not? |
|**dateCreated**: string <br>*(date-time)* | Date when the Classification was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Classification |
|**createdByName**: string | Name of the user who created the Classification |
|**lastUpdated**: string *(date-time)* | Last Date when the Classification was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Classification |
|**lastUpdatedByName**: string | Name of the last user who updated the Classification |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "classificationId": "00000000-0000-0000-0000-000000000000",
  "classificationName": "string",
  "classificationTypeId": "integer (int32)",
  "classificationTypeValue": "string",
  "organizationId": "00000000-0000-0000-0000-000000000000",
  "organizationNo": "string",
  "organizationName": "string",
  "activeStatus": "boolean",
  "dateCreated": "string (date-time)",
  "createdBy": "00000000-0000-0000-0000-000000000000",
  "createdByName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByName": "string"
}
```
