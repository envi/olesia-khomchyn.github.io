Refine the results of your query by using query options.

- [$search](#search)
- [$top and $skip](#top-and-skip)
- [$filter](#filter)
- [$orderby](#orderby)
- [$format](#format)

This section will help you go through query options supported by Envi OData API and common scenarios for using them. Envi OData API is based on OData protocol v4.0 but has its own custom implementation, so currently not all query options are supported. Envi API allows using query options for all resources that return lists of entities, except those which actions or functions are applied to OData.

Also, Envi OData API defines a set of logical operators that evaluate to true or false. Logical operators are typically used in the $filter query option to filter the set of resources. For more details go to the $filter article. The concept of logical operators is simple. They allow the program to make a decision based on multiple conditions. Each operand is considered a condition that can be evaluated to a true or false. These operands can combine multiple Boolean expressions or values and provide a single Boolean output.

## <span style="color: #F05D30">$search</span> 

The ``` $search ```  system query option allows searching through all available entity fields in a collection of resources that are addressed by the request URL. The expression specified by ``` $search ```  consists of the search value only which is treated as the ``` like ```  expression.

- The expression of the item evaluates to true for at least one of the fields included in the response.
- The expression of resources evaluates to false or to null for all searchable fields omitted in the response.


``` title="Request example"
https://<HOSTNAME>/odata/Inventory?$search="inv" 
    
```
(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)



The following request example filters target records set based on the ``` inv ```  search value. In case any of the searchable fields contains ``` inv``` , the entity is included in the response.

Since no ``` $top ```  option is specified, only first 20 records are included in the response. Except for ``` $top```  and ``` $skip```  options, ``` @odata.nextLink``` includes the ``` $search``` option.


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

The ```$skip``` query option requests the number of items in the queried collection that should be skipped and not included in the response. In case ```$top``` option is not provided, Envi API automatically adds ```$top=20``` to the initial query. Thus, a response contains 20 first records only, and the ```@odata.next``` link includes ```$top``` and ```$skip``` query options based on that value.


``` title="Request example"
https://<HOSTNAME>/odata/Inventory 
    
```
(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

Since neither ```$top``` nor ```$skip``` options are specified, the system uses default values, so a response contains first 20 records from the matched list, and ```@odata.nextLink``` is composed based on default values.


``` json title="Response example"
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

``` title="Request example"
https://<HOSTNAME>/odata/Inventory?$top=5
    
```
(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

Since the ```$top``` option is specified, system returns first 5 records from the matched list, and ```@odata.nextLink``` is composed based on this value.

``` json title="Response example"

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

``` title="Request example"
https://<HOSTNAME>/odata/Inventory?$skip=10
    
```
(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

Since ```$skip``` option is specified, but ```$top``` is not, system skips first 10 records and uses default value for ```$top``` option, so next 20 records from the matched list (after 10 records that are skipped) are returned, and ```@odata.nextLink``` is composed based on the following value.

``` json title="Response example"
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

The ```$filter``` system query option allows clients to filter a collection of resources addressed by a request URL. The expression specified with ```$filter``` is evaluated for each resource in the collection, and only items, which expression is evaluated to true are included in the response. Resources which expression is evaluated to False or Null are skipped in the response. Property names should be specified in lower camel case.

Now, Envi API allows filtering by the following functions:

 - **```Contains```**—treated as the like expression. The system searches the specified value in any part of the property.

Also, Envi API supports the following logical operations:

 - **```Equals```**—treated as the Strict match expression. It means that specified property should exactly be matched with provided value.


``` title="Request example"
https://<HOSTNAME>/odata/Inventory?$filter=notes eq 'Capital Item'
    
```

(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

This request example filters target records set based on value of notes property and in case it equals Capital Item, entity will be included in resulting set.

Since no ```$top``` option is specified, only first 20 records will be included. Except of ```$top``` and ```$skip``` options, ```@odata.nextLink``` in the response will include ```$filter``` option.

``` json title="Response example"
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


``` title="Request example"
https://<HOSTNAME>/odata/Inventory?$filter=contains(notes, 'Capital')
    
```

(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

This request example filters target records set based on value of notes property and in case it contains Capital in any part of the text, entity will be included in resulting set.

Since no ```$top``` option is specified, only first 20 records will be included. Except of ```$top``` and ```$skip``` options, ```@odata.nextLink``` in the response will include ```$filter``` option.

``` json title="Response example"
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

### <span style="color: #1779BA">Logical Operators</span>

Also, the ```$filter``` query option supports the following logical operators:

The logical **and** operator evaluates to true if both the left and right operands evaluate to true, otherwise it evaluates to false.
``` json title="Example"
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' and inventoryNo eq 'DEXAMT'
    
```
The logical **or** operator evaluates to true if one of the left or right operands evaluates to true, otherwise it evaluates to false.

``` json title="Example"
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' or contains(inventoryDescription, 'DEXAMT')
    
```
The **in** operator returns true if the left operand is a member of the right operand. The right operand must be either a comma-separated list of a values, enclosed in parentheses, or a single expression that resolves to a collection. Also, the **in** operator enables a shorthand way of writing multiple **eq** expressions joined by **or**.

``` json title="Example"
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' or classificationName eq = 'DEXAMT' 
   
```
``` 
https://api-demo.envi.net/odata/Inventory?$filter=classificationName in ('MEDICATION', 'DEXAMT')

``` 
The **in** operator is supported in the following lists:

 - Addresses
 - Facilities
 - Inventory
 - Inventory Activity
 - Inventory Locations
 - Inventory Location Cost and Quantity
 - Inventory Location extended
 - Inventory Snapshot
 - Inventory Snapshot Item Details
 - Inventory Vendors
 - Purchase Orders
 - Purchase Orders Items
 - Receipts
 - Receipts Items
 - PAR Areas
 - PAR Area Items
 - PO Confirmations
 - PO Confirmations Items
 - Requisition Items
 - Requisition Items specified
 - Requisitions
 - Requisitions specified
 - Vendors

The **gt** operator returns true if the left operand is greater than the right operand, otherwise it returns false. This operator supports decimal, integer, and dates values.

``` json title="Example"
https://api-demo.envi.net/odata/PurchaseOrders?$filter=unitCost gt 1.2345 
   
```

The **gt** operator is supported in the following lists:

 - Addresses
 - Facilities
 - Inventory
 - Inventory Location extended
 - Inventory Locations
 - Inventory Snapshot
 - Inventory Snapshot Item Details
 - Inventory Vendors
 - Purchase Orders
 - Purchase Orders Items
 - Receipts
 - Receipts Items
 - PAR Areas
 - PAR Area Items
 - PO Confirmations
 - PO Confirmations Items
 - Requisition Items
 - Requisition Items specified
 - Requisitions
 - Requisitions specified
 - Vendors

The **ge** operator returns true if the left operand is greater than or equal to the right operand, otherwise it returns false. This operator supports decimal, integer, and dates values.

``` json title="Example"
https://api-demo.envi.net/odata/PurchaseOrders?$filter=lastUpdated ge YYYY-MM-DD
   
```
The **ge** operator is supported in the following lists:

 - Addresses
 - Facilities
 - Inventory
 - Inventory Location extended
 - Inventory Locations
 - Inventory Snapshot
 - Inventory Snapshot Item Details
 - Inventory Vendors
 - Purchase Orders
 - Purchase Orders Items
 - Receipts
 - Receipts Items
 - PAR Areas
 - PAR Area Items
 - PO Confirmations
 - PO Confirmations Items
 - Requisition Items
 - Requisition Items specified
 - Requisitions
 - Requisitions specified
 - Vendors

The **lt** operator returns true if the left operand is less than the right operand, otherwise it returns false. This operator supports decimal, integer, and dates values.
``` json title="Example"
https://api-demo.envi.net/odata/PurchaseOrders?$filter=unitCost lt 1.2345
   
```
The **lt** operator is supported in the following lists:

 - Addresses
 - Facilities
 - Inventory
 - Inventory Location extended
 - Inventory Locations
 - Inventory Snapshot
 - Inventory Snapshot Item Details
 - Inventory Vendors
 - Purchase Orders
 - Purchase Orders Items
 - Receipts
 - Receipts Items
 - PAR Areas
 - PAR Area Items
 - PO Confirmations
 - PO Confirmations Items
 - Requisition Items
 - Requisition Items specified
 - Requisitions
 - Requisitions specified
 - Vendors

The **le** operator returns true if the left operand is less than or equal to the right operand, otherwise it returns false. This operator supports decimal, integer, and dates values.

``` json title="Example"
https://api-demo.envi.net/odata/PurchaseOrders?$filter=lastUpdated le YYYY-MM-DD
   
```
The **le** operator is supported in the following lists:

 - Addresses
 - Facilities
 - Inventory
 - Inventory Location extended
 - Inventory Locations
 - Inventory Snapshot
 - Inventory Snapshot Item Details
 - Inventory Vendors
 - Purchase Orders
 - Purchase Orders Items
 - Receipts
 - Receipts Items
 - PAR Areas
 - PAR Area Items
 - PO Confirmations
 - PO Confirmations Items
 - Requisition Items
 - Requisition Items specified
 - Requisitions
 - Requisitions specified
 - Vendors


!!! warning 

    You can use only one type of logical operators at once.


``` json title="Example"
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' and inventoryNo eq '27417' and contains(inventoryDescription, '27417')
   
```
**OR**

``` 
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' or inventoryNo eq '27417' or contains(inventoryDescription, '27417')
   
```
You cannot mix logical operators together as in the following example. In such cases, you’ll receive the 400 Bad Request response.

``` json title="Example"
   
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' and inventoryNo eq '27417' or contains(inventoryDescription, '27417')
   
```

Use logical operators only with different fields for searching, as in the following example. 

You’ll receive 400 Bad request response if you specify same fields.

``` json title="Example"
   
https://api-demo.envi.net/odata/Inventory?$filter=classificationName eq 'MEDICATION' and inventoryNo eq '27417' and contains(inventoryDescription, '27417')
   
```

## <span style="color: #F05D30">$orderby</span>

The ```$orderby``` system query option allows clients to request resources in either ascending using asc or descending orders using desc. If asc or desc values are not specified, then resources are displayed in ascending order.

Property name should be specified in lower camel case.

Now, Envi API supports sorting by only one field at a time.

``` title="Request example"
https://<HOSTNAME>/odata/Inventory?$orderby inventoryNo
    
```

(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

This sample request sorts target records set by value of the inventoryNo property in ascending order.

Since the ```$top``` option is not specified, only first 20 records are included. Except ```$top``` and ```$skip``` options, ```@odata.nextLink``` also includes ```$orderby``` in the response.

``` json title="Response example"
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

``` title="Request example"
https://<HOSTNAME>/odata/Inventory?$orderby inventoryNo desc
    
```

(for example, **&lt;HOSTNAME&gt;** = api-demo.envi.net)

This sample request sorts target records set by a value of the inventoryNo property in descending order.

Since the ```$top``` option is not specified, only first 20 records are included. Except ```$top``` and ```$skip``` options, ```@odata.nextLink``` also includes ```$orderby``` in the response.

``` json title="Response example"
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

The ```$format``` system query option allows requesting a response in a particular format. When you don’t have an access, you can request headers for standard content-type and odata.metada level specification. ```$format``` takes precedence over standard content-type negotiation.

You can find examples of how to use ```$format``` in the [Metadata](Metadata.md) section.
