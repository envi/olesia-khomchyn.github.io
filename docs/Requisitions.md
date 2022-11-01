# Requisitions

## Get the list of requisitions

### <span style="color: #F05D30">Path</span>
GET /odata/Requisitions

### <span style="color: #F05D30">Description</span>
Returns the paged list of existing requisitions. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

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
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**requisitionId**: string *(uuid)*  | Unique Identifier of the Requisition |
|**requisitionNo**: string | Identification code of the Requisition |
|**requisitionTypeId**: integer *(int32)* | Unique Identifier of the Requisition |
|**requisitionType**: string | Type of Requsition |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**patientId**: string *(uuid)* | Unique Identifier of the Patient |
|**departmentId**: string *(uuid)* | Unique Identifier of the Department |
|**departmentNo**: string | Number of the Department |
|**departmentName**: string | Name of the Department |
|**deliveryLocationId**: string <br> *(uuid)* | Unique Identifier of the Delivery Location |
|**deliveryLocationNo**: string | Identification Number of the Delivery Location |
|**deliveryLocationName**: string | Name of the Delivery Location |
|**reference**: string | Information concerning the Transaction |
|**requisitionerId**: string *(uuid)* | Unique Identifier of the Requisitioner |
|**requisitionerName**: string | Name of the Requisitioner |
|**requisitionDate**: string *(date-time)* | Date of the Requsition |
|**requiredDeliveryDate**: string <br> *(date-time)* | Required Delivery Date of the Requisition |
|**requisitionStatusId**: integer *(int32)* | Unique Identifier of the Requisition |
|**requisitionStatus**: string | Status of the Requisition |
|**requisitionNotes**: string | Comments about the Requisition |
|**buyerName**: string | Name of the Buyer |
|**buyerAddress1**: string | The first Address of the Buyer for shipping or billing purposes |
|**buyerAddress2**: string | The second Address of the Buyer for shipping or billing purposes |
|**buyerCity**: string | City of the Buyer |
|**buyerState**: string | State of the Buyer |
|**buyerZip**: string | Zip of the Buyer |
|**buyerCountry**: string | Country of the Buyer |
|**buyerContact**: string | Contact of the Buyer |
|**buyerContactEmail**: string | Contact Email of the Buyer |
|**buyerPhone**: string | Phone of the Buyer |
|**buyerFax**: string | Fax of the Buyer |
|**shippingName**: string | Name of the Shipping |
|**shippingAddress1**: string | The First Address for sending the Requisition |
|**shippingAddress2**: string | The Second Address for sending the Requisition |
|**shippingCity**: string | City for sending the Requisition |
|**shippingState**: string | State for sending the Requisition |
|**shippingZip**: string | Zip for sending the Requisition |
|**shippingCountry**: string | Country for sending the Requisition |
|**shippingContact**: string | Contact for sending the Requisition |
|**shippingContactEmail**: string | Contact Email for sending the Requisition |
|**shippingPhone**: string | Phone for sending the Requisition |
|**shippingPhoneExt**: string | Phone Extension for sending the Requisition |
|**shippingFax**: string | Fax for sending the Requisition |
|**discount**: number *(double)* | Discount for the Requisition |
|**discountTypeId**: integer *(int32)* | Unique Identifier of the Discount Type for the Requisition |
|**discountType**: string | Type of the discount for the Requisition |
|**salesTax**: string | Tax for the Sales |
|**salesTaxTypeId**: string | Unique Identifier of the Tax for the Sales |
|**shipping**: number *(double)*  | Number of the Shipping |
|**shippingTypeId**: integer *(int32)* | Unique Identifier of the Shipping Type |
|**shippingType**: string | Type of the Shipping |
|**dateSubmitted**: string *(date-time)* | Date when the Requisition was submitted |
|**dateCreated**: string *(date-time)* | Date when the Requisition was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Requsition |
|**createdByName**: string | Name of the user who created the Requisition |
|**lastUpdated**: string *(date-time)* | Last Date when the Requisition was updated |
|**lastUpdatedBy**: string *(date-time)* | Unique Identifier of the last user who updated the Requisition |
|**lastUpdatedByName**: string | Name of the last user who updated the Requisition |
|**requisitionSourceId**: integer *(int32)* | Unique Identifier of the Requisition |
|**requisitionSource**: string | Source of the Requisition |
|**notes**: string | Comments about the Requisition |
|**submittedBy**: string *(uuid)* | Unique Identifier of the user who submitted the Requisition |
|**submittedByName**: string | Name of the user who submitted the Requisition |
|**isCanceled**: boolean | Is the Requisition canceled or not? |
|**parAreaId**: string *(uuid)* | Unique Identifier of the PAR Area |
|**sourceFacilityId**: string *(uuid)* | Unique Identifier of the Facility Source |
|**sourceFacilityNo**: string | Number of the Facility Source |
|**sourceFacilityName**: string | Name of the Facility Source |
|**statusLastUpdated**: string <br> *(date-time)* | Last Date when the Status of the Facility Source was updated |
|**statusLastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Status of the Facility Source |
|**statusLastUpdatedByName**: string | Name of the last user who updated the Status of the Facility Source |
|**isConverted**: boolean | Is the Facility Source converted or not? |
|**cancelledRemainingQuantities<br>LastUpdated**: string *(date-time)* | Last Date when the Remaining Quantities of the Facility Source was canceled and updated |
|**cancelledRemaining<br>QuantitiesBy**: string *(uuid)* | Unique Identifier of the user who canceled the Remaining Quantities of the Facility Source |
|**cancelledRemaining<br>QuantitiesByName**: string | Name of the user who updated the Remaining Quantities of the Facility Source |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
        "items": [
        {
        "requisitionId": "00000000-0000-0000-0000-000000000000",
        "requisitionNo": "string",
        "requisitionTypeId": "integer (int32)",
        "requisitionType": "string",
        "facilityId": "00000000-0000-0000-0000-000000000000",
        "facilityNo": "string",
        "facilityName": "string",
        "patientId": "00000000-0000-0000-0000-000000000000",
        "departmentId": "00000000-0000-0000-0000-000000000000",
        "departmentNo": "string",
        "departmentName": "string",
        "deliveryLocationId": "00000000-0000-0000-0000-000000000000",
        "deliveryLocationNo": "string",
        "deliveryLocationName": "string",
        "reference": "string",
        "requisitionerId": "00000000-0000-0000-0000-000000000000",
        "requisitionerName": "string",
        "requisitionDate": "string (date-time)",
        "requiredDeliveryDate":  "string (date-time)"  ,
        "requisitionStatusId": "integer (int32)",
        "requisitionStatus": "string",
        "requisitionNotes": "string",
        "buyerName": "string",
        "buyerAddress1": "string",
        "buyerAddress2": "string",
        "buyerCity": "string",
        "buyerState": "string",
        "buyerZip": "string",
        "buyerCountry": "string",
        "buyerContact": "string",
        "buyerContactEmail": "string",
        "buyerPhone": "string",
        "buyerPhoneExt": "string",
        "buyerFax": "string",
        "shippingName": "string",
        "shippingAddress1": "string",
        "shippingAddress2": "string",
        "shippingCity": "string",
        "shippingState": "string",
        "shippingZip": "string",
        "shippingCountry": "string",
        "shippingContact": "string",
        "shippingContactEmail": "string",
        "shippingPhone": "string",
        "shippingPhoneExt": "string",
        "shippingFax": "string",
        "discount": "number (double)",
        "discountTypeId": "integer (int32)",
        "discountType": "string",
        "salesTax": "number (double)",
        "salesTaxTypeId": "integer (int32)",
        "salesTaxType": "string",
        "shipping": "number (double)",
        "shippingTypeId": "integer (int32)",
        "shippingType": "string",
        "dateSubmitted": "string (date-time)",
        "dateCreated": "string (date-time)",
        "createdBy": "00000000-0000-0000-0000-000000000000",
        "createdByName": "string",
        "lastUpdated": "string (date-time)",
        "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
        "lastUpdatedByName": "string",
        "requisitionSourceId": "integer (int32)",
        "requisitionSource": "string",
        "notes": "string",
        "submittedBy": "00000000-0000-0000-0000-000000000000",
        "submittedByName": "string",
        "isCanceled": "boolean",
        "parAreaId": "00000000-0000-0000-0000-000000000000",
        "sourceFacilityId": "00000000-0000-0000-0000-000000000000",
        "sourceFacilityNo": "string",
        "sourceFacilityName": "string",
        "statusLastUpdated": "string (date-time)",
        "statusLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
        "statusLastUpdatedByName": "string",
        "isConverted": "boolean",
        "cancelledRemainingQuantitiesLastUpdated": "string (date-time)",
        "cancelledRemainingQuantitiesBy": "00000000-0000-0000-0000-000000000000",
        "cancelledRemainingQuantitiesByName": "string"
        }
        ],
        "nextPageLink": "string",
        "count": "integer (int64)"
        }
