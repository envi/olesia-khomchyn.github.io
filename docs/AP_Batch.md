# AP Batch
## Get the list of AP Batches

### <span style="color: #F05D30">Path</span>
GET /odata/Batches

### <span style="color: #F05D30">Description</span>
Returns list of AP Batches within a logged organization. You can filter the results by the strict match using the ```$filter``` parameter–entity eq ‘string’. Or filter the results by the partial match using ```$filter```=contains parameter–contains(entity, ‘string’).)

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**api-version**: string default: 1.0 <br> *in header*|The requested API version.|    
|**$filter**: string <br> *in query* | Restricts the set of items returned. The maximum number of expressions is 100.|  
|**$orderby**: string <br> *in query* | Specifies the order in which items are returned. The maximum number of expressions is 5.|
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
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
|**apBatchId**: string *(uuid)* | Unique Identifier of the Account Payable Batch |
|**batchNo**: string | Identification Number of the Batch |
|**reference**: string | Information concerning the Transaction |
|**batchStatusId**: integer *(int32)* | Unique Identifier of the Batch Status |
|**batchStatus**: string | Status of the Batch |
|**batchTotal**: number *(double)* | Total of the Batch |
|**invoiceCount**: integer *(int32)* | Count of the Invoices |
|**isScheduledExporting**: boolean | Is Exporting of the Batch scheduled or not? |
|**lastExportDate**: string *(date-time)* | Last Date when the Batch was exported |
|**dateCreated**: string *(date-time)* | Date when the Batch was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Batched Invoice |
|**createdByUserName**: string | Name of the user who created the Batched Invoice |
|**lastUpdated**: string *(date-time)* | Last Date when the Batched Invoice was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Batched Invoice |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Batched Invoice |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
    "items": [
    {
      "apBatchId": "00000000-0000-0000-0000-000000000000",
      "batchNo": "string",
      "reference": "string",
      "batchStatusId": "integer (int32)",
      "batchStatus": "string",
      "batchTotal": "number (double)",
      "invoiceCount": "integer (int32)",
      "isScheduledExporting": "boolean",
      "lastExportDate": "string (date-time)",
      "dateCreated": "string (date-time)",
      "createdBy": "00000000-0000-0000-0000-000000000000",
      "createdByUserName": "string",
      "lastUpdated": "string (date-time)",
      "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
      "lastUpdatedByUserName": "string"
    }
    ],
    "nextPageLink": "string",
    "count": "integer (int64)"
    }
```

## Create a new AP Batch

### <span style="color: #F05D30">Path</span>
POST /odata/Batches

### <span style="color: #F05D30">Description</span>
Creates a new AP Batch within a logged organization.

### <span style="color: #F05D30">Request Body</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:420px">Explanation</div>  |                      
|-----:|:-------|
|**batchNo**: string | Identification Number of the Batch |
|**reference**: string | Information concerning the Transaction |


``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML <br> Request Example"
{
      "batchNo": "string",
      "reference": "string"
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
|**api-version**: string default: 1.0 <br> *in header*|The requested API version.|      
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**204 No Content** | No Content |    
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

## Get the specified AP Batch

### <span style="color: #F05D30">Path</span>
GET /odata/Batches({batchId})

### <span style="color: #F05D30">Description</span>
Returns details of the batch specified by ID.

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.



### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**batchId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the batch here. |
|**api-version**: string default: 1.0 <br> *in header*|The requested API version.|      
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|


### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**200 OK** | OK |    
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
|**apBatchId**: string *(uuid)* | Unique Identifier of the Account Payable Batch |
|**batchNo**: string | Identification Number of the Batch |
|**reference**: string | Information concerning the Transaction |
|**batchStatusId**: integer *(int32)* | Unique Identifier of the Batch Status |
|**batchStatus**: string | Status of the Batch |
|**batchTotal**: number *(double)* | Total of the Batch |
|**invoiceCount**: integer *(int32)* | Count of the Invoices |
|**isScheduledExporting**: boolean | Is Exporting of the Batch scheduled or not? |
|**lastExportDate**: string *(date-time)* | Last Date when the Batch was exported |
|**dateCreated**: string *(date-time)* | Date when the Batch was created |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created the Batched Invoice |
|**createdByUserName**: string | Name of the user who created the Batched Invoice |
|**lastUpdated**: string *(date-time)* | Last Date when the Batched Invoice was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Batched Invoice |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Batched Invoice |

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
{
    "apBatchId": "00000000-0000-0000-0000-000000000000",
    "batchNo": "string",
    "reference": "string",
    "batchStatusId": "integer (int32)",
    "batchStatus": "string",
    "batchTotal": "number (double)",
    "invoiceCount": "integer (int32)",
    "isScheduledExporting": "boolean",
    "lastExportDate": "string (date-time)",
    "dateCreated": "string (date-time)",
    "createdBy": "00000000-0000-0000-0000-000000000000",
    "createdByUserName": "string",
    "lastUpdated": "string (date-time)",
    "lastUpdatedBy": "00000000-0000-0000-0000-000000000000",
    "lastUpdatedByUserName": "string"
    }
    
```

