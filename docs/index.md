# Envi OData Public API 1.0
This page contains description of Envi public OData API. It includes all public end-points as well as description of parameters and models used. You can use this page for testing and prototyping purposes.


!!! note ""

    **API Endpoint** <br>
    ``` 
    https://api-demo.envi.net 
    ``` 
    **Schemes**: HTTP, HTTPS <br>
    **Version**: V1


# What's new
Stay up-to-date with the latest API features, improvements, and articles.

[Subscribe to our newsletter](https://news.envi.net/Signup/dev-news){ .md-button .md-button--primary }

<span style="color: #E0592A">V. 5.7.4</span>

Requisition Fills endpoints are now available on Envi OData API.

<span style="color: #E0592A">V. 5.7.3</span>

A new Requisition Item endpoint has been implemened. Thus, you can partially update the details of the Requisition Line Item specified by Requisition Item ID.

WebHook is enabled within Envi. The WebHook subscription configuration allows you to get notifications regarding affected entities of selected types.

<span style="color: #E0592A">V. 5.7.2</span>

Now, active subscribers will receive updates via WebHook when the Usage transaction status has been changed to Submitted.

<span style="color: #E0592A">V. 5.6.7</span>

A new Requisition Item endpoint has been added. So, now you are able to add specified Requisition Line Items.

<span style="color: #E0592A">V. 5.5.4</span>

From now on, you can use the Requisition Items endpoints to get a list of Requisition Items from all Requisitions within a logged organization or get specified Requisition Item by ID.

<span style="color: #E0592A">V. 5.4.7</span>

Requisitions endpoints are now available on **Envi OData API**.


<div class="show-more-item" style="display: none;">blah</div>
<div class="show-more-item" style="display: none;">blah</div>
<div class="show-more-item" style="display: none;">blah</div>
<div class="show-more-item" style="display: none;">blah</div>
<div class="show-more-item" style="display: none;">blah</div>
<div class="show-more-item" style="display: none;">blah</div>
<div class="show-more-item" style="display: none;">blah</div>
<div class="show-more-item" style="display: none;">blah</div>
<div class="show-more-item" style="display: none;">blah</div>
<div class="show-more-btn">Load More</div>


??? note "Version History"

    <span style="color: #E0592A">V. 5.4.5</span>

    We have added a new Inventory Vendor endpoint that enables you to create a new Inventory Vendor within a logged organization and specified Inventory.

    <span style="color: #E0592A">V. 5.4.4</span>

    You can now create a new Inventory Location specified by ID using the Inventory Locations endpoint.

    <span style="color: #E0592A">V. 5.4.0</span>

    Inventory Location Cost and Quantity endpoints have been added to the **Envi OData API**.

    <span style="color: #E0592A">V. 5.3.9</span>

    Vendors endpoint supports now the **and**, **or**, **in**, **gt**, **ge**, **lt**, **le** logical operators.

    <span style="color: #E0592A">V. 5.3.8</span>

    Facilities endpoint supports now the **and**, **or**, **in**, **gt**, **ge**, **lt**, **le** logical operators.

    <span style="color: #E0592A">V. 5.3.7</span>

    Addresses endpoint supports now the **and**, **or**, **in**, **gt**, **ge**, **lt**, **le** logical operators.

    <span style="color: #E0592A">V. 5.3.6</span>

    Inventory Vendor endpoints support the **in**, **gt**, **ge**, **lt**, **le** logical operators.

    <span style="color: #E0592A">V. 5.3.5</span>

    Inventory supports the **in**, **gt**, **ge**, **lt**, **le** logical operators.

    <span style="color: #E0592A">V. 5.3.1</span>

    Inventory Locations support the **in**, **gt**, **ge**, **lt**, **le** logical operators.

    Additional fields are now available in the Facilities endpoint.

    <span style="color: #E0592A">V. 5.3.0</span>

    InventorySnapshotItems are now available on Envi OData API.

    <span style="color: #E0592A">V. 5.2.9</span>

    You can now get the InventorySnapshots data.

    <span style="color: #E0592A">V. 5.2.6</span>

    The Receipts endpoints support now additional ``` receiptSourceId ```  and ``` receiptSource``` fields.
