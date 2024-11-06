
## Get the list of Matched Invoices

### <span style="color: #F05D30">Path</span>
GET /odata/MatchedInvoices

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing Matched Invoices within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

### <span style="color: #F05D30">Request parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition. |  
|**$orderby**: string <br> *in query* | Sorts the results.|
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
|**apMatchedInvoiceId**: string *(uuid)* | Unique Identifier of the Account Payable Matched Invoice |
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**purchaseOrderNo**: string | Number of the Purchase Order |
|**sequenceNo**: integer *(int32)* | Number of the Sequence |
|**poType**: string | Type of the Purchase Order |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**invoiceNo**: string | Number of the Invoice |
|**matchedInvoiceStatusId**: <br> integer *(int32)*  | Unique Identifier of the Matched Invoice status |
|**matchedInvoiceStatus**: string | Status of the Matched Invoice |
|**vendorRemitToId**: string *(uuid)* | Unique Identifier of the Vendor Remit-to |
|**remitToNo**: string | Number of the Remit-to |
|**remitToDescription**: string | Description of the Remit-to |
|**remitToVendorNo**: string | Vendor Number of the Remit-to |
|**creditCardIDId**: string *(uuid)* | Unique Identifier of the Credit Card |
|**creditCardID**: string | Identifier of the Credit Card |
|**creditCardIDDescription**: string | Description of the Credit Card |
|**reference**: string | Information concerning the Transaction |
|**notes**: string | Comments about the Matched Invoice |
|**invoiceDate**: string *(date-time)* | Date of the Invoice |
|**invoiceDueDate**: string <br> *(date-time)* | Expiration Date of the Invoice |
|**trackingCode**: string | Code for Tracking |
|**invoiceValidationTotal**: number <br> *(double)* | Validation Total of the Invoice |
|**cerNoId**: string *(uuid)* | Unique Identifier of the Capital Expenditure Request Number |
|**cerNo**: string | Number of the Capital Expenditure Request Number |
|**cerNoDescription**: string | Description of the Capital Expenditure Request Number |
|**discountAmount**: number *(double)* | Amount of the Discount |
|**taxAmount**: number *(double)*  | Amount of the Tax |
|**shippingAmount**: number <br> *(double)* | Amount of the Shipping |
|**taxExpenseGLCode**: string | General Ledger Code of the Tax Expense |
|**taxAccrualGLCode**: string | General Ledger Code of the Tax Accrual |
|**discountGLCode**: string | General Ledger Code of the Discount |
|**taxExpenseAmount**: number <br> *(double)*  | Amount of the Tax Expense |
|**apBatchId**: string *(uuid)* | Unique Identifier of the Account Payable Batch |
|**apBatchNo**: string | Number of the Account Payable Batch |
|**taxCode**: string | Code of the Tax |
|**receivedInvoiceId**: string *(uuid)* | Unique Identifier of the Received Invoice |
|**offset**: number *(double)* | Canceled accounting entry |
|**offsetGLCode**: string | General Ledger Code of the canceled accounting entry |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created Matched Invoice |
|**createdByUserName**: string | Name of the user who created Matched Invoice |
|**dateCreated**: string *(date-time)* | Date when the Matched Invoice was created |
|**lastUpdated**: string *(date-time)* | Last Date when the Matched Invoice was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Matched Invoice |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Matched Invoice |
|**dateSubmitted**: string *(date-time)* | Date when the Matched Invoice was submitted |
|**submittedBy**: string *(uuid)* | Unique Identifier of the user who submitted the Matched Invoice |
|**submittedByUserName**: string | Name of the user who submitted the Matched Invoice |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "apMatchedInvoiceId": "00000000-0000-0000-0000-000000000000",
      "purchaseOrderId": "00000000-0000-0000-0000-000000000000",
      "purchaseOrderNo": "string",
      "sequenceNo": "integer (int32)",
      "poType": "string",
      "facilityId": "00000000-0000-0000-0000-000000000000",
      "facilityNo": "string",
      "facilityName": "string",
      "locationId": "00000000-0000-0000-0000-000000000000",
      "locationNo": "string",
      "locationName": "string",
      "vendorId": "00000000-0000-0000-0000-000000000000",
      "vendorNo": "string",
      "vendorName": "string",
      "invoiceNo": "string",
      "matchedInvoiceStatusId": "integer (int32)",
      "matchedInvoiceStatus": "string",
      "vendorRemitToId": "00000000-0000-0000-0000-000000000000",
      "remitToNo": "string",
      "remitToDescription": "string",
      "remitToVendorNo": "string",
      "creditCardIDId": "00000000-0000-0000-0000-000000000000",
      "creditCardID": "string",
      "creditCardIDDescription": "string",
      "reference": "string",
      "notes": "string",
      "invoiceDate": "string (date-time)",
      "invoiceDueDate": "string (date-time)",
      "trackingCode": "string",
      "invoiceValidationTotal": "number (double)",
      "cerNoId": "00000000-0000-0000-0000-000000000000",
      "cerNo": "string",
      "cerNoDescription": "string",
      "discountAmount": "number (double)",
      "taxAmount": "number (double)",
      "shippingAmount": "number (double)",
      "taxExpenseGLCode": "string",
      "taxAccrualGLCode": "string",
      "discountGLCode": "string",
      "taxExpenseAmount": "number (double)",
      "apBatchId": "00000000-0000-0000-0000-000000000000",
      "apBatchNo": "string",
      "taxCode": "string",
      "receivedInvoiceId": "00000000-0000-0000-0000-000000000000",
      "offset": "number (double)",
      "offsetGLCode": "string",
      "createdBy": "00000000-0000-0000-0000-000000000000",
      "createdByUserName": "string",
      "dateCreated": "string (date-time)",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByUserName": "string",
      "dateSubmitted": "string (date-time)",
      "submittedBy": "00000000-0000-0000-0000-000000000000",
      "submittedByUserName": "string"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```

## Get the specified Matched Invoice

### <span style="color: #F05D30">Path</span>
GET /odata/MatchedInvoices({matchedInvoiceId})

### <span style="color: #F05D30">Description</span>
Returns the details of the Matched Invoice specified by ID.

### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**matchedInvoiceId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Matched Invoice here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

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
|**apMatchedInvoiceId**: string *(uuid)* | Unique Identifier of the Account Payable Matched Invoice |
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**purchaseOrderNo**: string | Number of the Purchase Order |
|**sequenceNo**: integer *(int32)* | Number of the Sequence |
|**poType**: string | Type of the Purchase Order |
|**facilityId**: string *(uuid)* | Unique Identifier of the Facility |
|**facilityNo**: string | Identification Number of the Facility |
|**facilityName**: string | Name of the Facility |
|**locationId**: string *(uuid)* | Unique Identifier of the Location |
|**locationNo**: string | Identification Number of the Location |
|**locationName**: string | Name of the Location |
|**vendorId**: string *(uuid)* | Unique Identifier of the Vendor |
|**vendorNo**: string | Code of the Supplier who sells products |
|**vendorName**: string | Name of the Vendor |
|**invoiceNo**: string | Number of the Invoice |
|**matchedInvoiceStatusId**: <br> integer *(int32)*  | Unique Identifier of the Matched Invoice status |
|**matchedInvoiceStatus**: string | Status of the Matched Invoice |
|**vendorRemitToId**: string *(uuid)* | Unique Identifier of the Vendor Remit-to |
|**remitToNo**: string | Number of the Remit-to |
|**remitToDescription**: string | Description of the Remit-to |
|**remitToVendorNo**: string | Vendor Number of the Remit-to |
|**creditCardIDId**: string *(uuid)* | Unique Identifier of the Credit Card |
|**creditCardID**: string | Identifier of the Credit Card |
|**creditCardIDDescription**: string | Description of the Credit Card |
|**reference**: string | Information concerning the Transaction |
|**notes**: string | Comments about the Matched Invoice |
|**invoiceDate**: string *(date-time)* | Date of the Invoice |
|**invoiceDueDate**: string <br> *(date-time)* | Expiration Date of the Invoice |
|**trackingCode**: string | Code for Tracking |
|**invoiceValidationTotal**: number <br> *(double)* | Validation Total of the Invoice |
|**cerNoId**: string *(uuid)* | Unique Identifier of the Capital Expenditure Request Number |
|**cerNo**: string | Number of the Capital Expenditure Request Number |
|**cerNoDescription**: string | Description of the Capital Expenditure Request Number |
|**discountAmount**: number *(double)* | Amount of the Discount |
|**taxAmount**: number *(double)*  | Amount of the Tax |
|**shippingAmount**: number <br> *(double)* | Amount of the Shipping |
|**taxExpenseGLCode**: string | General Ledger Code of the Tax Expense |
|**taxAccrualGLCode**: string | General Ledger Code of the Tax Accrual |
|**discountGLCode**: string | General Ledger Code of the Discount |
|**taxExpenseAmount**: number <br> *(double)*  | Amount of the Tax Expense |
|**apBatchId**: string *(uuid)* | Unique Identifier of the Account Payable Batch |
|**apBatchNo**: string | Number of the Account Payable Batch |
|**taxCode**: string | Code of the Tax |
|**receivedInvoiceId**: string *(uuid)* | Unique Identifier of the Received Invoice |
|**offset**: number *(double)* | Canceled accounting entry |
|**offsetGLCode**: string | General Ledger Code of the canceled accounting entry |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created Matched Invoice |
|**createdByUserName**: string | Name of the user who created Matched Invoice |
|**dateCreated**: string *(date-time)* | Date when the Matched Invoice was created |
|**lastUpdated**: string *(date-time)* | Last Date when the Matched Invoice was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Matched Invoice |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Matched Invoice |
|**dateSubmitted**: string *(date-time)* | Date when the Matched Invoice was submitted |
|**submittedBy**: string *(uuid)* | Unique Identifier of the user who submitted the Matched Invoice |
|**submittedByUserName**: string | Name of the user who submitted the Matched Invoice |


``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "apMatchedInvoiceId": "00000000-0000-0000-0000-000000000000",
  "purchaseOrderId": "00000000-0000-0000-0000-000000000000",
  "purchaseOrderNo": "string",
  "sequenceNo": "integer (int32)",
  "poType": "string",
  "facilityId": "00000000-0000-0000-0000-000000000000",
  "facilityNo": "string",
  "facilityName": "string",
  "locationId": "00000000-0000-0000-0000-000000000000",
  "locationNo": "string",
  "locationName": "string",
  "vendorId": "00000000-0000-0000-0000-000000000000",
  "vendorNo": "string",
  "vendorName": "string",
  "invoiceNo": "string",
  "matchedInvoiceStatusId": "integer (int32)",
  "matchedInvoiceStatus": "string",
  "vendorRemitToId": "00000000-0000-0000-0000-000000000000",
  "remitToNo": "string",
  "remitToDescription": "string",
  "remitToVendorNo": "string",
  "creditCardIDId": "00000000-0000-0000-0000-000000000000",
  "creditCardID": "string",
  "creditCardIDDescription": "string",
  "reference": "string",
  "notes": "string",
  "invoiceDate": "string (date-time)",
  "invoiceDueDate": "string (date-time)",
  "trackingCode": "string",
  "invoiceValidationTotal": "number (double)",
  "cerNoId": "00000000-0000-0000-0000-000000000000",
  "cerNo": "string",
  "cerNoDescription": "string",
  "discountAmount": "number (double)",
  "taxAmount": "number (double)",
  "shippingAmount": "number (double)",
  "taxExpenseGLCode": "string",
  "taxAccrualGLCode": "string",
  "discountGLCode": "string",
  "taxExpenseAmount": "number (double)",
  "apBatchId": "00000000-0000-0000-0000-000000000000",
  "apBatchNo": "string",
  "taxCode": "string",
  "receivedInvoiceId": "00000000-0000-0000-0000-000000000000",
  "offset": "number (double)",
  "offsetGLCode": "string",
  "createdBy": "00000000-0000-0000-0000-000000000000",
  "createdByUserName": "string",
  "dateCreated": "string (date-time)",
  "lastUpdated": "string (date-time)",
  "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
  "lastUpdatedByUserName": "string",
  "dateSubmitted": "string (date-time)",
  "submittedBy": "00000000-0000-0000-0000-000000000000",
  "submittedByUserName": "string"
}
```

