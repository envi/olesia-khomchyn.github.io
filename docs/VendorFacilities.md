# VendorFacilities

## Get the list of Vendor Facilities

### <span style="color: #F05D30">Path</span>
GET /odata/VendorFacilities

### <span style="color: #F05D30">Description</span>
Returns the list of Vendor Facilities within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).


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
|**400 Bad Request** | The limit for the ```$top``` query has been exceeded. The value from the incoming request is 'N' (N is your value from the request). You can find the data on the current limit [here](Options_and_Limitations.md#top-and-skip).
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|


### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**vendorFacilityId**: string *(uuid)* | Unique Identifier of the Vendor Facility |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**vendorFacilityNo**: string | Identification Number of the Facility |
|**vendorFacilityName**: string | Name of the Vendor Facility |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**shipToAccount**: string | Ship To Account |
|**billToAccount**: string | Bill To Account |
|**leadTime**: integer *(int32)* | Allowed Time for the Completion |
|**shippingValue**: number *(double)* | Value of the Shipping |
|**shippingType**: string | Type of the Shipping |
|**discountValue**: number *(double)* | Value of the Discount |
|**discountType**: string | Type of the Discount |
|**taxValue**: number *(double)* | Value of the Tax |
|**taxType**: string | Type of the Tax |
|**vendorGLCode**: string | General Ledger Code of the Vendor |
|**vendorAPNumber**: string | Accounts Payable Number of the Vendor |
|**vendorFacilityPOAlert**: string | Vendor Facility Purchase Order Alert|
|**dateAdded**: string *(date-time)* | Date when the Vendor Facility was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Vendor Facility |
|**addedByName**: string | Name of the user who added the Vendor Facility |
|**lastUpdated**: string *(date-time)* | Last Date when the Vendor Facility was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Vendor Facility |
|**lastUpdatedByName**: string | Name of the last user who updated the Vendor Facility |
|**activeStatus**: boolean | Is the Status of the Vendor Facility active or not? |
|**apToleranceLevel**: number *(double)* | Discrepancy between the original PO and the Invoice sent by the Vendor |
|**apToleranceLevelType**: integer *(int32)* | Type of the Discrepancy  between the original PO and the Invoice sent by the Vendor |
|**apToleranceLevelType<br>Value**: string | Type Value of the Discrepancy  between the original PO and the Invoice sent by the Vendor |
|**paymentMethodId**: string *(uuid)* | Unique Identifier of the Payment Method |
|**paymentMethod**: string | Purchase Order Payment Method |
|**paymentTermsId**: string *(uuid)* | Purchase Order Payment Terms |
|**paymentTermsValue**: string | Value of the Payment Terms |
|**fobId**: string *(uuid)*  | Unique Identifier of the Free On Board (Destination or Ship Point) |
|**fobValue**: string | Value of the Free On Board (Destination or Ship Point)|
|**shipMethod**: string | Method of Shipment |
|**shipVia**: string | Way of Shipment |
|**apToleranceLevel2**: number *(double)* | Discrepancy2 between the original PO and the Invoice sent by the Vendor |
|**apToleranceLevel2Type**: integer *(int32)* | Type of the Discrepancy 2 between the original PO and the Invoice sent by the Vendor |
|**apToleranceLevel2Type<br>Value**: string | Type Value of the Discrepancy 2 between the original PO and the Invoice sent by the Vendor |
|**apFreeFormedTolerance<br>Level**: number *(double)* | Tolerance Level for Free-Form of the Account Payable |
|**apFreeFormedTolerance<br>LevelType**: integer *(int32)* | Type of the Account Payable Free-Formed Tolerance Level |
|**apFreeFormedTolerance<br>LevelTypeValue**: string | Value of the Account Payable Free-Formed Tolerance Level Type |
|**apFreeFormedTolerance<br>Level2**: number *(double)*  | Second Tolerance Level for Free-Form of the Account Payable |
|**apFreeFormedTolerance<br>Level2Type**: integer *(int32)* | Second Type of the Account Payable Free-Formed Tolerance Level |
|**apFreeFormedTolerance<br>Level2TypeValue**: string | Second Value of the Account Payable Free-Formed Tolerance Level Type |
|**defaultBlankPOExpected<br>Date**: boolean | Expected Date of Delivery Purchase Order Blank by default </span> |
|**defaultPONotes**: string | Default Notes fo Purchase Orders  |
|**creditCardIDId**: string *(uuid)* | Unique Identifier of the Credit Card |
|**creditCardID**: string | Identifier of the Credit Card |
|**credirCardDescription**: string | Description of the Credit Card |
|**currencyTypeId**: integer *(int32)* | Unique Identifier of the Currency Type |
|**currencyTypeValue**: string | Value of the Currency Type|
|**vendorXref**: string | Cross Reference of the Vendor | 
|**autoAttachProcessOCR**: boolean | Indicates Automatical Processing of OCR Invoices |
|**minimumOrderTypeId**: integer *(int32)* | Identifier of the Minimum Order Type  |
|**minimumOrderTypeValue**: string | Value of the Minimum Order Type |
|**minimumOrder**: number *(double)* | Minimum Order |
|**matchOptionId**: integer *(int32)* | Unique Identifier of the Match Option |
|**matchOptionValue**: string | Value of the Match Option |
|**ocrMatchOptionId**: integer *(int32)* | Unique Identifier of the OCR Match Option |
|**ocrMatchOptionValue**: string | Value of the OCR Match Option |
|**splitTaxValue**: boolean | Value of the Split Tax |
|**splitDiscountValue**: boolean | Value of the Discount Split |
|**splitShippingValue**: boolean | Value of the Split Shipping |
|**takeDepartmentsIntoAccount**: boolean | Take Departments into account |
|**taxableItemsOnly**: boolean | Take Taxable Items only into account |



``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "vendorFacilityId": "00000000-0000-0000-0000-000000000000",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "vendorFacilityNo": "string",
      "vendorFacilityName": "string",
      "vendorId": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "locationId": "00000000-0000-0000-0000-000000000000",
      "locationNo": "string",
      "locationName": "string",
      "shipToAccount": "string",
      "billToAccount": "string",
      "leadTime": "integer (int32)",
      "shippingValue": "number (double)",
      "shippingType": "string",
      "discountValue": "number (double)",
      "discountType": "string",
      "taxValue": "number (double)",
      "taxType": "string",
      "vendorGLCode": "string",
      "vendorAPNumber": "string",
      "vendorFacilityPOAlert": "string",
      "dateAdded": "string (date-time)",
      "addedBy": "00000000-0000-0000-0000-000000000000",
      "addedByName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByName": "string",
      "activeStatus": "boolean",
      "apToleranceLevel": "number (double)",
      "apToleranceLevelType": "integer (int32)",
      "apToleranceLevelTypeValue": "string",
      "paymentMethodId": "00000000-0000-0000-0000-000000000000",
      "paymentMethod": "string",
      "paymentTermsId": "00000000-0000-0000-0000-000000000000",
      "paymentTermsValue": "string",
      "fobId": "00000000-0000-0000-0000-000000000000",
      "fobValue": "string",
      "shipMethod": "string",
      "shipVia": "string",
      "apToleranceLevel2": "number (double)",
      "apToleranceLevel2Type": "integer (int32)",
      "apToleranceLevel2TypeValue": "string",
      "apFreeFormedToleranceLevel": "number (double)",
      "apFreeFormedToleranceLevelType": "integer (int32)",
      "apFreeFormedToleranceLevelTypeValue": "string",
      "apFreeFormedToleranceLevel2": "number (double)",
      "apFreeFormedToleranceLevel2Type": "integer (int32)",
      "apFreeFormedToleranceLevel2TypeValue": "string",
      "defaultBlankPOExpectedDate": "boolean",
      "defaultPONotes": "string",
      "creditCardIDId": "00000000-0000-0000-0000-000000000000",
      "creditCardID": "string",
      "creditCardDescription": "string",
      "currencyTypeId": "integer (int32)",
      "currencyTypeValue": "string",
      "vendorXref": "string",
      "autoAttachProcessOCR": "boolean",
      "minimumOrderTypeId": "integer (int32)",
      "minimumOrderTypeValue": "string",
      "minimumOrder": "number (double)",
      "matchOptionId": "integer (int32)",
      "matchOptionValue": "string",
      "ocrMatchOptionId": "integer (int32)",
      "ocrMatchOptionValue": "string",
      "splitTaxValue": "boolean",
      "splitDiscountValue": "boolean",
      "splitShippingValue": "boolean",
      "takeDepartmentsIntoAccount": "boolean",
      "taxableItemsOnly": "boolean"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```


## Create a new Vendor Facility

### <span style="color: #F05D30">Path</span>
POST /odata/Vendors({VendorId})/VendorFacilities 

### <span style="color: #F05D30">Description</span>
Creates a new Vendor Facility for a specified active Location (All Locations) within an active Vendor logged in an organization.

### <span style="color: #F05D30">Request body</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:420px">Explanation</div>  |                      
|-----:|:-------|
|**facilityId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> | Unique Identifier of the Facility |
|**locationId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> | Unique Identifier of the Location |
|**shipToAccount**: string | Ship To Account |
|**billToAccount**: string | Bill To Account |
|**leadTime**: integer *(int32)*  <br> <span style="color: #F05D30">**required**</span> | Allowed Time for the Completion |
|**paymentMethodId**: string *(uuid)* | Unique Identifier of the Payment Method. <br> **If not provided**: None.|
|**paymentTermsId**: string *(uuid)* | Purchase Order Payment Terms. <br> **If not provided**: None.|
|**creditCardIDId**: string *(uuid)* | Unique Identifier of the Credit Card. <br> **If not provided**: None. |
|**fobId**: string *(uuid)*  | Unique Identifier of the Free On Board (Destination or Ship Point). <br> **If not provided**: None. |
|**shipMethod**: string | Method of Shipment |
|**shipVia**: string | Way of Shipment |
|**vendorXref**: string | Cross Reference of the Vendor | 
|**matchOptionId**: integer *(int32)* | Unique Identifier of the Match Option. <br> **If not provided**: None.|
|**ocrMatchOptionId**: integer *(int32)* | Unique Identifier of the OCR Match Option. <br> **If not provided**: None. |
|**taxableItemsOnly**: boolean | Take Taxable Items only into account |
|**takeDepartmentsIntoAccount**: boolean | Take Departments into account |
|**minimumOrder**: number *(double)* | Minimum Order |
|**minimumOrderTypeId**: integer *(int32)* | Identifier of the Minimum Order Type. <br> **If not provided**: warning message. |
|**discountValue**: number *(double)* | Value of the Discount |
|**discountTypeId**: integer *(int32)* | Unique Identifier of the Discount Type for the Vendor Facility. <br> **If not provided**: %. |
|**splitDiscountValue**: boolean | Value of the Discount Split |
|**taxValue**: number *(double)* | Value of the Tax |
|**taxTypeId**: integer *(int32)* | Unique Identifier of the Tax Type. <br> **If not provided**: %. |
|**splitTaxValue**: boolean | Value of the Split Tax |
|**shippingValue**: number *(double)* | Value of the Shipping |
|**shippingTypeId**: integer *(int32)* | Unique Identifier of the Shipping Type. <br> **If not provided**: %. |
|**splitShippingValue**: boolean | Value of the Split Shipping |
|**vendorGLCode**: string | General Ledger Code of the Vendor |
|**vendorAPNumber**: string | Accounts Payable Number of the Vendor |
|**apToleranceLevel**: number *(double)* | Discrepancy between the original PO and the Invoice sent by the Vendor |
|**apToleranceLevelType**: integer *(int32)* | Type of the Discrepancy between the original PO and the Invoice sent by the Vendor. <br> **If not provided**: % (Unit Cost).|
|**apToleranceLevel2**: number *(double)* | Discrepancy2 between the original PO and the Invoice sent by the Vendor |
|**apToleranceLevel2Type**: integer *(int32)* | Type of the Discrepancy 2 between the original PO and the Invoice sent by the Vendor. <br> **If not provided**: % (Unit Cost). |
|**apFreeFormedTolerance<br>Level**: number *(double)* | Tolerance Level for Free-Form of the Account Payable |
|**apFreeFormedTolerance<br>LevelType**: integer *(int32)* | Type of the Account Payable Free-Formed Tolerance Level. <br> **If not provided**: $ (Extended Cost).|
|**apFreeFormedTolerance<br>Level2**: number *(double)*  | Second Tolerance Level for Free-Form of the Account Payable |
|**apFreeFormedTolerance<br>Level2Type**: integer *(int32)* | Second Type of the Account Payable Free-Formed Tolerance Level. <br> **If not provided**: $ (Extended Cost). |
|**currencyTypeId**: integer *(int32)* | Unique Identifier of the Currency Type. <br> **If not provided**: USD. |
|**defaultBlankPOExpected<br>Date**: boolean | Expected Date of Delivery Purchase Order Blank by default. <br> **If not provided**: ```true```.  |
|**autoAttachProcessOCR**: boolean | Indicates Automatical Processing of OCR Invoices |
|**vendorFacilityPOAlert**: string | Vendor Facility Purchase Order Alert|
|**defaultPONotes**: string | Default Notes fo Purchase Orders  |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML <br> Request Example"
{
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "locationId": "00000000-0000-0000-0000-000000000000",
  "shipToAccount": "string",
  "billToAccount": "string",
  "leadTime": "integer (int32)",
  "paymentMethodId": "00000000-0000-0000-0000-000000000000",
  "paymentTermsId": "00000000-0000-0000-0000-000000000000",
  "creditCardIDId": "00000000-0000-0000-0000-000000000000",
  "fobId": "00000000-0000-0000-0000-000000000000",
  "shipMethod": "string",
  "shipVia": "string",
  "vendorXref": "string",
  "matchOptionId": "integer (int32)",
  "ocrMatchOptionId": "integer (int32)",
  "taxableItemsOnly": "boolean",
  "takeDepartmentsIntoAccount": "boolean",
  "minimumOrder": "number (double)",
  "minimumOrderTypeId": "integer (int32)",
  "discountValue": "number (double)",
  "discountTypeId": "integer (int32)",
  "splitDiscountValue": "boolean",
  "taxValue": "number (double)",
  "taxTypeId": "integer (int32)",
  "splitTaxValue": "boolean",
  "shippingValue": "number (double)",
  "shippingTypeId": "integer (int32)",
  "splitShippingValue": "boolean",
  "vendorGLCode": "string",
  "vendorAPNumber": "string",
  "apToleranceLevel": "number (double)",
  "apToleranceLevelType": "integer (int32)",
  "apToleranceLevel2": "number (double)",
  "apToleranceLevel2Type": "integer (int32)",
  "apFreeFormedToleranceLevel": "number (double)",
  "apFreeFormedToleranceLevelType": "integer (int32)",
  "apFreeFormedToleranceLevel2": "number (double)",
  "apFreeFormedToleranceLevel2Type": "integer (int32)",
  "currencyTypeId": "integer (int32)",
  "defaultBlankPOExpectedDate": "boolean",
  "autoAttachProcessOCR": "boolean",
  "vendorFacilityPOAlert": "string",
  "defaultPONotes": "string"
}
    
```
### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**vendorId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Vendor here. |
|**api-version**: string default: 1.0 <br> *in header*|The requested API version.|      
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK** | OK |    
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response Example (200 OK)"
"00000000-0000-0000-0000-000000000000"
```


## Get the specified Vendor Facility

### <span style="color: #F05D30">Path</span>
GET /odata/VendorFacilities({vendorFacilityId})

### <span style="color: #F05D30">Description</span>
Returns the details of the Vendor Facility specified by ID within a logged organization

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**vendorFacilityId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Vendor Facility here. |
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
|**vendorFacilityId**: string *(uuid)* | Unique Identifier of the Vendor Facility |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**vendorFacilityNo**: string | Identification Number of the Facility |
|**vendorFacilityName**: string | Name of the Vendor Facility |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**shipToAccount**: string | Ship To Account |
|**billToAccount**: string | Bill To Account |
|**leadTime**: integer *(int32)* | Allowed Time for the Completion |
|**shippingValue**: number *(double)* | Value of the Shipping |
|**shippingType**: string | Type of the Shipping |
|**discountValue**: number *(double)* | Value of the Discount |
|**discountType**: string | Type of the Discount |
|**taxValue**: number *(double)* | Value of the Tax |
|**taxType**: string | Type of the Tax |
|**vendorGLCode**: string | General Ledger Code of the Vendor |
|**vendorAPNumber**: string | Accounts Payable Number of the Vendor |
|**vendorFacilityPOAlert**: string | Vendor Facility Purchase Order Alert|
|**dateAdded**: string *(date-time)* | Date when the Vendor Facility was added |
|**addedBy**: string *(uuid)* | Unique Identifier of the user who added the Vendor Facility |
|**addedByName**: string | Name of the user who added the Vendor Facility |
|**lastUpdated**: string *(date-time)* | Last Date when the Vendor Facility was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Vendor Facility |
|**lastUpdatedByName**: string | Name of the last user who updated the Vendor Facility |
|**activeStatus**: boolean | Is the Status of the Vendor Facility active or not? |
|**apToleranceLevel**: number *(double)* | Discrepancy between the original PO and the Invoice sent by the Vendor |
|**apToleranceLevelType**: integer *(int32)* | Type of the Discrepancy between the original PO and the Invoice sent by the Vendor |
|**apToleranceLevelType<br>Value**: string | Type Value of the Discrepancy between the original PO and the Invoice sent by the Vendor |
|**paymentMethodId**: string *(uuid)* | Unique Identifier of the Payment Method |
|**paymentMethod**: string | Purchase Order Payment Method |
|**paymentTermsId**: string *(uuid)* | Purchase Order Payment Terms |
|**paymentTermsValue**: string | Value of the Payment Terms |
|**fobId**: string *(uuid)*  | Unique Identifier of the Free On Board (Destination or Ship Point) |
|**fobValue**: string | Value of the Free On Board (Destination or Ship Point)|
|**shipMethod**: string | Method of Shipment |
|**shipVia**: string | Way of Shipment |
|**apToleranceLevel2**: number *(double)* | Discrepancy2 between the original PO and the Invoice sent by the Vendor |
|**apToleranceLevel2Type**: integer *(int32)* | Type of the Discrepancy 2 between the original PO and the Invoice sent by the Vendor |
|**apToleranceLevel2Type<br>Value**: string | Type Value of the Discrepancy 2 between the original PO and the Invoice sent by the Vendor |
|**apFreeFormedTolerance<br>Level**: number *(double)* | Tolerance Level for Free-Form of the Account Payable |
|**apFreeFormedTolerance<br>LevelType**: integer *(int32)* | Type of the Account Payable Free-Formed Tolerance Level |
|**apFreeFormedTolerance<br>LevelTypeValue**: string | Value of the Account Payable Free-Formed Tolerance Level Type |
|**apFreeFormedTolerance<br>Level2**: number *(double)*  | Second Tolerance Level for Free-Form of the Account Payable |
|**apFreeFormedTolerance<br>Level2Type**: integer *(int32)* | Second Type of the Account Payable Free-Formed Tolerance Level |
|**apFreeFormedTolerance<br>Level2TypeValue**: string | Second Value of the Account Payable Free-Formed Tolerance Level Type |
|**defaultBlankPOExpected<br>Date**: boolean | Expected Date of Delivery Purchase Order Blank by default </span> |
|**defaultPONotes**: string | Default Notes fo Purchase Orders  |
|**creditCardIDId**: string *(uuid)* | Unique Identifier of the Credit Card |
|**creditCardID**: string | Identifier of the Credit Card |
|**credirCardDescription**: string | Description of the Credit Card |
|**currencyTypeId**: integer *(int32)* | Unique Identifier of the Currency Type |
|**currencyTypeValue**: string | Value of the Currency Type|
|**vendorXref**: string | Cross Reference of the Vendor | 
|**autoAttachProcessOCR**: boolean | Indicates Automatical Processing of OCR Invoices |
|**minimumOrderTypeId**: integer *(int32)* | Identifier of the Minimum Order Type  |
|**minimumOrderTypeValue**: string | Value of the Minimum Order Type |
|**minimumOrder**: number *(double)* | Minimum Order |
|**matchOptionId**: integer *(int32)* | Unique Identifier of the Match Option |
|**matchOptionValue**: string | Value of the Match Option |
|**ocrMatchOptionId**: integer *(int32)* | Unique Identifier of the OCR Match Option |
|**ocrMatchOptionValue**: string | Value of the OCR Match Option |
|**splitTaxValue**: boolean | Value of the Split Tax |
|**splitDiscountValue**: boolean | Value of the Discount Split |
|**splitShippingValue**: boolean | Value of the Split Shipping |
|**takeDepartmentsIntoAccount**: boolean | Take Departments into account |
|**taxableItemsOnly**: boolean | Take Taxable Items only into account |




``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "vendorFacilityId": "00000000-0000-0000-0000-000000000000",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "vendorFacilityNo": "string",
  "vendorFacilityName": "string",
  "vendorId": "00000000-0000-0000-0000-000000000000",
  "vendorNo": "string",
  "vendorName": "string",
  "locationId": "00000000-0000-0000-0000-000000000000",
  "locationNo": "string",
  "locationName": "string",
  "shipToAccount": "string",
  "billToAccount": "string",
  "leadTime": "integer (int32)",
  "shippingValue": "number (double)",
  "shippingType": "string",
  "discountValue": "number (double)",
  "discountType": "string",
  "taxValue": "number (double)",
  "taxType": "string",
  "vendorGLCode": "string",
  "vendorAPNumber": "string",
  "vendorFacilityPOAlert": "string",
  "dateAdded": "string (date-time)",
  "addedBy": "00000000-0000-0000-0000-000000000000",
  "addedByName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByName": "string",
  "activeStatus": "boolean",
  "apToleranceLevel": "number (double)",
  "apToleranceLevelType": "integer (int32)",
  "apToleranceLevelTypeValue": "string",
  "paymentMethodId": "00000000-0000-0000-0000-000000000000",
  "paymentMethod": "string",
  "paymentTermsId": "00000000-0000-0000-0000-000000000000",
  "paymentTermsValue": "string",
  "fobId": "00000000-0000-0000-0000-000000000000",
  "fobValue": "string",
  "shipMethod": "string",
  "shipVia": "string",
  "apToleranceLevel2": "number (double)",
  "apToleranceLevel2Type": "integer (int32)",
  "apToleranceLevel2TypeValue": "string",
  "apFreeFormedToleranceLevel": "number (double)",
  "apFreeFormedToleranceLevelType": "integer (int32)",
  "apFreeFormedToleranceLevelTypeValue": "string",
  "apFreeFormedToleranceLevel2": "number (double)",
  "apFreeFormedToleranceLevel2Type": "integer (int32)",
  "apFreeFormedToleranceLevel2TypeValue": "string",
  "defaultBlankPOExpectedDate": "boolean",
  "defaultPONotes": "string",
  "creditCardIDId": "00000000-0000-0000-0000-000000000000",
  "creditCardID": "string",
  "creditCardDescription": "string",
  "currencyTypeId": "integer (int32)",
  "currencyTypeValue": "string",
  "vendorXref": "string",
  "autoAttachProcessOCR": "boolean",
  "minimumOrderTypeId": "integer (int32)",
  "minimumOrderTypeValue": "string",
  "minimumOrder": "number (double)",
  "matchOptionId": "integer (int32)",
  "matchOptionValue": "string",
  "ocrMatchOptionId": "integer (int32)",
  "ocrMatchOptionValue": "string",
  "splitTaxValue": "boolean",
  "splitDiscountValue": "boolean",
  "splitShippingValue": "boolean",
  "takeDepartmentsIntoAccount": "boolean",
  "taxableItemsOnly": "boolean"
}
```

