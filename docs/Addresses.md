# Addresses
## Get list of addresses

### <span style="color: #F05D30">Path</span>
GET /odata/Addresses

### <span style="color: #F05D30">Description</span>
Returns paged list of the existing addresses within logged organization. You can filter the results by the strict match using $filter parameter – entity eq ‘string’. Or filter the results by the partial match using $filter=contains parameter – contains(entity, ‘string’).

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
| Pesponse     |   Explanation     |                      
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
|**addressId**: string *(uuid)*|Unique Identifier of the Address.|
|**organizationId**: string *(uuid)*|Unique Identifier of the Organization.|
|**organizationNo**: string | Indentification Number of the Organization.|
|**organizationName**: string| Name of the Organization.|
|**addressNo**: string| Identification Number of the Address.|
|**addressName**: string| Name of the Address.|
|**addressTypeId**: integer *(int32)* |Unique Identifier of the Address Type.|


``` json title="Response content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
        "items": [
          {
      "futurePricingId": "00000000-0000-0000-0000-000000000000",
      "inventoryId": "00000000-0000-0000-0000-000000000000",
      "inventoryNo": "string",
      "vendorItemNo": "string",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "vendorId": "00000000-0000-0000-0000-000000000000",
      "organizationId": "00000000-0000-0000-0000-000000000000",
      "organizationNo": "string",
      "organizationName": "string",
      "vendorUOM": "string",
      "vendorConversionFactor": "integer (int32)",
      "contractNo": "string",
      "contractExpDate": "string (date-time)",
      "priceChangeDate": "string (date-time)",
      "newPrice": "number (double)",
      "priceChangeStatus": "integer (int32)",
      "priceChangeStatusName": "string",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "facilityNo": "string",
      "facilityName": "string",
      "addedByName": "string",
      "lastUpdatedByName": "string"
}
```

## Get the specified address

### <span style="color: #F05D30">Path</span>
GET /odata/Addresses({addressId})

### <span style="color: #F05D30">Description</span>
Returns details of the address specified by ID.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
| Parameter     |   Explanation     |                      
|-----:|:-------|
|**addressId**: string (uuid)<br> *in path*| Enter the ID of the address here.|
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
|**addressId**: string *(uuid)*|Unique Identifier of the Address.|
|**organizationId**: string *(uuid)*|Unique Identifier of the Organization.|
|**organizationNo**: string | Indentification Number of the Organization.|
|**organizationName**: string| Name of the Organization.|
|**addressNo**: string| Identification Number of the Address.|
|**addressName**: string| Name of the Address.|
|**addressTypeId**: integer *(int32)* |Unique Identifier of the Address Type.|

``` json title="Response content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
        "items": [
          {
      "futurePricingId": "00000000-0000-0000-0000-000000000000",
      "inventoryId": "00000000-0000-0000-0000-000000000000",
      "inventoryNo": "string",
      "vendorItemNo": "string",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "vendorId": "00000000-0000-0000-0000-000000000000",
      "organizationId": "00000000-0000-0000-0000-000000000000",
      "organizationNo": "string",
      "organizationName": "string",
      "vendorUOM": "string",
      "vendorConversionFactor": "integer (int32)",
      "contractNo": "string",
      "contractExpDate": "string (date-time)",
      "priceChangeDate": "string (date-time)",
      "newPrice": "number (double)",
      "priceChangeStatus": "integer (int32)",
      "priceChangeStatusName": "string",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "facilityNo": "string",
      "facilityName": "string",
      "addedByName": "string",
      "lastUpdatedByName": "string"
}
```

