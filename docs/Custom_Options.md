While pulling some valuable information, Envi OData API allows you to use custom parameters. For inactive items, you can use the following parameters:

 - **```includeInactiveInventory```**–gets all inactive inventory items and works with the following endpoints:
    - [Inventory Vendors for the specified Inventory](Inventory.md#get-the-list-of-inventory-vendors-for-the-specified-inventory)
    - [Inventory Vendors](InventoryVendors.md#get-the-list-of-all-inventory-vendors)
    - [Specified Inventory Vendor](InventoryVendors.md#get-the-specified-inventory-vendor)
    - [Inventory Vendors changed from the specified date](InventoryVendors.md#get-the-list-of-inventory-vendors-changed-from-the-specified-date)
    - [Inventory Items changed from the specified date](Inventory.md#get-the-list-of-inventory-items-changed-from-the-specified-date)
    - [Inventory Locations changed from the specified date](InventoryLocations.md#get-the-list-of-inventory-locations-changed-from-the-specified-date)


``` title="Example"
https://api-demo.envi.net/odata/inventoryVendors?includeInactiveInventory=true
    
```



 - **```includeInactiveInventoryLocations```**–gets all inactive inventory locations and works with the following endpoints:
    - [Inventory Vendors changed from the specified date](InventoryVendors.md#get-the-list-of-inventory-vendors-changed-from-the-specified-date)
    - [Inventory Items changed from the specified date](Inventory.md#get-the-list-of-inventory-items-changed-from-the-specified-date)
    - [Inventory Locations changed from the specified date](InventoryLocations.md#get-the-list-of-inventory-locations-changed-from-the-specified-date)

``` json title="Example"
https://api-demo.envi.net/odata/inventoryLocations/GetAllFromDate?includeInactiveInventoryLocations=true

```



 - **```includeInactiveVendorFacilities```**–gets all inactive vendor facilities and works with the following endpoint:
    - [Inventory Vendors changed from the specified date](InventoryVendors.md#get-the-list-of-inventory-vendors-changed-from-the-specified-date)
    - [Vendor(s) within the Facility](Vendors.md#get-the-list-of-vendors)

``` json title="Example"
https://api-demo.envi.net/odata/Vendors/GetVendorsInfo?includeInactiveVendorFacilities=true

```

 - **```includeInactiveInventoryVendors```**–gets all inactive inventory vendors and works with the following endpoint:
    - [Inventory Vendors changed from the specified date](InventoryVendors.md#get-the-list-of-inventory-vendors-changed-from-the-specified-date)

``` json title="Example"
https://api-demo.envi.net/odata/inventoryVendors/GetAllFromDate?includeInactiveInventoryVendors=true

```

 - **```includeInactiveLocations```**–gets all inactive locations and works with the following endpoints:
    - [Inventory Vendors changed from the specified date](InventoryVendors.md#get-the-list-of-inventory-vendors-changed-from-the-specified-date)
    - [Inventory Items changed from the specified date](Inventory.md#get-the-list-of-inventory-items-changed-from-the-specified-date)
    - [Inventory Locations changed from the specified date](InventoryLocations.md#get-the-list-of-inventory-locations-changed-from-the-specified-date)

``` json title="Example"
https://api-demo.envi.net/odata/inventory/GetAllFromDate?includeInactiveLocations=true

```

 - **```includeInactiveVendorAddresses```**–gets all inactive vendor addresses and works with the following endpoint:
    - [Vendor(s) within the Facility](Vendors.md#get-the-list-of-vendors)

``` json title="Example"
https://api-demo.envi.net/odata/Vendors/GetVendorsInfo?includeInactiveVendorAddresses=true

```

 - **```includeInactiveVendors```**–gets all inactive vendors and works with the following endpoints:
    - [Vendor(s) within the Facility](Vendors.md#get-the-list-of-vendors)
    - [Vendor Addresses](VendorAddresses.md#get-the-list-of-vendor-addresses)
    - [Specified Vendor Address](VendorAddresses.md#get-the-specified-vendor-address)
    - [Vendor Contacts](VendorContacts.md#get-the-list-of-vendor-contacts)
    - [Specified Vendor Contact](VendorContacts.md#get-the-specified-vendor-contact)
    - [Vendor Email Configurations](VendorEmailConfigurations.md#get-the-list-of-vendor-email-configurations)
    - [Specified Vendor Email Configuration](VendorEmailConfigurations.md#get-the-specified-vendor-email-configuration)
    - [Purchase Orders](PurchaseOrders.md#get-the-list-of-purchase-orders)
    - [Specified Purchase Order](PurchaseOrders.md#get-the-specified-purchase-order)

``` json title="Example"
https://api-demo.envi.net/odata/Vendors/GetVendorsInfo?includeInactiveVendors=true

```

 - **```includeInactiveFacilities```**–gets all inactive Facilities and works with the following endpoints:
    - [Vendor Addresses](VendorAddresses.md#get-the-list-of-vendor-addresses)
    - [Specified Vendor Address](VendorAddresses.md#get-the-specified-vendor-address)
    - [Vendor Contacts](VendorContacts.md#get-the-list-of-vendor-contacts)
    - [Specified Vendor Contact](VendorContacts.md#get-the-specified-vendor-contact)
    - [Vendor Email Configurations](VendorEmailConfigurations.md#get-the-list-of-vendor-email-configurations)
    - [Specified Vendor Email Configuration](VendorEmailConfigurations.md#get-the-specified-vendor-email-configuration)


``` json title="Example"
https://api-demo.envi.net/odata/VendorContacts?includeInactiveVendors=true

```