```

## Create a new standard requisition

### <span style="color: #F05D30">Path</span>
POST /odata/Requisitions

### <span style="color: #F05D30">Description</span>
Creates a new standard requisition within a logged organization.

### <span style="color: #F05D30">Request Body</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:450px">Explanation</div>  |                      
|-----:|:-------|
|**facilityNo**: string <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Identification Number of the Facility |
|**departmentNo**: string <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Identification Number of the Department |
|**patientId**: string *(uuid)* | Unique Identifier of the Patient |
|**reference**: string | Information concerning the Transaction |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML <br> Request Example"
{
      "facilityNo": "string",
      "departmentNo": "string",
      "patientId": "00000000-0000-0000-0000-000000000000",
      "reference": "string"
      }   
```

### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*|The requested API version.|      
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|


### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|   
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request.|

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML <br> Request Example"
"00000000-0000-0000-0000-000000000000"

```

## Get the specified requisition

### <span style="color: #F05D30">Path</span>
GET /odata/Requisitions({requisitionId})

### <span style="color: #F05D30">Description</span>
Returns the details of the Requisition specified by ID.

### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**requisitionId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Requisition here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request. |

### <span style="color: #F05D30">Properties</span>
|<div style="width:200px">Property </div> |<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**requisitionId**: string *(uuid)*  | Unique Identifier of the Requisition |
|**requisitionNo**: string | Identification code of the Requisition |
|**requisitionTypeId**: integer *(int32)* | Unique Identifier of the Requisition |
|**requisitionType**: string | Type of Requsition |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**patientId**: string *(uuid)* | Unique Identifier of the Patient |
|**departmentId**: string *(uuid)* | Unique Identifier of the Department |
|**departmentNo**: string | Number of the Department |
|**departmentName**: string | Name of the Department |
|**deliveryLocationId**: string <br> *(uuid)* | Unique Identifier of the Delivery Location |
|**deliveryLocationNo**: string | Identification Number of the Delivery Location |
|**deliveryLocationName**: string | Name of the Delivery Location |
|**reference**: string | Information concerning the Transaction |
|**requisitionerId**: string *(uuid)* | Unique Identifier of the Requisitioner |
|**requisitionerName**: string | Name of the Requisitioner |
|**requisitionDate**: string *(date-time)* | Date of the Requsition |
|**requiredDeliveryDate**: string <br> *(date-time)* | Required Delivery Date of the Requisition |
|**requisitionStatusId**: integer *(int32)* | Unique Identifier of the Requisition |
|**requisitionStatus**: string | Status of the Requisition |
|**requisitionNotes**: string | Comments about the Requisition |
|**buyerName**: string | Name of the Buyer |
|**buyerAddress1**: string | The first Address of the Buyer for shipping or billing purposes |
|**buyerAddress2**: string | The second Address of the Buyer for shipping or billing purposes |
|**buyerCity**: string | City of the Buyer |
|**buyerState**: string | State of the Buyer |
|**buyerZip**: string | Zip of the Buyer |
|**buyerCountry**: string | Country of the Buyer |
|**buyerContact**: string | Contact of the Buyer |
|**buyerContactEmail**: string | Contact Email of the Buyer |
|**buyerPhone**: string | Phone of the Buyer |
|**buyerFax**: string | Fax of the Buyer |
|**shippingName**: string | Name of the Shipping |
|**shippingAddress1**: string | The First Address for sending the Requisition |
|**shippingAddress2**: string | The Second Address for sending the Requisition |
|**shippingCity**: string | City for sending the Requisition |
|**shippingState**: string | State for sending the Requisition |
|**shippingZip**: string | Zip for sending the Requisition |
|**shippingCountry**: string | Country for sending the Requisition |
|**shippingContact**: string | Contact for sending the Requisition |
|**shippingContactEmail**: string | Contact Email for sending the Requisition |
|**shippingPhone**: string | Phone for sending the Requisition |
|**shippingPhoneExt**: string | Phone Extension for sending the Requisition |
|**shippingFax**: string | Fax for sending the Requisition |
|**discount**: number *(double)* | Discount for the Requisition |
|**discountTypeId**: integer *(int32)* | Unique Identifier of the Discount Type for the Requisition |
|**discountType**: string | Type of the discount for the Requisition |
|**salesTax**: string | Tax for the Sales |
|**salesTaxTypeId**: string | Unique Identifier of the Tax for the Sales |
|**shipping**: number *(double)*  | Number of the Shipping |
|**shippingTypeId**: integer *(int32)* | Unique Identifier of the Shipping Type |
|**shippingType**: string | Type of the Shipping |
|**dateSubmitted**: string *(date-time)* | Date when the Requisition was submitted |
|**dateCreated**: string *(date-time)* | Date when the Requisition was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Requsition |
|**createdByName**: string | Name of the user who created the Requisition |
|**lastUpdated**: string *(date-time)* | Last Date when the Requisition was updated |
|**lastUpdatedBy**: string *(date-time)* | Unique Identifier of the last user who updated the Requisition |
|**lastUpdatedByName**: string | Name of the last user who updated the Requisition |
|**requisitionSourceId**: integer *(int32)* | Unique Identifier of the Requisition |
|**requisitionSource**: string | Source of the Requisition |
|**notes**: string | Comments about the Requisition |
|**submittedBy**: string *(uuid)* | Unique Identifier of the user who submitted the Requisition |
|**submittedByName**: string | Name of the user who submitted the Requisition |
|**isCanceled**: boolean | Is the Requisition canceled or not? |
|**parAreaId**: string *(uuid)* | Unique Identifier of the PAR Area |
|**sourceFacilityId**: string *(uuid)* | Unique Identifier of the Facility Source |
|**sourceFacilityNo**: string | Number of the Facility Source |
|**sourceFacilityName**: string | Name of the Facility Source |
|**statusLastUpdated**: string <br> *(date-time)* | Last Date when the Status of the Facility Source was updated |
|**statusLastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Status of the Facility Source |
|**statusLastUpdatedByName**: string | Name of the last user who updated the Status of the Facility Source |
|**isConverted**: boolean | Is the Facility Source converted or not? |
|**cancelledRemainingQuantities<br>LastUpdated**: string *(date-time)* | Last Date when the Remaining Quantities of the Facility Source was canceled and updated |
|**cancelledRemaining<br>QuantitiesBy**: string *(uuid)* | Unique Identifier of the user who canceled the Remaining Quantities of the Facility Source |
|**cancelledRemaining<br>QuantitiesByName**: string | Name of the user who updated the Remaining Quantities of the Facility Source |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
  {
  "requisitionId": "00000000-0000-0000-0000-000000000000",
  "requisitionNo": "string",
  "requisitionTypeId": "integer (int32)",
  "requisitionType": "string",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "facilityNo": "string",
  "facilityName": "string",
  "patientId": "00000000-0000-0000-0000-000000000000",
  "departmentId": "00000000-0000-0000-0000-000000000000",
  "departmentNo": "string",
  "departmentName": "string",
  "deliveryLocationId": "00000000-0000-0000-0000-000000000000",
  "deliveryLocationNo": "string",
  "deliveryLocationName": "string",
  "reference": "string",
  "requisitionerId": "00000000-0000-0000-0000-000000000000",
  "requisitionerName": "string",
  "requisitionDate": "string (date-time)",
  "requiredDeliveryDate": "string (date-time)",
  "requisitionStatusId": "integer (int32)",
  "requisitionStatus": "string",
  "requisitionNotes": "string",
  "buyerName": "string",
  "buyerAddress1": "string",
  "buyerAddress2": "string",
  "buyerCity": "string",
  "buyerState": "string",
  "buyerZip": "string",
  "buyerCountry": "string",
  "buyerContact": "string",
  "buyerContactEmail": "string",
  "buyerPhone": "string",
  "buyerPhoneExt": "string",
  "buyerFax": "string",
  "shippingName": "string",
  "shippingAddress1": "string",
  "shippingAddress2": "string",
  "shippingCity": "string",
  "shippingState": "string",
  "shippingZip": "string",
  "shippingCountry": "string",
  "shippingContact": "string",
  "shippingContactEmail": "string",
  "shippingPhone": "string",
  "shippingPhoneExt": "string",
  "shippingFax": "string",
  "discount": "number (double)",
  "discountTypeId": "integer (int32)",
  "discountType": "string",
  "salesTax": "number (double)",
  "salesTaxTypeId": "integer (int32)",
  "salesTaxType": "string",
  "shipping": "number (double)",
  "shippingTypeId": "integer (int32)",
  "shippingType": "string",
  "dateSubmitted": "string (date-time)",
  "dateCreated": "string (date-time)",
  "createdBy": "00000000-0000-0000-0000-000000000000",
  "createdByName": "string",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByName": "string",
  "requisitionSourceId": "integer (int32)",
  "requisitionSource": "string",
  "notes": "string",
  "submittedBy": "00000000-0000-0000-0000-000000000000",
  "submittedByName": "string",
  "isCanceled": "boolean",
  "parAreaId": "00000000-0000-0000-0000-000000000000",
  "sourceFacilityId": "00000000-0000-0000-0000-000000000000",
  "sourceFacilityNo": "string",
  "sourceFacilityName": "string",
  "statusLastUpdated": "string (date-time)",
  "statusLastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "statusLastUpdatedByName": "string",
  "isConverted": "boolean",
  "cancelledRemainingQuantitiesLastUpdated": "string (date-time)",
  "cancelledRemainingQuantitiesBy": "00000000-0000-0000-0000-000000000000",
  "cancelledRemainingQuantitiesByName": "string"
  }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
  }
```