## Get the specified AP Batched Invoice

### <span style="color: #F05D30">Path</span>
GET /odata/Batches({batchId})/invoices

### <span style="color: #F05D30">Description</span>
Returns paged list of the existing invoices within Batch specified by ID.

!!! note 

    This endpoint does not support logical operators (**in**, **gt**, **ge**, **lt**, **le**) for data filtering.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**batchId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Batched Invoice here. |
|**api-version**: string default: 1.0 <br> *in header*|The requested API version.|     
|**$filter**: string <br> *in query* | Restricts the set of items returned. The maximum number of expressions is 100.|  
|**$orderby**: string <br> *in query* | Specifies the order in which items are returned. The maximum number of expressions is 5.|
|**$search**: string <br> *in query*  | Picks the value in all possible fields.|  
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
|**apMatchedInvoiceId**: string *(uuid)* | Unique Identifier of the Account Payable Matched Invoice |
|**purchaseOrderId**: string *(uuid)* | Unique Identifier of the Purchase Order |
|**purchaseOrderNo**: string | Number of the Purchase Order |
|**sequenceNo**: integer *(int32)* | Number of the Sequence |
|**poType**: string | Type of the Purchase Order (Standard, Return, or Capital) |
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
|**matchedInvoiceStatusId**: integer <br> *(int32)* | Unique Identifier of the Matched Invoice Status |
|**matchedInvoiceStatus**: string | Status of the Matched Invoice |
|**vendorRemitToId**: string *(uuid)* | Unique Identifier of the Vendor Remit-to |
|**remitToNo**: string | Number of the Remit-to |
|**remitToDescription**: string | Description of the Remit-to |
|**remitToVendorNo**: string | Vendor Number of the Remit-to |
|**creditCardIDId**: string *(uuid)* | Unique Identifier of the Credit Card |
|**creditCardID**: string | Identifier of the Credit Card |
|**creditCardIDDescription**: string | Description of the Credit Card |
|**reference**: string | Information concerning the Transaction |
|**notes**: string | Comments about the Batched Invoice |
|**invoiceDate**: string *(date-time)* | Date of the Invoice |
|**invoiceDueDate**: string *(date-time)*  | Expiration Date of the Invoice |
|**trackingCode**: string | Code for Tracking |
|**invoiceValidationTotal**: number *(double)* | Validation Total of the Invoice |
|**cerNoId**: string *(uuid)* | Unique Identifier of the Capital Expenditure Request Number |
|**cerNo**: string | Number of the Capital Expenditure Request Number |
|**cerNoDescription**: string | Description of the Capital Expenditure Request Number |
|**discountAmount**: number *(double)* | Amount of the Discount |
|**taxAmount**: number *(double)* | Amount of the Tax |
|**shippingAmount**: number *(double)* | Amount of the Shipping |
|**taxExpenseGLCode**: string | General Ledger Code of the Tax Expense |
|**taxAccrualGLCode**: string | General Ledger Code of the Tax Accrual |
|**discountGLCode**: string | General Ledger Code of the Discount |
|**taxExpenseAmount**: number *(double)* | Amount of the Tax Expense |
|**apBatchId**: string *(uuid)* | Unique Identifier of the Account Payable Batch |
|**apBatchNo**: string | Number of the Account Payable Batch |
|**taxCode**: string | Code of the Tax |
|**receivedInvoiceId**: string *(uuid)* | Unique Identifier of the Received Invoice |
|**offset**: number *(double)* | Canceled accounting entry |
|**offsetGLCode**: string | General Ledger Code of the canceled accounting entry |
|**createdBy**: string *(uuid)* | Unique Identifier of the user who created Batched Invoice |
|**createdByUserName**: string | Name of the user who created Batched Invoice |
|**dateCreated**: string *(date-time)* | Date when the Batched Invoice was created |
|**lastUpdated**: string *(date-time)* | Last Date when the Batched Invoice was updated |
|**lastUpdatedBy**: string *(uuid)* | Unique Identifier of the last user who updated the Batched Invoice |
|**lastUpdatedByUserName**: string | Name of the last user who updated the Batched Invoice |
|**dateSubmitted**: string *(date-time)* | Date when the Batched Invoice was submitted |
|**submittedBy**: string *(uuid)* | Unique Identifier of the user who submitted the Batched Invoice |
|**submittedByUserName**: string | Name of the user who submitted the Batched Invoice |

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
      "submittedByUserName": "string",
    }
    ],
    "nextPageLink": "string",
    "count": "integer (int64)"
    }
    
