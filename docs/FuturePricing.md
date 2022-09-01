# FuturePricing
## Get the specified future pricing item

### <span style="color: #F05D30">Path</span>
GET /odata/FuturePricing({futurePricingId})

### <span style="color: #F05D30">Description</span>
Returns details of the future pricing specified by ID.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**futurePricingId**: string *(uuid)* <br> *in path* | Enter the ID of the Future Pricing Item here. |
|**api-version**: string default: 1.0 <br> *in header* | The requested API version. |
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
|<div style="width:200px">Property </div> |<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**futurePricingId**: string *(uuid)* | Unique Identifier of the Future Pricing record |
|**inventoryId**: string *(uuid)* | Unique Identifier of the Inventory item |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**organizationId**: string *(uuid)* | Unique Identifier of the Organization |
|**organizationNo**: string | Identification Number of the Organization |
|**organizationName**: string | Name of the Organization |
|**vendorUOM**: string | Vendor's Unit of Measure |
|**vendorConversionFactor**: <br> integer *(int32)* | Number of Stock Keeping Units in another Vendor's Unit of Measure |
|**contractNo**: string | Number of Contract |
|**contractExpDate**: string <br> *(date-time)* | Expiration Date of the Contract |
|**priceChangeDate**: string <br> *(date-time)* | Date of the Price Changing |
|**newPrice**: number *(double)* | New Price value |
|**priceChangeStatus**: integer <br>*(int32)* | Status of the Price Changing |
|**priceChangeStatusName**: <br> string | Status Name of the Price Changing |
|**dateAdded**: string *(date-time)* | Date when the Future Pricing was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Future Pricing |
|**lastUpdated**: string *(date-time)* | Last Date when the Future Pricing was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Future Pricing |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**addedByName**: string | Name of the user who added the Future Pricing |
|**lastUpdatedByName**: string | Name of the last user who updated the Future Pricing |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML <br> Response Example (200 OK)"
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