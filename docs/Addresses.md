# Addresses
## Get the list of addresses

### <span style="color: #F05D30">Path</span>
GET /odata/Addresses

### <span style="color: #F05D30">Description</span>
Returns paged list of the existing addresses within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*|The requested API version.|      
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
|**$filter**: string <br> *in query* | Filters the results, based on the Boolean condition.|
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

### <span style="color: #F05D30">Properties</span>
<style>
td, th {
   border: none!important;
}
</style>
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**addressId**: string *(uuid)*|Unique Identifier of the Address|
|**organizationId**: string *(uuid)*|Unique Identifier of the Organization|
|**organizationNo**: string | Identification Number of the Organization|
|**organizationName**: string| Name of the Organization|
|**addressNo**: string| Identification Number of the Address|
|**addressName**: string| Name of the Address|
|**addressTypeId**: integer *(int32)* |Unique Identifier of the Address Type|
|**addressType**: string | Address where to send the invoices (Billing) or products (Shipping)
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**addressDescription**: string | Description of the Address |
|**address1**: string | The first Address for shipping or billing purposes |
|**address2**: string | The second Address for shipping or billing purposes |
|**city**: string | City |
|**state**: string |State |
|**zip**: string |Zip |
|**country**: string | Country |
|**contactName**: string | Name of the main contact point |
|**contactEmail**: string | Email of the main contact point |
|**phone**: string | Phone of main the contact point |
|**phoneExt**: string | Phone Extension of the main contact point |
|**fax**: string | Fax |
|**isDefaultAddress**: *boolean* |Is the Address default or not?|
|**activeStatus**: boolean | Is the Status of the Address active or not? |
|**dateCreated**: string *(date-time)* | Date when the Address was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Address |
|**createdByName**: string | Name of the user who created the Address |
|**lastUpdated**: string *(date-time)* | Last Date when the Address was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Address |
|**lastUpdatedByName**: string | Name of the last user who updated the Address |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML <br> Response Example (200 OK)"
{
        "items": [
          {
            "addressId": "00000000-0000-0000-0000-000000000000",
            "organizationId": "00000000-0000-0000-0000-000000000000",
            "organizationNo": "string",
            "organizationName": "string",
            "addressNo": "string",
            "addressName": "string",
            "addressTypeId": "integer (int32)",
            "addressType": "string",
            "facilityId": "00000000-0000-0000-0000-000000000000",
            "facilityNo": "string",
            "facilityName": "string",
            "addressDescription": "string",
            "address1": "string",
            "address2": "string",
            "city": "string",
            "state": "string",
            "zip": "string",
            "country": "string",
            "contactName": "string",
            "contactEmail": "string",
            "phone": "string",
            "phoneExt": "string",
            "fax": "string",
            "isDefaultAddress": "boolean",
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
| <div style="width:200px"> Parameter </div> |<div style="width:380px">Explanation</div> |                      
|-----:|:-------|
|**addressId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path*| Enter the ID of the address here.|
|**api-version**: string default: 1.0 <br> *in header*|The requested API version.|      
|**Authorization**: string dafault: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

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


### <span style="color: #F05D30">Properties</span>
<style>
td, th {
   border: none!important;
}
</style>
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**addressId**: string *(uuid)*|Unique Identifier of the Address|
|**organizationId**: string *(uuid)*|Unique Identifier of the Organization|
|**organizationNo**: string | Identification Number of the Organization|
|**organizationName**: string| Name of the Organization|
|**addressNo**: string| Identification Number of the Address|
|**addressName**: string| Name of the Address|
|**addressTypeId**: integer *(int32)* |Unique Identifier of the Address Type|
|**addressType**: string | Address where to send the invoices (Billing) or products (Shipping)
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**addressDescription**: string | Description of the Address |
|**address1**: string | The first Address for shipping or billing purposes |
|**address2**: string | The second Address for shipping or billing purposes |
|**city**: string | City |
|**state**: string |State |
|**zip**: string |Zip |
|**country**: string | Country |
|**contactName**: string | Name of the main contact point |
|**contactEmail**: string | Email of the main contact point |
|**phone**: string | Phone of the main contact point |
|**phoneExt**: string | Phone Extension of the main contact point |
|**fax**: string | Fax |
|**isDefaultAddress**: *boolean* |Is the Address default or not?|
|**activeStatus**: boolean | Is the Status of the Address active or not? |
|**dateCreated**: string *(date-time)* | Date when the Address was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Address |
|**createdByName**: string | Name of the user who created the Address |
|**lastUpdated**: string *(date-time)* | Last Date when the Address was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Address |
|**lastUpdatedByName**: string | Name of the last user who updated the Address |


``` json title="Response content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
        "addressId": "00000000-0000-0000-0000-000000000000",
        "organizationId": "00000000-0000-0000-0000-000000000000",
        "organizationNo": "string",
        "organizationName": "string",
        "addressNo": "string",
        "addressName": "string",
        "addressTypeId": "integer (int32)",
        "addressType": "string",
        "facilityId": "00000000-0000-0000-0000-000000000000",
        "facilityNo": "string",
        "facilityName": "string",
        "addressDescription": "string",
        "address1": "string",
        "address2": "string",
        "city": "string",
        "state": "string",
        "zip": "string",
        "country": "string",
        "contactName": "string",
        "contactEmail": "string",
        "phone": "string",
        "phoneExt": "string",
        "fax": "string",
        "isDefaultAddress": "boolean",
        "activeStatus": "boolean",
        "dateCreated": "string (date-time)",
        "createdBy": "00000000-0000-0000-0000-000000000000",
        "createdByName": "string",
        "lastUpdated": "string (date-time)",
        "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
        "lastUpdatedByName": "string"
      }
```

