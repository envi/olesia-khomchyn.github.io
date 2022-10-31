# Usages

## Create new usages

### <span style="color: #F05D30">Path</span>
POST /odata/Usages/BulkAdd

### <span style="color: #F05D30">Description</span>
Creates new usages within a logged organization.

### <span style="color: #F05D30">Request Body</span>
For adding procedure(s) to usage(s)
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:420px">Explanation</div>  |                      
|-----:|:-------|
|**facilityNo**: string <br> <span style="color: #F05D30">**required**</span> <br>  *in formData* | Identification Number of the Facility. <br> **If not provided**: 400 Bad Request. |
|**usageDate**: string <br> *in formData* | Date of the Usage. <br> **If not provided**: Date according to the user Time Zone. |
|**departmentNo**: string <br> <span style="color: #F05D30">**required**</span> <br>  *in formData* | Number of the Department. <br> **If not provided**: User Default Department if it is set and matches with user Default Facility. Otherwise, ```none```. 
|**patientNo**: string <br> *in formData* | Number of the Patient. <br> **If not provided**: ```none```. |
|**reference**: string <br> *in formData* | Information concerning the Usage.<br> **If not provided**: Empty. |
|**caseNo**: string <br> *in formData* | Number of the Case. <br> **If not provided**: Empty. |
|**trackingCode**: string <br> *in formData* | Code for Tracking. <br> **If not provided**: Empty. |
|**physicianNo**: string <br> *in formData* | Number of the Physician. <br> **If not provided**: The ```none``` value if it is not specified or it doesn't match the specified Facility. |
|**usageType**: string <br> *in formData* | Standard <br> **Auto-Populated** |
|**source**: string <br> *in formData* | Auto <br> **Auto-Populated** |


``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML <br> Request Example"
{
  "facilityNo": "string",
  "usageDate": "string (date-time)",
  "departmentNo": "string",
  "patientNo": "string",
  "reference": "string",
  "caseNo": "string",
  "trackingCode": "string",
  "physicianNo": "string",
  "usageType": "string",
  "source": "string",
}
```

``` json title="Request Example"
{
 "usageItems":[
  {
    "usageId": "UsageId1"
  },
  {
    "usageId": "UsageId2"
  },
  {
    "usageId": "UsageId3"
  }
 ]
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
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |

### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request.|

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
"00000000-0000-0000-0000-000000000000"

```

## Submit usages

### <span style="color: #F05D30">Path</span>
POST /odata/Usages/BulkSubmit

### <span style="color: #F05D30">Description</span>
Submits usages within a logged organization.

### <span style="color: #F05D30">Request Body</span>
For usage(s) submition
<style>
td, th {
   border: none!important;
}
</style>
|  <div style="width:200px">Parameter</div>  |  <div style="width:420px">Explanation</div>  |                      
|-----:|:-------|
|**usageId**: string <br> <span style="color: #F05D30">**required**</span> <br>  *in formData* | Unique Identifier of the the Usage. <br> **If not provided**: 400 Bad Request. |

``` json title="Request Content-types: APPLICATION/JSON, APPLICATION/XML <br> Request Example"
{
  "usageId": "string(uuid)",
}
```

``` json title="Request Example"
{
 "usageIds":
 [
  {
    "usageId": "UsageId1"
  },
  {
    "usageId": "UsageId2"
  },
  {
    "usageId": "UsageId3"
  }
 ]
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
|**api-version**: string default: 1.0 <br> *in header*| The requested API version.|   
|**Authorization**: string default: <br> Bearer access_token <br> *in header* |Specify the type of the token (bearer) and then insert the ```access_token```, which was obtained during authentication. |



### <span style="color: #F05D30">Responses</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**200 OK**|OK|      
|**400 Bad Request**| Incorrect input data or organization ID does not match with the organization ID user is logged in.|
|**401 Unauthorized**| Incorrect specified ```access_token``` or ```access_token``` got expired.|
|**403 Forbidden**| User doesn’t have appropriate privileges.|
|**500 Internal Server Error**| Server encountered an unexpected condition that prevented it from fulfilling the request.|

``` json title="Response Content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
"object"

```
### <span style="color: #F05D30">Custom Errors</span>
<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Response </div>|<div style="width:420px">Explanation</div>|                      
|-----:|:-------|
|**400 Bad Request** | There is at least one Line Item with the Quantity "0" (zero) on the Line Items tab.|

``` json title="Response Example"
At least one line item has zero quantity.
```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Usage contains Line Item with a negative Quantity and required Tracking.|

``` json title="Response Example"

At least one item with tracking values has negative quantity.

```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Usage has been already submitted by another user.|

``` json title="Response Example"

Usage has been already processed, submitted, or canceled.

```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Usage has completed Line Item with Tracking by Serial Number and Quantity/CF larger than 1.|

``` json title="Response Example"

At least one line item requires serial number tracking and has a quantity larger than one.

```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Usage contains Line Item with not unique Serial Number. |

``` json title="Response Example"

Usage contains not unique serial number. 

```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Usage contains Line Item with Tracking by Expiration Date and Quantity larger than Expiration Date quantity. |

``` json title="Response Example"

Line items with tracking by Expiration Date have insufficient quantity.

```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Usage contains Line Item with Tracking by Lot No with Quantity larger than Lot No Quantity. |

``` json title="Response Example"

Line items with tracking by Lot No have insufficient quantity.

```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Usage contains Line Item with Tracking by Serial No with Quantity larger than Serial No Quantity. |

``` json title="Response Example"

Line items with tracking by Serial No have insufficient quantity.

```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Some arithmetic overflow errors occurred during the Usage submission. |

``` json title="Response Example"

Arithmetic Overflow Error(s) occurred during submission process.

```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Usage contains at least one ‘Implant’ Line Item with **Implant Completed**—**No**. |

``` json title="Response Example"

Arithmetic Overflow Error(s) occurred during submission process.

```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Usage contains failed Line Item(s).|

``` json title="Response Example"

Usage has failed line item(s).

```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Patient field is not specified but Usage requires a selected Facility option of the Patient.|

``` json title="Response Example"

Usage requires a patient.

```


<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Case Number is not unique within a Facility or is not set.|

``` json title="Response Example"

Usage requires a unique case number.

```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Department field of the Usage is not specified (“None”).|

``` json title="Response Example"

Department is required.

```

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px"> </div>|<div style="width:420px"></div>|                      
|-----:|:-------|
|**400 Bad Request** | Patient, Procedure, Physician, Case Number and Schedule fields of the Usage are not specified and the 'Usage requires a procedure', 'Usage requires a doctor', 'Usage requires a case number' and 'Usage requires a schedule number', ‘Usage requires a patient’ facility settings are enabled. |

``` json title="Response Example"

Usage requires a case number.

```

``` json title="Response Example"

Usage requires a doctor.

```


``` json title="Response Example"

Usage requires a procedure.

```

``` json title="Response Example"

Usage requires a schedule number.

```