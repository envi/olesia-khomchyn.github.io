# Inventory

## Get list of inventory items

### <span style="color: #F05D30">Path</span>
GET /odata/Inventory

### <span style="color: #F05D30">Description</span>
Returns paged list of the existing inventory within logged organization. You can filter the results by the strict match using $filter parameter – entity eq ‘string’. Or filter the results by the partial match using $filter=contains parameter – contains(entity, ‘string’).

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
| Parameter     |   Explanation     |                      
|-----:|:-------|
|**api-version**: string default 1.0 <br> *in header*|The requested API version.|      
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition.|
|**$orderby**: string <br> *in query* | Sorts the results.|
|**$top**: string  <br> *in query* | Returns only the first n results.|
|**$skip**: string <br> *in query*| Skips the first n results.|
|**Authorization**: string <br> Bearer access_token <br> *in header* |Specify type of the token (bearer), and then insert the access_token, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>
| Response     |   Explanation     |                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**|Incorrect input data or organization ID does not match with organization ID user is logged in.|
|**401 Unauthorized**|Incorrect specified access_token or access_token got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered with an unexpected condition that prevented it from fulfilling the request.|


### <span style="color: #F05D30">Properties</span>
<style>
td, th {
   border: none!important;
}
</style>
| Property     |   Explanation     |                      
|-----:|:-------|
|**inventoryId**: string *(uuid)*|Unique Identifier of the Inventory item.|
|**organizationId**: string *(uuid)*|Unique Identifier of the Organization.|
|**organizationName**: string |Name of the Organization.|
|**inventoryGroupId**: string| Unique Identifier of the Group that contains related Inventory items.|
|**inventoryNo**: string| Identification code of the Inventory item. |
|**inventoryGroupName**: string |Name of the Group that contains related Inventory items|

``` json title="Response content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
      "items": [
        {
          "inventoryId": "00000000-0000-0000-0000-000000000000",
          "organizationId": "00000000-0000-0000-0000-000000000000",
          "organizationName": "string",
          "inventoryGroupId": "00000000-0000-0000-0000-000000000000",
          "inventoryNo": "string",
          "inventoryGroupName": "string",
          "inventoryDescription": "string",
          "inventoryDescription2": "string",
          "stockUOM": "string",
          "arBillingCode": "string",
          "hcpcsCode": "string",
          "notes": "string",
          "dateAdded": "string (date-time)",
          "addedId": "00000000-0000-0000-0000-000000000000",
          "addedByName": "string",
}
```
## Create a new inventory

### <span style="color: #F05D30">Path</span>
POST /odata/Inventory

### <span style="color: #F05D30">Description</span>
Creates a new inventory within logged organization.

### <span style="color: #F05D30">Request Body </span>
<style>
td, th {
   border: none!important;
}
</style>
| Body element     |   Explanation     |                      
|-----:|:-------|
|**inventoryId**: string (uuid) | Unique Identifier of the Inventory item|      
|**organizationId**: string (uuid) | Unique Identifier of the Organization.|  
|**organizationName**: string (uuid) | Name of the Organization.|  
**inventoryGroupId**: string (uuid) | Unique Identifier of the Group that contains related Inventory items. |  


### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
| Parameter     |   Explanation     |                      
|-----:|:-------|
|**api-version**: string default 1.0 <br> *in header*|The requested API version.|      
|**Authorization**: string <br> Bearer access_token <br> *in header* |Specify type of the token (bearer), and then insert the access_token, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>
| Pesponse     |   Explanation     |                      
|-----:|:-------|
|**200 OK**|OK|   
|type|string (uuid)|   
|**400 Bad Request**|Incorrect input data or organization ID does not match with organization ID user is logged in.|
|**401 Unauthorized**|Incorrect specified access_token or access_token got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered with an unexpected condition that prevented it from fulfilling the request.|

``` json title="Response content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
"00000000-0000-0000-0000-000000000000"        
```