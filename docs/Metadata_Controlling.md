In general, there are three levels of metadata specification: ```none```, ```minimal```, and ```full```. ```Default``` metadata level is minimal, so the service removes metadata information from the payload wherever possible.

Taking into account your need of application, you can request the needed amount of metadata information included in the payload.

If you want to specify the amount of included metadata information in the response, use ```format``` query option of an OData request as a part of URL with specified ```odata.metadata``` parameter. For example, to specify none level, which means no metadata at all, URL should look like the following:

```https://<HOSTNAME>/<resource>?$format=application/json;odata.metadata=none```

for example, ```<HOSTNAME> = api-demo.envi.net```

The example shows that ```$format``` option should also include expected content type of the response (in this case ```application/json```).

## <span style="color: #F05D30">none</span> 

If you do not need metadata information, use ```odata.metadata=none```. It means that the service omits metadata information other than ```odata.nextLink``` and ```odata.count```. The following example shows the request/response for the case based on the Inventory module:


``` title="Request example"
https://<HOSTNAME>/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)?$format=application/json;odata.metadata=none
    
```
(for example, ```<HOSTNAME> = api-demo.envi.net```)


``` json title="Response example"
{
       "inventoryId": "4311192f-c46f-4655-8d51-fc2f49aabf78",
       "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec",
       "organizationName": " Test Org",
       "inventoryGroupId": "88212fc1-7698-40b3-8642-edd4ff793fcd",
       "inventoryNo": "152439785",
       "inventoryGroupName": "Item Master",
       "inventoryDescription": "Inventory Description",
       "inventoryDescription2": "Inventory Description 2",
       "stockUOM": "EA",
       "arBillingCode": "225-749-325",
       "hcpcsCode": null,
       "notes": "Some notes",
       "dateAdded": "2015-01-13T16:52:57.233-06:00",
       "addedId": "185393e0-9113-4343-8d70-921bd4bed453",
       "addedByName": "employee@domain.com",
       "lastUpdated": "2017-11-16T18:10:39.723-06:00",
       "lastUpdatedBy": "74d636e2-2dc5-402e-a12e-2722f5286adc",
       "lastUpdatedByName": "employee2@domain.com",
       "activeStatus": true,
       "unspsc": null,
       "isLatex": false,
       "classificationId": "b01be311-d138-4abd-a4b4-05740ce5cbcf",
       "classificationName": "gloves",
       "classification2Id": "7f97e363-5e33-4448-93bd-b7decdf093ac",
       "classification2Name": "classification2",
       "defaultExpenseLedgerNo": "5243",
       "defaultAssetLedgerNo": "85469",
       "periopCategoryId": "31c05c5e-6d2c-4763-bc40-e5078440b33e",
       "periopCategory": "Equipment",
       "itemType": null,
       "billable": false,
       "systemTypeId": 1,
       "systemType": "Standard"
    }
```
## <span style="color: #F05D30">minimal</span> 

If you want to save on network bandwith size but still need some metadata for correct response processing, the format query option should contain odata.metadata=minimal. It means that the service removes metadata information from the payload wherever possible. This is a default value for the odata.metadata parameter and will be assumed if no other values are specified. The response contains the following common annotation:


```title="Request example"
https://<HOSTNAME>/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)?$format=application/json;odata.metadata=minimal
    
```
**OR**

```
https://<HOSTNAME>/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)
    
```
(for example,```<HOSTNAME> = api-demo.envi.net```)


``` json title="Response example"
{
       "@odata.context": "https:///odata/$metadata#Inventory/$entity",
       "inventoryId": "4311192f-c46f-4655-8d51-fc2f49aabf78",
       "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec",
       "organizationName": " Test Org",
       "inventoryGroupId": "88212fc1-7698-40b3-8642-edd4ff793fcd",
       "inventoryNo": "152439785",
       "inventoryGroupName": "Item Master",
       "inventoryDescription": "Inventory Description",
       "inventoryDescription2": "Inventory Description 2",
       "stockUOM": "EA",
       "arBillingCode": "225-749-325",
       "hcpcsCode": null,
       "notes": "Some notes",
       "dateAdded": "2015-01-13T16:52:57.233-06:00",
       "addedId": "185393e0-9113-4343-8d70-921bd4bed453",
       "addedByName": "employee@domain.com",
       "lastUpdated": "2017-11-16T18:10:39.723-06:00",
       "lastUpdatedBy": "74d636e2-2dc5-402e-a12e-2722f5286adc",
       "lastUpdatedByName": "employee2@domain.com",
       "activeStatus": true,
       "unspsc": null,
       "isLatex": false,
       "classificationId": "b01be311-d138-4abd-a4b4-05740ce5cbcf",
       "classificationName": "gloves",
       "classification2Id": "7f97e363-5e33-4448-93bd-b7decdf093ac",
       "classification2Name": "classification2",
       "defaultExpenseLedgerNo": "5243",
       "defaultAssetLedgerNo": "85469",
       "periopCategoryId": "31c05c5e-6d2c-4763-bc40-e5078440b33e",
       "periopCategory": "Equipment",
       "itemType": null,
       "billable": false,
       "systemTypeId": 1,
       "systemType": "Standard"
    }
```