## Partially update the specified Requisition

### <span style="color: #F05D30">Path</span>
PATCH /odata/Requisitions({requisitionId})

### <span style="color: #F05D30">Description</span>
Partially updates the requisition specified by the requisition ID (applicable only for the **Standart** requisition type).

### <span style="color: #F05D30">Request Body</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:480px">Explanation</div>  |                      
|-----:|:-------|
|**reference**: string | Information concerning the Transaction |
|**notes**: string | Comments about the Requisition |
|**requisitionDate**: string *(date-time)* | Date of the Requsition |
|**requiredDeliveryDate**: <br> string *(date-time)* | Required Delivery Date of the Requisition |
|**shippingName**: string | Name of the Shipping |
|**shippingAddress1**: string | The First Address for sending the Requisition |
|**shippingAddress2**: string | The Second Address for sending the Requisition |
|**shippingCity**: string | City for sending the Requisition |
|**shippingState**: string | State for sending the Requisition |
|**shippingZip**: string | Zip for sending the Requisition |
|**shippingContact**: string | Contact for sending the Requisition |
|**shippingPhone**: string | Phone for sending the Requisition |
|**shippingPhoneExt**: string | Phone Extension for sending the Requisition |
|**shippingFax**: string | Fax for sending the Requisition |
|**shippingContactEmail**: string | Contact Email for sending the Requisition |
|**shippingCountry**: string | Country for sending the Requisition |
|**buyerName**: string | Name of the Buyer |
|**buyerAddress1**: string | The first Address of the Buyer for shipping or billing purposes |
|**buyerAddress2**: string | The second Address of the Buyer for shipping or billing purposes |
|**buyerCity**: string | City of the Buyer |
|**buyerState**: string | State of the Buyer |
|**buyerZip**: string | Zip of the Buyer | 
|**buyerContact**: string | Contact of the Buyer |
|**buyerPhone**: string | Phone of the Buyer |
|**buyerPhoneExt**: string | Phone Extension of the Buyer |
|**buyerFax**: string | Fax of the Buyer |
|**buyerContactEmail**: string | Contact Email of the Buyer |
|**buyerCountry**: string | Country of the Buyer |
|**requisitionNotes**: string | Comments about the Requisition |
|**discount**: number *(double)* | Discount for the Requisition |
|**discountTypeId**: integer *(int32)* | Unique Identifier of the Discount Type for the Requisition |
|**salesTax**: number *(double)* | Tax for the Sales |
|**salesTaxTypeId**: integer *(int32)* | Unique Identifier of the Tax for the Sales |
|**shipping**: number *(double)* | Number of the Shipping |
|**shippingTypeId**: integer <br> *(int32)* | Unique Identifier of the Shipping Type |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML <br> Request Example"
{
    "reference": "string",
    "notes": "string",
    "requisitionDate": "string (date-time)",
    "requiredDeliveryDate": "string (date-time)",
    "shippingName": "string",
    "shippingAddress1": "string",
    "shippingAddress2": "string",
    "shippingCity": "string",
    "shippingState": "string",
    "shippingZip": "string",
    "shippingContact": "string",
    "shippingPhone": "string",
    "shippingPhoneExt": "string",
    "shippingFax": "string",
    "shippingContactEmail": "string",
    "shippingCountry": "string",
    "buyerName": "string",
    "buyerAddress1": "string",
    "buyerAddress2": "string",
    "buyerCity": "string",
    "buyerState": "string",
    "buyerZip": "string",
    "buyerContact": "string",
    "buyerPhone": "string",
    "buyerPhoneExt": "string",
    "buyerFax": "string",
    "buyerContactEmail": "string",
    "buyerCountry": "string",
    "requisitionNotes": "string",
    "discount": "number (double)",
    "discountTypeId": "integer (int32)",
    "salesTax": "number (double)",
    "salesTaxTypeId": "integer (int32)",
    "shipping": "number (double)",
    "shippingTypeId": "integer (int32)"
    } 
```

### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**requisitionId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Requisition here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |


### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request. |

## Change the requisition status to ‘Open’

### <span style="color: #F05D30">Path</span>
POST /odata/Requisitions({requisitionId})/Submit

### <span style="color: #F05D30">Description</span>
Changes the requisition status to ‘Open’ if the specified requisition has at least one line item.


### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**requisitionId**: string *(uuid)*  <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Requisition here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version. |   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |


### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|  
|**400 Bad Request** | The request is incorrect.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**404 Not Found** | Specified ID is absent in the system. |
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request. |


## Cancel an existing Requisition

### <span style="color: #F05D30">Path</span>
POST /odata/Requisitions({requisitionId})/Cancel

### <span style="color: #F05D30">Description</span>
Cancels the requisition specified by the requisition ID.

### <span style="color: #F05D30">Request Parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**requisitionId**: string *(uuid)*  <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Requisition here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version. |   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* | Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |

### <span style="color: #F05D30">Responses</span>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|  
|**400 Bad Request** | The request is incorrect.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request. |