```

## Add Invoice to Batch

### <span style="color: #F05D30">Path</span>
POST /odata/Batches({batchId})/Invoices

### <span style="color: #F05D30">Description</span>
Adds Invoice with the ‘Vouchered’ status to an existed Batch within a logged organization. After adding to the Batch, added Invoice changes its Invoice status to ‘Batched’.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**batchId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Batched Invoice here. |
|**api-version**: string default: 1.0 <br> *in header*|The requested API version.|     
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML <br> Request Example"
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
### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**204 No Content**| No Content |      
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|


### <span style="color: #F05D30">Custom Errors</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**400 Bad Request** | Invoice is **NOT** in the 'Vouchered' status |

``` json title="Response Example"

Only Vouchered Invoices can be added to the Batch.

```

## Change Batch Status to ‘Exported’

### <span style="color: #F05D30">Path</span>
POST /odata/Batches({batchId})/Export

### <span style="color: #F05D30">Description</span>
Changes Batch Status to ‘Exported’ when the specified Batch has at least one Invoice.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**batchId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Batched Invoice here. |
|**api-version**: string default: 1.0 <br> *in header*|The requested API version.|     
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**204 No Content**| No Content |      
|**400 Bad Request**|This batch cannot be exported because it does not contain any invoice.|
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

## Change AP Batch Status to ‘Queued’

### <span style="color: #F05D30">Path</span>
POST /odata/Batches({batchId})/SubmitToQueued

### <span style="color: #F05D30">Description</span>
Submits AP Batch to the 'Queued' status.

### <span style="color: #F05D30">Request Parameters</span>
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**batchId**: string *(uuid)* <br> <span style="color: #F05D30">**required**</span> <br> *in path* | Enter the ID of the Batched Invoice here. |
|**api-version**: string default: 1.0 <br> *in header*|The requested API version.|     
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication.|

### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**204 No Content**| No Content |      
|**400 Bad Request**|Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**|Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**|User doesn’t have appropriate privileges.|
|**500 Internal Server Error**|Server encountered an unexpected condition that prevented it from fulfilling the request.|

### <span style="color: #F05D30">Custom Errors</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:380px">Explanation</div>|                      
|-----:|:-------|
|**400 Bad Request** | Specified batch exists in the 'Queued' status. |

``` json title="Response Example"

This batch cannot be submitted to queued because it already exists in the 'Queued' batch status.

```