## <span style="color: #F05D30">full</span>

If you need full metadata information, you should use odata.metadata=full. It directs the service to inline the metadata information that normally would be computed from metadata expressions in the payload. The response contains a lot of additional annotation, including information about fields type and related navigation links:

```title="Request example"
https://<HOSTNAME>/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)?$format=application/json;odata.metadata=full

```
(for example, ```<HOSTNAME> = api-demo.envi.net```)

``` json title="Response example"
{
       "@odata.context": "https://api-demo.envi.net/odata/$metadata#Inventory/$entity",
       "@odata.type": "#Api.Common.Entities.Inventory.DTO.Inventory",
       "@odata.id": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)",
       "@odata.editLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)",
       "inventoryId@odata.type": "#Guid",
       "inventoryId": "4311192f-c46f-4655-8d51-fc2f49aabf78",
       "organizationId@odata.type": "#Guid",
       "organizationId": "05e36af1-0676-4216-aa3f-aa1ba787aaec",
       "organizationName": "Test Org",
       "inventoryGroupId@odata.type": "#Guid",
       "inventoryGroupId": "88212fc1-7698-40b3-8642-edd4ff793fcd",
       "inventoryNo": "152439785",
       "inventoryGroupName": "Item Master",
       "inventoryDescription": "Inventory Description",
       "inventoryDescription2": "Inventory Description 2",
       "stockUOM": "EA",
       "arBillingCode": "225-749-325",
       "hcpcsCode": null,
       "notes": "Some notes",
       "dateAdded@odata.type": "#DateTimeOffset",
       "dateAdded": "2015-01-13T16:52:57.233-06:00",
       "addedId@odata.type": "#Guid",
       "addedId": "185393e0-9113-4343-8d70-921bd4bed453",
       "addedByName": "employee@domain.com",
       "lastUpdated@odata.type": "#DateTimeOffset",
       "lastUpdated": "2017-11-16T18:10:39.723-06:00",
       "lastUpdatedBy@odata.type": "#Guid",
       "lastUpdatedBy": "74d636e2-2dc5-402e-a12e-2722f5286adc",
       "lastUpdatedByName": "employee2@domain.com",
       "activeStatus": true,
       "unspsc": null,
       "isLatex": false,
       "classificationId@odata.type": "#Guid",
       "classificationId": "b01be311-d138-4abd-a4b4-05740ce5cbcf",
       "classificationName": "gloves",
       "classification2Id@odata.type": "#Guid",
       "classification2Id": "7f97e363-5e33-4448-93bd-b7decdf093ac",
       "classification2Name": "classification2",
       "defaultExpenseLedgerNo": "5243",
       "defaultAssetLedgerNo": "85469",
       "periopCategoryId@odata.type": "#Guid",
       "periopCategoryId": "31c05c5e-6d2c-4763-bc40-e5078440b33e",
       "periopCategory": "Equipment",
       "itemType": null,
       "billable": false,
       "systemTypeId@odata.type": "#Byte",
       "systemTypeId": 1,
       "systemType": "Standard",
       "poHistoryItems@odata.associationLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/poHistoryItems/$ref",
       "poHistoryItems@odata.navigationLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/poHistoryItems",
       "futurePricing@odata.associationLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/futurePricing/$ref",
       "futurePricing@odata.navigationLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/futurePricing",
       "inventoryLocations@odata.associationLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/inventoryLocations/$ref",
       "inventoryLocations@odata.navigationLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/inventoryLocations",
       "inventoryUOMs@odata.associationLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/inventoryUOMs/$ref",
       "inventoryUOMs@odata.navigationLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/inventoryUOMs",
       "inventoryVendors@odata.associationLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/inventoryVendors/$ref",
       "inventoryVendors@odata.navigationLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/inventoryVendors",
       "inventoryTrackings@odata.associationLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/inventoryTrackings/$ref",
       "inventoryTrackings@odata.navigationLink": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/inventoryTrackings",
       "#Default.ManagePurchasing": {
           "title": "ManagePurchasing",
           "target": "https://api-demo.envi.net.com/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/Default.ManagePurchasing"
      },
       "#Default.inventoryTrackingValues": {
            "title": "inventoryTrackingValues",
           "target": "https://api-demo.envi.net/odata/Inventory(4311192f-c46f-4655-8d51-fc2f49aabf78)/Default.inventoryTrackingValues(facilityId=@facilityId,trackingType=@trackingType)"
        }
    }
```