## Get the list of Matched Invoice Items for the specified Matched Invoice

### <span style="color: #F05D30">Path</span>
GET /odata/MatchedInvoices({matchedInvoiceId})/matchedInvoiceItems

### <span style="color: #F05D30">Description</span>
Returns the paged list of the existing matched invoice items within a matched Invoice specified by ID. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.


### <span style="color: #F05D30">Request parameters</span>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**matchedInvoiceId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Matched Invoice here. |
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|
|**$filter**: string <br> *in query* | Filters the results, based on a Boolean condition. |  
|**$orderby**: string <br> *in query* | Sorts the results.|
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
|**apMatchedInvoiceItemId**: string *(uuid)* | Unique Identifier of the Account Payable Matched Invoice Item |
|**matchedInvoiceItemNo**: integer <br> *(int32)* | Number of the Matched Invoice Item |
|**matchedInvoiceId**: string *(uuid)* | Unique Identifier of the Matched Invoice |
|**matchedInvoiceNo**: string | Number of the Matched Invoice |
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**purchaseOrderNo**: string | Number of the Purchase Order |
|**poReceiptItemId**: string *(uuid)* | Unique Identifier of the Purchase Order Receipt Item |
|**returnItemId**: string *(uuid)* | Unique Identifier of the Return Item |
|**invoiceQuantity**: integer <br> *(int32)* | Specified Quantity in the Invoice |
|**invoiceUOM**: string | Specified Unit of Measure in the Invoice |
|**invoiceConversionFactor**: integer <br> *(int32)* | Specified Number of Stock Keeping Units in another Unit of Measure in the Invoice |
|**invoicePrice**: number <br> *(double)* | Specified Price in the Invoice |
|**notes**: string | Comments about the Matched Invoice Item |
|**departmentGLCode**: string | General Ledger Code of the Department |
|**glCode**: string | General Ledger Code |
|**lineItemTypeId**: integer <br> *(int32)* | Unique Identifier of the Line Item Type |
|**lineItemType**: string | Type of the Line Item |
|**qtyApprovalTypeId**: integer <br> *(int32)*  | Unique Identifier of the Quantity Approval Type |
|**qtyApprovalType**: string | Approval Type of the Quantity |
|**priceApprovalTypeId**: integer <br> *(int32)* | Unique Identifier of the Price Approval Type |
|**priceApprovalType**: string | Approval Type of the Price |
|**inventoryNo**: string | Identification code of the Inventory Item |
|**inventoryDescription**: string | Description of the Inventory Item |
|**vendorItemNo**: string | Code that is used by the Vendor for the Item identification |
|**manufacturerName**: string | Name of the Manufacturer |
|**manufacturerItemNo**: string | Number of the Manufacturer Item |
|**dateCreated**: string *(date-time)* | Date when the Matched Invoice Item was added |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Matched Invoice Item |
|**createdByName**: string | Name of the user who created the Matched Invoice Item |
|**lastUpdated**: string *(date-time)* | Last Date when the Matched Invoice Item was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Matched Invoice Item |
|**lastUpdatedByName**: string | Name of the last user who updated the Matched Invoice Item |
|**isTaxable**: boolean | Is the Matched Invoice Item taxable or not? |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
  "items": [
    {
      "apMatchedInvoiceItemId": "00000000-0000-0000-0000-000000000000",
      "matchedInvoiceItemNo": "integer (int32)",
      "matchedInvoiceId": "00000000-0000-0000-0000-000000000000",
      "matchedInvoiceNo": "string",
      "purchaseOrderId": "00000000-0000-0000-0000-000000000000",
      "purchaseOrderNo": "string",
      "poReceiptItemId": "00000000-0000-0000-0000-000000000000",
      "returnItemId": "00000000-0000-0000-0000-000000000000",
      "invoiceQuantity": "integer (int32)",
      "invoiceUOM": "string",
      "invoiceConversionFactor": "integer (int32)",
      "invoicePrice": "number (double)",
      "notes": "string",
      "departmentGLCode": "string",
      "glCode": "string",
      "lineItemTypeId": "integer (int32)",
      "lineItemType": "string",
      "qtyApprovalTypeId": "integer (int32)",
      "qtyApprovalType": "string",
      "priceApprovalTypeId": "integer (int32)",
      "priceApprovalType": "string",
      "inventoryNo": "string",
      "inventoryDescription": "string",
      "vendorItemNo": "string",
      "manufacturerName": "string",
      "manufacturerItemNo": "string",
      "dateCreated": "string (date-time)",
      "createdBy": "00000000-0000-0000-0000-000000000000",
      "createdByName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByName": "string",
      "isTaxable": "boolean"
    }
  ],
  "nextPageLink": "string",
  "count": "integer (int64)"
}
```





