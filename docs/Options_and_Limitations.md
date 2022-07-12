Refine the results of your query by using query options.

- $search
- $top and $skip
- $filter
- $orderby
- $format

This section will help you go through query options supported by Envi OData API and common scenarios for using them. Envi OData API is based on OData protocol v4.0 but has its own custom implementation, so currently not all query options are supported. Envi API allows using query options for all resources that return lists of entities, except those which actions or functions are applied to OData.

Also, Envi OData API defines a set of logical operators that evaluate to true or false. Logical operators are typically used in the $filter query option to filter the set of resources. For more details go to the **$filter** article. The concept of logical operators is simple. They allow the program to make a decision based on multiple conditions. Each operand is considered a condition that can be evaluated to a true or false. These operands can combine multiple Boolean expressions or values and provide a single Boolean output.


## <span style="color: #E0592A">$search</span>

The ``` $search ```  system query option allows searching through all available entity fields in a collection of resources that are addressed by the request URL. The expression specified by ``` $search ```  consists of the search value only which is treated as the ``` like ```  expression.

- The expression of the item evaluates to true for at least one of the fields included in the response.
- The expression of resources evaluates to false or to null for all searchable fields omitted in the response.


### <span style="color: #4051B5">Request Example</span>

(for example, **<HOSTNAME>** = api-demo.envi.net)

The following request example filters target records set based on the ``` inv ```  search value. In case any of the searchable fields contains ``` inv``` , the entity is included in the response.

Since no ``` $top ```  option is specified, only first 20 records are included in the response. Except for ``` $top```  and ``` $skip```  options, ``` @odata.nextLink``` includes the ``` $search``` option.

``` json title="Response content-types: APPLICATION/JSON, APPLICATION/XML<br>Response example (200 OK)"
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






