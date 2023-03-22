Refine the results of your query by using query options.

- [$search](#search)
- [$top and $skip](#top-and-skip)
- [$filter](#filter)
- [$orderby](#orderby)
- [$format](#format)

This section will help you go through query options supported by Envi OData API and common scenarios for using them. Envi OData API is based on OData protocol v4.0 but has its custom implementation, so currently, not all query options are supported. Envi API allows using query options for all resources that return lists of entities, except those for which actions or functions are applied to OData.

Also, Envi OData API defines a set of logical operators that evaluate True or False. Logical operators are typically used in the $filter query option to filter the set of resources. For more details, go to the [$filter](#filter) article. The concept of logical operators is simple. They allow the program to make a decision based on multiple conditions. Each operand is considered a condition that can be evaluated True or False. These operands can combine multiple Boolean expressions or values and provide a single Boolean output.

## <span style="color: #F05D30">$search</span> 

The ``` $search ```  system query option allows searching through all available entity fields in a collection of resources that are addressed by the request URL. The expression specified by ``` $search ```  consists of the search value only, which is treated as the ``` like ```  expression.

- The expression of the item evaluates True for at least one of the fields included in the response.
- The expression of resources evaluates False or Null for all searchable fields omitted in the response.


``` title="Request Example"
https://<HOSTNAME>/odata/Inventory?$search="inv" 
    
```
(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

The following request example filters target records set based on the ``` inv ```  search value. If any searchable fields contain ``` inv```, the entity is included in the response.

Since no ``` $top ```  option is specified, only the first 20 records are included in the response. Except for the ``` $top```  and ``` $skip```  options, ``` @odata.nextLink``` includes the ``` $search``` option.


``` json title="Response example"
{
    "@odata.context": "https://api-demo.envi.net/odata/$metadata#Inventory",
    "@odata.count": 174,
    "value": [
    {
    ....
    "organizationName": "Invision Test Org",
    ....
    },
    {
    ....
    "inventoryNo": "Inv #10",
    ....
    },
    {
    ....
    "classificationName": "Capital Inventory",
    ....
    },
    ....
    {....}
    ],
    "@odata.nextLink": "https://api-demo.envi.net/odata/Inventory?$search=inv&$top=20&$skip=20"
    }

```
## <span style="color: #F05D30">$top and $skip</span> 

The ```$top``` system query option requests the number of items in the queried collection included in the result.

Due to the ```$top``` operator max value, the current limit is **5 000** records within one API request. When the specified ```$top``` value is greater than the limit, you will receive the response—400 Bad Request.

The ```$skip``` query option requests the number of items in the queried collection that should be skipped and not included in the response. If the ```$top``` option is not provided, Envi API automatically adds ```$top=20``` to the initial query. So, the response contains only the first 20 records. 


``` title="Request Example"
https://<HOSTNAME>/odata/Inventory 
    
```
(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

Since neither the ```$top``` nor ```$skip``` options are specified, the system uses default values, so a response contains the first 20 records from the matched list, and ```@odata.nextLink``` is composed based on default values.


``` json title="Response Example"
{
    "@odata.context": "https://api-demo.envi.net/odata/$metadata#Inventory",
    "@odata.count": 17521,
    "value": [
    {
    "inventoryId": "732adaec-fd14-44e5-b3d6-603fe893bc15",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    {....},
    ....
    {....}
    ],
    "@odata.nextLink": "https://api-demo.envi.net/odata/Inventory?$top=20&$skip=20"
    }

```

<br>

``` title="Request Example"
https://<HOSTNAME>/odata/Inventory?$top=5
    
```
(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

Since the ```$top``` option is specified, the system returns the first 5 records from the matched list, and ```@odata.nextLink``` is composed based on this value.

``` json title="Response Example"

{
    "@odata.context": "https://api-demo.envi.net/odata/$metadata#Inventory",
    "@odata.count": 17521,
    "value": [
    {
    "inventoryId": "732adaec-fd14-44e5-b3d6-603fe893bc15",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    {....},
    ....
    {....}
    ],
    "@odata.nextLink": "https://api-demo.envi.net/odata/Inventory?$top=5&$skip=5"
    }
```

<br>

``` title="Request Example"
https://<HOSTNAME>/odata/Inventory?$skip=10
    
```
(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

Since the ```$skip``` option is specified, but ```$top``` is not, the system skips the first 10 records and uses a default value for the ```$top``` option, so the next 20 records from the matched list (after 10 records that are skipped) are returned, and ```@odata.nextLink``` is composed based on the following value.

``` json title="Response Example"
{
    "@odata.context": "https://api-demo.envi.net/odata/$metadata#Inventory",
    "@odata.count": 17521,
    "value": [
    {
    "inventoryId": "732adaec-fd14-44e5-b3d6-603fe893bc15",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    {....},
    ....
    {....}
    ],
    "@odata.nextLink": "https://api-demo.envi.net/odata/Inventory?$top=20&$skip=30"
    }

```

## <span style="color: #F05D30">$filter</span> 

The ```$filter``` system query option allows clients to filter a collection of resources addressed by a request URL. The expression specified with the```$filter``` is evaluated for each resource in the collection, and only items, in which the expression is evaluated True are included in the response. Resources in which the expression is evaluated False or Null are skipped in the response. Property names should be specified in lowerCamelCase.

Now, Envi API allows filtering by the following functions:

 - **```Contains```**—treated as the like expression. The system searches the specified value in any part of the property.

Also, Envi API supports the following logical operations:

 - **```Equals```**—treated as the Strict match expression. It means that a specified property should exactly be matched with a provided value.


``` title="Request Example"
https://<HOSTNAME>/odata/Inventory?$filter=notes eq 'Capital Item'
    
```

(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

This request example filters target records set based on the value of notes property, and if it equals Capital Item, an entity will be included in the resulting set.

Since no ```$top``` option is specified, only the first 20 records will be included. Except for the ```$top``` and ```$skip``` options, ```@odata.nextLink``` in the response will include the ```$filter``` option.

``` json title="Response Example"
{
    "@odata.context": "https://api-demo.envi.net/odata/$metadata#Inventory",
    "@odata.count": 52,
    "value": [
    {
    ....
    "notes": "Capital Item",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    {
    ....
    "notes": "Capital Item",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    ....
    {....}
    ],
    "@odata.nextLink": "https://api-demo.envi.net/odata/Inventory?$filter=notes%20eq%20%27%21%20Capital%20Item%27&$top=20&$skip=20"
    }

```


``` title="Request Example"
https://<HOSTNAME>/odata/Inventory?$filter=contains(notes, 'Capital')
    
```

(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

This request example filters target records set based on the value of notes property, and if it contains Capital in any part of the text, an entity will be included in the resulting set.

Since no ```$top``` option is specified, only the first 20 records will be included. Except for the ```$top``` and ```$skip``` options, ```@odata.nextLink``` in the response will include the ```$filter``` option.

``` json title="Response Example"
{
    "@odata.context": "https://api-demo.envi.net/odata/$metadata#Inventory",
    "@odata.count": 92,
    "value": [
    {
    ....
    "notes": "Capital Item",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    {
    ....
    "notes": "Not Capital",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
      ....
    },
    {
    ....
    "notes": "Can be treated as Capital",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    ....
    {....}
    ],
    "@odata.nextLink": "https://api-demo.envi.net/odata/Inventory?$filter=contains%28notes,%20%27Capital%27%29&$top=20&$skip=20"
    }

```

### <span style="color: #F05D30">Logical operators</span>

Also, the ```$filter``` query option supports the following logical operators:

#### <span style="color: #F05D30">and</span>
The logical **and** operator evaluates True if both the left and right operands evaluate True, otherwise it evaluates False.
``` json title="Example"
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' and inventoryNo eq 'DEXAMT'
    
```
#### <span style="color: #F05D30">or</span>
The logical **or** operator evaluates True if one of the left or right operands evaluates True, otherwise it evaluates False.

``` json title="Example"
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' or contains(inventoryDescription, 'DEXAMT')
    
```

#### <span style="color: #F05D30">in</span>
The **in** operator returns True if the left operand is a member of the right operand. The right operand must be either a comma-separated list of values enclosed in parentheses or a single expression that resolves to a collection. Also, the **in** operator enables a shorthand way of writing multiple **eq** expressions joined by **or**.

``` json title="Example"
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' or classificationName eq = 'DEXAMT' 
   
```
``` 
https://api-demo.envi.net/odata/Inventory?$filter=classificationName in ('MEDICATION', 'DEXAMT')

``` 
The **in** operator is supported in the following lists:

 - [Addresses](Addresses.md#get-the-list-of-addresses)
 - [Facilities](Facilities.md#get-the-list-of-facilities)
 - [Inventory](Inventory.md#get-the-list-of-inventory-items)
 - [Inventory Activity](InventoryActivity.md#get-the-list-of-inventory-activities)
 - [Inventory Locations](InventoryLocations.md#get-the-list-of-inventory-locations)
 - [Inventory Locations Cost and Quantity](InventoryLocationsCostAndQuantity.md#get-the-list-of-inventory-locations-cost-and-quantity)
 - [Inventory Location extended](InventoryLocationsExtended.md#get-the-list-of-extended-inventory-location)
 - [Inventory Snapshots](InventorySnapshots.md#get-the-list-of-inventory-snapshots)
 - [Inventory Snapshot Item Details](InventorySnapshotItems.md#get-the-details-of-the-specified-inventory-snapshot-item)
 - [Inventory Vendors](InventoryVendors.md#get-the-cost-history-for-the-specified-inventory-vendor)
 - [Manufacturers](Manufacturers.md#get-the-list-of-manufacturers)
 - [Purchase Orders](PurchaseOrders.md#get-the-list-of-purchase-orders)
 - [Purchase Orders Items](PurchaseOrderItems.md#get-the-list-of-purchase-order-items)
 - [Receipts](Receipts.md#get-the-list-of-po-receipts)
 - [Receipts Items](ReceiptItems.md#get-the-list-of-po-receipt-items)
 - [PAR Areas](PARAreas.md#get-the-list-of-par-areas)
 - [PAR Area Items](PARAreaItems.md#get-the-list-of-par-area-items)
 - [PO Confirmations](POConfirmations.md#get-the-list-of-po-confirmations)
 - [PO Confirmations Items](POConfirmationItems.md#get-the-list-of-po-confirmation-items)
 - [Requisition Fill Items](RequisitionFillItems.md#get-the-list-of-requisition-fill-items)
 - [Requisition Fills](RequisitionFills.md#get-the-list-of-requisition-fills)
 - [Requisition Items](RequisitionItems.md#get-the-list-of-requisition-items)
 - [Requisitions](Requisitions.md#get-the-list-of-requisitions)
 - [Vendor Addresses](VendorAddresses.md#get-the-list-of-vendor-addresses)
 - [Vendor Contacts](VendorContacts.md#get-the-list-of-vendor-contacts)
 - [Vendor Email Configurations](VendorEmailConfigurations.md#get-the-list-of-vendor-email-configurations)
 - [Vendor Facilities](VendorFacilities.md#get-the-list-of-vendor-facilities)
 - [Vendor Fax Configurations](VendorFaxConfigurations.md#get-the-list-of-vendor-fax-configurations)
 - [Vendors](Vendors.md#get-the-list-of-vendors)


#### <span style="color: #F05D30">gt</span>
The **gt** operator returns True if the left operand is greater than the right operand, otherwise it returns False. This operator supports decimal, integer, and dates values.

``` json title="Example"
https://api-demo.envi.net/odata/PurchaseOrders?$filter=unitCost gt 1.2345 
   
```

The **gt** operator is supported in the following lists:

 - [Addresses](Addresses.md#get-the-list-of-addresses)
 - [Facilities](Facilities.md#get-the-list-of-facilities)
 - [Inventory](Inventory.md#get-the-list-of-inventory-items)
 - [Inventory Location extended](InventoryLocationsExtended.md#get-the-list-of-extended-inventory-location)
 - [Inventory Locations](InventoryLocations.md#get-the-list-of-inventory-locations)
 - [Inventory Snapshots](InventorySnapshots.md#get-the-list-of-inventory-snapshots)
 - [Inventory Snapshot Item Details](InventorySnapshotItems.md#get-the-details-of-the-specified-inventory-snapshot-item)
 - [Inventory Vendors](InventoryVendors.md#get-the-cost-history-for-the-specified-inventory-vendor)
 - [Manufacturers](Manufacturers.md#get-the-list-of-manufacturers)
 - [Purchase Orders](PurchaseOrders.md#get-the-list-of-purchase-orders)
 - [Purchase Orders Items](PurchaseOrderItems.md#get-the-list-of-purchase-order-items)
 - [Receipts](Receipts.md#get-the-list-of-po-receipts)
 - [Receipts Items](ReceiptItems.md#get-the-list-of-po-receipt-items)
 - [PAR Areas](PARAreas.md#get-the-list-of-par-areas)
 - [PAR Area Items](PARAreaItems.md#get-the-list-of-par-area-items)
 - [PO Confirmations](POConfirmations.md#get-the-list-of-po-confirmations)
 - [PO Confirmations Items](POConfirmationItems.md#get-the-list-of-po-confirmation-items)
 - [Requisition Fill Items](RequisitionFillItems.md#get-the-list-of-requisition-fill-items)
 - [Requisition Fills](RequisitionFills.md#get-the-list-of-requisition-fills)
 - [Requisition Items](RequisitionItems.md#get-the-list-of-requisition-items)
 - [Requisitions](Requisitions.md#get-the-list-of-requisitions)
 - [Vendor Addresses](VendorAddresses.md#get-the-list-of-vendor-addresses)
 - [Vendor Contacts](VendorContacts.md#get-the-list-of-vendor-contacts)
 - [Vendor Email Configurations](VendorEmailConfigurations.md#get-the-list-of-vendor-email-configurations)
 - [Vendor Facilities](VendorFacilities.md#get-the-list-of-vendor-facilities)
 - [Vendor Fax Configurations](VendorFaxConfigurations.md#get-the-list-of-vendor-fax-configurations)
 - [Vendors](Vendors.md#get-the-list-of-vendors)

#### <span style="color: #F05D30">ge</span>
The **ge** operator returns True if the left operand is greater than or equal to the right operand, otherwise it returns False. This operator supports decimal, integer, and dates values.

``` json title="Example"
https://api-demo.envi.net/odata/PurchaseOrders?$filter=lastUpdated ge YYYY-MM-DD
   
```
The **ge** operator is supported in the following lists:

 - [Addresses](Addresses.md#get-the-list-of-addresses)
 - [Facilities](Facilities.md#get-the-list-of-facilities)
 - [Inventory](Inventory.md#get-the-list-of-inventory-items)
 - [Inventory Location extended](InventoryLocationsExtended.md#get-the-list-of-extended-inventory-location)
 - [Inventory Locations](InventoryLocations.md#get-the-list-of-inventory-locations)
 - [Inventory Snapshots](InventorySnapshots.md#get-the-list-of-inventory-snapshots)
 - [Inventory Snapshot Item Details](InventorySnapshotItems.md#get-the-details-of-the-specified-inventory-snapshot-item)
 - [Inventory Vendors](InventoryVendors.md#get-the-cost-history-for-the-specified-inventory-vendor)
 - [Manufacturers](Manufacturers.md#get-the-list-of-manufacturers)
 - [Purchase Orders](PurchaseOrders.md#get-the-list-of-purchase-orders)
 - [Purchase Orders Items](PurchaseOrderItems.md#get-the-list-of-purchase-order-items)
 - [Receipts](Receipts.md#get-the-list-of-po-receipts)
 - [Receipts Items](ReceiptItems.md#get-the-list-of-po-receipt-items)
 - [PAR Areas](PARAreas.md#get-the-list-of-par-areas)
 - [PAR Area Items](PARAreaItems.md#get-the-list-of-par-area-items)
 - [PO Confirmations](POConfirmations.md#get-the-list-of-po-confirmations)
 - [PO Confirmations Items](POConfirmationItems.md#get-the-list-of-po-confirmation-items)
 - [Requisition Fill Items](RequisitionFillItems.md#get-the-list-of-requisition-fill-items)
 - [Requisition Fills](RequisitionFills.md#get-the-list-of-requisition-fills)
 - [Requisition Items](RequisitionItems.md#get-the-list-of-requisition-items)
 - [Requisitions](Requisitions.md#get-the-list-of-requisitions)
 - [Vendor Addresses](VendorAddresses.md#get-the-list-of-vendor-addresses)
 - [Vendor Contacts](VendorContacts.md#get-the-list-of-vendor-contacts)
 - [Vendor Email Configurations](VendorEmailConfigurations.md#get-the-list-of-vendor-email-configurations)
 - [Vendor Facilities](VendorFacilities.md#get-the-list-of-vendor-facilities)
 - [Vendor Fax Configurations](VendorFaxConfigurations.md#get-the-list-of-vendor-fax-configurations)
 - [Vendors](Vendors.md#get-the-list-of-vendors)

#### <span style="color: #F05D30">lt</span>
The **lt** operator returns True if the left operand is less than the right operand, otherwise it returns False. This operator supports decimal, integer, and dates values.
``` json title="Example"
https://api-demo.envi.net/odata/PurchaseOrders?$filter=unitCost lt 1.2345
   
```
The **lt** operator is supported in the following lists:

 - [Addresses](Addresses.md#get-the-list-of-addresses)
 - [Facilities](Facilities.md#get-the-list-of-facilities)
 - [Inventory](Inventory.md#get-the-list-of-inventory-items)
 - [Inventory Location extended](InventoryLocationsExtended.md#get-the-list-of-extended-inventory-location)
 - [Inventory Locations](InventoryLocations.md#get-the-list-of-inventory-locations)
 - [Inventory Snapshots](InventorySnapshots.md#get-the-list-of-inventory-snapshots)
 - [Inventory Snapshot Item Details](InventorySnapshotItems.md#get-the-details-of-the-specified-inventory-snapshot-item)
 - [Inventory Vendors](InventoryVendors.md#get-the-cost-history-for-the-specified-inventory-vendor)
 - [Manufacturers](Manufacturers.md#get-the-list-of-manufacturers)
 - [Purchase Orders](PurchaseOrders.md#get-the-list-of-purchase-orders)
 - [Purchase Orders Items](PurchaseOrderItems.md#get-the-list-of-purchase-order-items)
 - [Receipts](Receipts.md#get-the-list-of-po-receipts)
 - [Receipts Items](ReceiptItems.md#get-the-list-of-po-receipt-items)
 - [PAR Areas](PARAreas.md#get-the-list-of-par-areas)
 - [PAR Area Items](PARAreaItems.md#get-the-list-of-par-area-items)
 - [PO Confirmations](POConfirmations.md#get-the-list-of-po-confirmations)
 - [PO Confirmations Items](POConfirmationItems.md#get-the-list-of-po-confirmation-items)
 - [Requisition Fill Items](RequisitionFillItems.md#get-the-list-of-requisition-fill-items)
 - [Requisition Fills](RequisitionFills.md#get-the-list-of-requisition-fills)
 - [Requisition Items](RequisitionItems.md#get-the-list-of-requisition-items)
 - [Requisitions](Requisitions.md#get-the-list-of-requisitions)
 - [Vendor Addresses](VendorAddresses.md#get-the-list-of-vendor-addresses)
 - [Vendor Contacts](VendorContacts.md#get-the-list-of-vendor-contacts)
 - [Vendor Email Configurations](VendorEmailConfigurations.md#get-the-list-of-vendor-email-configurations)
 - [Vendor Facilities](VendorFacilities.md#get-the-list-of-vendor-facilities)
 - [Vendor Fax Configurations](VendorFaxConfigurations.md#get-the-list-of-vendor-fax-configurations)
 - [Vendors](Vendors.md#get-the-list-of-vendors)

#### <span style="color: #F05D30">le</span>
The **le** operator returns True if the left operand is less than or equal to the right operand, otherwise it returns False. This operator supports decimal, integer, and dates values.

``` json title="Example"
https://api-demo.envi.net/odata/PurchaseOrders?$filter=lastUpdated le YYYY-MM-DD
   
```
The **le** operator is supported in the following lists:

 - [Addresses](Addresses.md#get-the-list-of-addresses)
 - [Facilities](Facilities.md#get-the-list-of-facilities)
 - [Inventory](Inventory.md#get-the-list-of-inventory-items)
 - [Inventory Location extended](InventoryLocationsExtended.md#get-the-list-of-extended-inventory-location)
 - [Inventory Locations](InventoryLocations.md#get-the-list-of-inventory-locations)
 - [Inventory Snapshots](InventorySnapshots.md#get-the-list-of-inventory-snapshots)
 - [Inventory Snapshot Item Details](InventorySnapshotItems.md#get-the-details-of-the-specified-inventory-snapshot-item)
 - [Inventory Vendors](InventoryVendors.md#get-the-cost-history-for-the-specified-inventory-vendor)
 - [Manufacturers](Manufacturers.md#get-the-list-of-manufacturers)
 - [Purchase Orders](PurchaseOrders.md#get-the-list-of-purchase-orders)
 - [Purchase Orders Items](PurchaseOrderItems.md#get-the-list-of-purchase-order-items)
 - [Receipts](Receipts.md#get-the-list-of-po-receipts)
 - [Receipts Items](ReceiptItems.md#get-the-list-of-po-receipt-items)
 - [PAR Areas](PARAreas.md#get-the-list-of-par-areas)
 - [PAR Area Items](PARAreaItems.md#get-the-list-of-par-area-items)
 - [PO Confirmations](POConfirmations.md#get-the-list-of-po-confirmations)
 - [PO Confirmations Items](POConfirmationItems.md#get-the-list-of-po-confirmation-items)
 - [Requisition Fill Items](RequisitionFillItems.md#get-the-list-of-requisition-fill-items)
 - [Requisition Fills](RequisitionFills.md#get-the-list-of-requisition-fills)
 - [Requisition Items](RequisitionItems.md#get-the-list-of-requisition-items)
 - [Requisitions](Requisitions.md#get-the-list-of-requisitions)
 - [Vendor Addresses](VendorAddresses.md#get-the-list-of-vendor-addresses)
 - [Vendor Contacts](VendorContacts.md#get-the-list-of-vendor-contacts)
 - [Vendor Email Configurations](VendorEmailConfigurations.md#get-the-list-of-vendor-email-configurations)
 - [Vendor Facilities](VendorFacilities.md#get-the-list-of-vendor-facilities)
 - [Vendor Fax Configurations](VendorFaxConfigurations.md#get-the-list-of-vendor-fax-configurations)
 - [Vendors](Vendors.md#get-the-list-of-vendors)



!!! warning 

    You can use only one type of logical operators at once.


``` json title="Example"
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' and inventoryNo eq '27417' and contains(inventoryDescription, '27417')
   
```
**OR**

``` 
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' or inventoryNo eq '27417' or contains(inventoryDescription, '27417')
   
```
You cannot mix logical operators together as in the following example. In such cases, you’ll receive the **400 Bad Request** response.

``` json title="Example"
   
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' and inventoryNo eq '27417' or contains(inventoryDescription, '27417')
   
```

Use logical operators only with different fields for searching, as in the following example. You’ll receive the **400 Bad Request** response if you specify the same fields.

``` json title="Example"
   
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' and inventoryNo eq '27417' and contains(inventoryDescription, '27417')
   
```

## <span style="color: #F05D30">$orderby</span>

The ```$orderby``` system query option allows clients to request resources in either ascending using asc or descending orders using desc. If asc or desc values are not specified, then resources are displayed in ascending order.

Property name should be specified in lowerCamelCase.

Now, Envi API supports sorting by only one field at a time.

``` title="Request Example"
https://<HOSTNAME>/odata/Inventory?$orderby inventoryNo
    
```

(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

This sample request sorts target records set by the value of the ```inventoryNo``` property in ascending order.

Since the ```$top``` option is not specified, only the first 20 records are included. Except for the ```$top``` and ```$skip``` options, ```@odata.nextLink``` also includes the ```$orderby``` in the response.

``` json title="Response Example"
{
    "@odata.context": "https://api-demo.envi.net/odata/$metadata#Inventory",
    "@odata.count": 92,
    "value": [
    {
    ....
    "inventoryNo": "#1011",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    {
    ....
    "inventoryNo": "#1025",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    {
    ....
    "inventoryNo": "#1523",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    ....
    {....}
    ],
    "@odata.nextLink": "https://api-demo.envi.net/odata/Inventory?$orderby=inventoryNo&$top=20&$skip=20"
    }

```
<br>

``` title="Request Example"
https://<HOSTNAME>/odata/Inventory?$orderby inventoryNo desc
    
```

(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

This sample request sorts target records set by the value of the ```inventoryNo``` property in descending order.

Since the ```$top``` option is not specified, only the first 20 records are included. Except for the ```$top``` and ```$skip``` options, ```@odata.nextLink``` also includes the ```$orderby``` in the response.

``` json title="Response Example"
{
    "@odata.context": "https://api-demo.envi.net/odata/$metadata#Inventory",
    "@odata.count": 92,
    "value": [
    {
    ....
    "inventoryNo": "#13975",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    {
    ....
    "inventoryNo": "#12579",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    {
    ....
    "inventoryNo": "#10256",
    "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec"
    ....
    },
    ....
    {....}
    ],
    "@odata.nextLink": "https://api-demo.envi.net/odata/Inventory?$orderby=inventoryNo%20desc&$top=20&$skip=20"
    }

```
## <span style="color: #F05D30">$format</span>

The ```$format``` system query option allows requesting a response in a particular format. When you don’t have access, you can request headers for the standard content-type and odata.metada level specifications. The ```$format``` takes precedence over standard content-type negotiation.

You can find examples of how to use the ```$format``` in the [Metadata](Metadata.md) section.
