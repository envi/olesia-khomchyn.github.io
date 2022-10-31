# Envi Use Cases
Except for general API endpoints, Envi OData API also contains several operations intended to fulfil specific business needs.

## <span style="color: #F05D30">Batch Support</span> 
Envi OData API supports repeatability for individual requests within a batch request, as well as for individual requests within a change set or atomicity group within a batch request. Batch requests allow the grouping of multiple operations into a single HTTP request payload.

The service returns a single HTTP response in the response to all operations in requests. Individual requests within a batch may have a mix of the ```Repeatability-Request-ID``` and ```Repeatability-First-Sent``` values. In this case, each individual response within the batch response will have the appropriate Repeatability-Result according to the corresponding request.

This way, you can optimize calls to the server and improve the scalability of its service.

The batch request is limited to 500 calls.

``` cs title="Example"
var batchUrl = $"{_baseAddress}/odata/$batch";

    // Global batch request
    var batchRequest = new HttpRequestMessage(HttpMethod.Post, batchUrl);
    batchRequest.Headers.Authorization = new AuthenticationHeaderValue("bearer", (await GetToken()).AccessToken);

    // Multiple GET Requests
    var batchContent = new MultipartContent("mixed", $"batch_{Guid.NewGuid()}")
    {
      ComposeGetContent($"{_baseAddress}/odata/Inventory({new Guid("4311192f-c46f-4655-8d51-fc2f49aabf78")})"),
      ComposeGetContent($"{_baseAddress}/odata/Inventory({new Guid("71395601-8db7-4f3a-b466-106663990c90")})"),
      ComposeGetContent($"{_baseAddress}/odata/Inventory({new Guid("2a3e66aa-2e15-4035-8534-cb8a2280beea")})")
    };

    // Multile POST Requests
    // multipart content that represents the changeset container
    MultipartContent changeSet = new MultipartContent("mixed", $"changeset_{Guid.NewGuid()}");

    // Add POST content to the changeset
    var content1 = new StringContent(Serialize(GetNewInventory()), Encoding.UTF8, "application/json");
    var content2 = new StringContent(Serialize(GetNewInventory()), Encoding.UTF8, "application/json");
    var content3 = new StringContent(Serialize(GetNewInventory()), Encoding.UTF8, "application/json");
    changeSet.Add(ComposePostContent($"{_baseAddress}/odata/Inventory", content1));
    changeSet.Add(ComposePostContent($"{_baseAddress}/odata/Inventory", content2));
    changeSet.Add(ComposePostContent($"{_baseAddress}/odata/Inventory", content3));

    // Add the changeset to the batch content
    batchContent.Add(changeSet);

    batchRequest.Content = batchContent;

    var http = new HttpClient();
    HttpResponseMessage response = await http.SendAsync(batchRequest);
    var result = await response.Content.ReadAsMultipartAsync();

    // Batch response handling
    foreach (HttpContent currentContent in result.Contents)
    {
      // Two cases:
      // 1. a "single" response
      if (currentContent.Headers.ContentType.MediaType.Equals("application/http", StringComparison.OrdinalIgnoreCase)
        && !currentContent.Headers.ContentType.Parameters.Any(parameter => parameter.Name.Equals("msgtype", 				StringComparison.OrdinalIgnoreCase) && parameter.Value.Equals("response", StringComparison.OrdinalIgnoreCase)))
      {
        currentContent.Headers.ContentType.Parameters.Add(new NameValueHeaderValue("msgtype", "response"));
        await currentContent.ReadAsHttpResponseMessageAsync();
        // The workingResponse object contains a classic exploitable HttpResponseMessage (with IsSuccessStatusCode, Content.ReadAsStringAsync().Result, etc.)
      }
      // 2. a changeset response, which is an embedded multipart content
      else
      {
        var subMultipartContent = await currentContent.ReadAsMultipartAsync();
        foreach (HttpContent currentSubContent in subMultipartContent.Contents)
        {
          currentSubContent.Headers.ContentType.Parameters.Add(new NameValueHeaderValue("msgtype", "response"));
          await currentSubContent.ReadAsHttpResponseMessageAsync();
          // Same here, the workingResponse object contains a classic exploitable HttpResponseMessage
        }
      }
    }
    private static HttpMessageContent ComposeGetContent(string url)
    {
    	var getRequest = new HttpRequestMessage(HttpMethod.Get, url);
        // Next line is only needed for .NET Core 2.1 because default HTTP request version for it is 2.0 and the HTTP version for the $batch request should be 1.1
        // For more info see https://docs.microsoft.com/en-us/dotnet/api/system.net.http.httprequestmessage.version
        getRequest.Version = new Version(1, 1);

        HttpMessageContent getContent = new HttpMessageContent(getRequest);
    	getContent.Headers.Remove("Content-Type");
    	getContent.Headers.Add("Content-Type", "application/http");
    	getContent.Headers.Add("Content-Transfer-Encoding", "binary");

    	return getContent;
    }
    private static HttpMessageContent ComposePostContent(string url, StringContent serrializedContent, string contentId = null)
    {
    	var postRequest = new HttpRequestMessage
    	{
    		Content = serrializedContent,
    		Method = HttpMethod.Post,
    		RequestUri = new Uri(url)
    	};

        // Next line is only needed for .NET Core 2.1 because default HTTP request version for it is 2.0 and the HTTP version for the $batch request should be 1.1
        // For more info see https://docs.microsoft.com/en-us/dotnet/api/system.net.http.httprequestmessage.version
        postRequest.Version = new Version(1, 1);

        HttpMessageContent postContent = new HttpMessageContent(postRequest);
    	postContent.Headers.Remove("Content-Type");
    	postContent.Headers.Add("Content-Type", "application/http");
    	postContent.Headers.Add("Content-Transfer-Encoding", "binary");
    	postContent.Headers.Add("Content-ID", contentId ?? Guid.NewGuid().ToString());

    	return postContent;
    }

```
To do that, perform the following actions:

1. Specify URL: ```<hostname>/odata/$batch```
2. Specify Content-Type header: ```multipart/mixed```<br>
```boundary=batch_<identifier>```<br>
```POST /service/$batch HTTP/1.1``` <br>
```Host: host``` <br>
```Content-Type: multipart/mixed; boundary=batch_36522ad7-fc75-4b56-8c71-56071383e77b``` <br>
**```<Multipart Batch request body>```**
3. Request body

The batch body should have its own **batch ID** and start from ```--batch_ <id> ``` and end ```--batch_ <id>```. The batch consists of multiple changesets. Each **changeset** is defined in ```Content-Type``` and has a separate ID. Requests are described in the changeset sections. An example of a request body for multiple PATCH requests using the batch is the following:



``` cs title="Example"
POST /service/$batch HTTP/1.1
Host: host
Content-Type: multipart/mixed;boundary=batch_8219-6895         // 
Define batch ID

--batch_8219-6895                                              // 
Batch 1 start

  Content-Type: multipart/mixed; boundary=changeset_a4e3-a738 // 
  Define changeset ID
  --changeset_a4e3-a738                                        // 
  Changeset 1 start
    Content-Type: application/http
    Content-Transfer-Encoding: binary
    [PUT...]

  --changeset_a4e3-a738                                        // 
  Changeset 2 start
    Content-Type: application/http
    Content-Transfer-Encoding: binary
    [POST...]

  --changeset_a4e3-a738--                                     // 
  Changeset (all) end

--batch_8219-6895                                              // 
Batch part 2 start
  Content-Type: application/http
  Content-Transfer-Encoding: binary
  [GET...]

--batch_8219-6895--                                            // 
Batch (all) end

```
## <span style="color: #F05D30">Inventory Master Interface</span> 
Inventory Master Interface is used for synchronization of Inventory related changes that occurred in Envi with other external systems since the specified point in time. The Interface combines data on the following entities:

 - Inventory
 - Inventory Vendors
 - Inventory Locations
 - Vendor Info

The following example shows how to achieve the same result with API in case request of InventoryHTTPHandler:

1. Define all endpoints used for the related data retrieving.

``` cs title="Example"
const string invntoryUrlTmpl = "/odata/Inventory/GetAllFromDate(from={0},facilityId={1},syncFlag={2})";
const string invntoryLocationsUrlTmpl = "/odata/InventoryLocations/GetAllFromDate(from={0},facilityId={1},syncFlag={2})";
const string invntoryVendorsUrlTmpl = "/odata/InventoryVendors/GetAllFromDate(from={0},facilityId={1},syncFlag={2})";
const string vendorsUrlTmpl = "/odata/Vendors/GetVendorsInfo(facilityId={0})";
const string dateFormat = "yyyy-MM-dd";

```
These endpoints are implemented using OData functionality; thus, you have to specify all parameters even if they are optional. If you want to omit some parameters, specify a string representation of null as a value.

Also, you need C# classes that represent all entities participating in the flow. The needed entities can be created based on metadata information.


``` cs title="Example"
public class InventoryLocation
      {
        public Guid? InventoryLocationId { get; set; }
        public Guid? InventoryId {get; set; }
        public string InventoryNo { get; set; }
        public Guid? FacilityId { get; set; }
        public string FacilityName { get; set; }
        public string FacilityNo { get; set; }
        public Guid? LocationId { get; set; }
        public string LocationName { get; set; }
        public string LocationNo { get; <set; }
        public string LocationUOM { get; set; }
        public int? LocationConversionFactor { get; set; }
        public string InventoryStockUOM { get; set; }
        public string DefaultIssueUOM { get; set; }
        public int? DefaultIssueConversionFactor { get; set; }
        public string DefaultCountUOM { get; set; }
        public int? DefaultCountConversionFactor { get; set; }
        public decimal? Cost { get; set; }
        public bool? IsBillable { get; set; }
        public bool? IsTaxable { get; set; }
        public byte? ItemType { get; set; }
        public string ItemTypeText { get; set; }
        public decimal? PriceMarkup { get; set; }
        public string PriceMarkupTypeText { get; set; }
        public bool? DisablePurchasing { get; set; }
        public int? MinQuantity { get; set; }
        public int? OnRequisition { get; set; }
        public int? MaxQuantity { get; set; }
        public int? SafetyStock { get; set; }
        public string BinShelf { get; set; }
        public string AssetLedgerNo { get; set; }
        public string ExpenseLedgerNo { get; set; }
        public bool? SyncFlag { get; set; }
        public DateTime? CostLastUpdated { get; set; }
        public Guid? CostLastUpdatedBy { get; set; }
        public DateTime? DateAdded { get; set; }
        public Guid? AddedBy { get; set; }
        public DateTime? LastUpdated { get; set; }
        public Guid? LastUpdatedBy { get; set; }
        public bool? ActiveStatus { get; set; }
        public DateTime? CostSynchronizationDate { get; set; }
        public string DefaultPurchaseUOM { get; set; }
        public byte? ValuationMethod { get; set; }
        public string ValuationMethodText { get; set; }
        public int? PendingOrders { get; set; }
        public int? SubmittedOrders { get; set; }
        public int? QuantityOnHand { get; set; }
        public string LastUpdatedByName { get; set; }
        public string AddedByName { get; set; }
        public string CostLastUpdatedByName { get; set; }
        public string CrossReferenceNo { get; set; }
      }

      public class InventoryVendor
      {
        public Guid? InventoryVendorId { get; set; }
        public Guid? InventoryId { get; set; }
        public string InventoryNo { get; set; }
        public Guid? VendorId { get; set; }
        public string VendorNo { get; set; }
        public string VendorName { get; set; }
        public Guid? FacilityId { get; set; }
        public string FacilityNo { get; set; }
        public string FacilityName { get; set; }
        public string VendorItemNo { get; set; }
        public string VendorUOM { get; set; }
        public int? VendorConversionFactor { get; set; }
        public decimal? VendorCost { get; set; }
        public int? VendorPriority { get; set; }
        public string ContractNo { get; set; }
        public DateTime? ContractExpDate { get; set; }
        public string ManufacturerItemNo { get; set; }
        public Guid? ManufacturerId { get; set; }
        public string ManufacturerNo { get; set; }
        public string ManufacturerName { get; set; }
        public string GTIN { get; set; }
        public DateTime? CostLastUpdated { get; set; }
        public Guid? CostLastUpdatedBy { get; set; }
        public DateTime? DateAdded { get; set; }
        public Guid? AddedBy { get; set; }
        public DateTime? LastUpdated { get; set; }
        public Guid? LastUpdatedBy { get; set; }
        public bool? ActiveStatus { get; set; }
        public string NDCNumber { get; set; }
        public bool? LockCost { get; set; }
        public string CostLastUpdatedByUserName { get; set; }
        public string AddedByUserName { get; set; }
        public string LastUpdatedByUserName { get; set; }
        public int? LeadTime { get; set; }
      }

      public class VendorInfo
      {
        public Guid? VendorId { get; set; }
        public string VendorName { get; set; }
        public string VendorNo { get; set; }
        public string Address1 { get; set; }
        public string Address2 { get; set; }
        public string City { get; set; }
        public string State { get; set; }
        public string Zip { get; set; }
        public string Country { get; set; }
        public string Url { get; set; }
        public string AccountNumber { get; set; }
        public bool? ActiveStatus { get; set; }
        public DateTime? LastUpdated { get; set; }
        public int? LeadTime { get; set; }
      }

```
2. Extend your Inventory entity with two or more properties.


``` cs title="Example"
public class Inventory
      {
        . . .
        . . .
        . . .
        public List<InventoryVendor> InventoryVendors { get; set; }
        public List<InventoryLocation> InventoryLocations{ get; set; }
      }

```
3. Use the following code to retrieve Inventory Master Interface data.

``` cs title="Example"
DateTime lastRunDate = new DateTime(2017, 10, 1);
      Guid? facilityPK = null;
      bool? syncFlag = null;

      //Obtain JWT token and set access token to authorization header
      await SetAuthHeader();

      //Retrieving of Inventory Info
      var inventoryUrl = string.Format(invntoryUrlTmpl,
        lastRunDate.Tostring(dateFormat),
        facilityPK?.Tostring() ?? "null",
        syncFlag?.Tostring() ?? "null");

      var response = await Client.GetAsync(inventoryUrl);
      var inventoryResult = await response.Content.ReadAsstringAsync();
      var inventory = JsonConvert.DeserializeObject<ODataListResponse<Inventory>>(inventoryResult).Value;

      // Retrieving of corresponding Inventory/Locations
      var inventoryLocationsUrl = string.Format(invntoryLocationsUrlTmpl,
        lastRunDate.Tostring(dateFormat),
        facilityPK?.Tostring() ?? "null",
        syncFlag?.Tostring() ?? "null");

      response = await Client.GetAsync(inventoryLocationsUrl);
      var inventoryLocationsResult = await response.Content.ReadAsstringAsync();
      var inventoryLocations = JsonConvert.DeserializeObject<ODataListResponse<InventoryLocation>>(inventoryLocationsResult).Value;

      // Retrieving of corresponding Inventory/Vendors
      var inventoryVendorsUrl = string.Format(invntoryVendorsUrlTmpl,
        lastRunDate.Tostring(dateFormat),
        facilityPK?.Tostring() ?? "null",
        syncFlag?.Tostring() ?? "null");

        response = await Client.GetAsync(inventoryVendorsUrl);
      var inventoryVenorsResult = await response.Content.ReadAsstringAsync();
      var inventoryVendors = JsonConvert.DeserializeObject<ODataListResponse<InventoryVendor>>(inventoryVenorsResult).Value;

      // Retrieving of resulting Vendor Ids
      var vendorIds = inventoryVendors.GroupBy(pk => pk.VendorId).Select(g => g.Key).ToList();

      // Retrieving of Vendors information
      var vendorsUrl = string.Format(vendorsUrlTmpl, facilityPK?.Tostring() ?? "null");
      var content = new stringContent(Serialize(new ListRepresentation<Guid?> { Value = vendorIds }), Encoding.UTF8, "application/json");

      response = await Client.PostAsync(vendorsUrl, content);
      var vendorsResult = await response.Content.ReadAsstringAsync();
      var vendors = JsonConvert.DeserializeObject<ODataListResponse<VendorInfo>>(vendorsResult).Value;

      // Getting information combined (adding of Inventory/Vendors and Inventory/Locations to corresponding Inventory)
      inventory.ForEach(i => i.InventoryLocations = new List<InventoryLocation>(inventoryLocations.Where(il => il.InventoryId == i.InventoryId).ToList()));
      inventory.ForEach(i => i.InventoryVendors = new List<InventoryVendor>(inventoryVendors.Where(iv => iv.InventoryId == i.InventoryId).ToList()));

```
Retrieving Vendors' information is based on the list provided by Vendor IDs. It is presented using a specific format, that is why the sample code uses the additional helper class ```ListRepresentation<T>```.

``` cs title="Example"
public class ListRepresentation<T>
      {
        [JsonProperty("value")]
        public List<T> Value { get; set; }
      }

```
## <span style="color: #F05D30">HTTP Depletion Interface</span> 

HTTP Depletion Interface is used for processing multiple usages. The Interface combines data on the following entities:

 - [Create Usages](#create-usages) ```/odata/Usages/BulkAdd```
 - [Create Usage Items](#create-usage-items) ```/odata/UsageItems/BulkAdd```
 - [Create Procedures](#create-procedures) ```/odata/UsageProcedures/BulkAdd```
 - [Submit Usages](#submit-usages) ```/odata/Usages/BulkSubmit```
The need for the Usage Procedure insertion depends on your Facility options. Use the POST method to perform these requests.

### <span style="color: #F05D30">Create Usages</span> 

The ```/odata/Usages/BulkAdd``` endpoint helps you to create multiple usages. For this, use the appropriate model.

**Facility No** and **Department No** are required to receive a successful response. The following example shows the process of usage creation.

``` cs title="Example"
public class Usage
    {
      /// <summary>
      /// Usage identidier
      /// </summary>
      public Guid? UsageId { get; set; }

      /// <summary>
      /// gets or sets the usage Ordinal No
      /// </summary>
      public int? UsageOrdinalNo { get; set; }

      /// <summary>
      /// Holds facility No of the usage
      /// </summary>
      public string FacilityNo { get; set; }

      /// <summary>
      /// Holds facility Name of the usage
      /// </summary>
      public string FacilityName { get; set; }

      /// <summary>
      /// Holds Department No of the usage
      /// </summary>
      public string DepartmentNo { get; set; }

      /// <summary>
      /// Holds Department Name of the usage
      /// </summary>
      public string DepartmentName { get; set; }

      /// <summary>
      /// Patient number
      /// </summary>
      public string PatientNo { get; set; }

      /// <summary>
      /// Usage number.
      /// </summary>
      public string UsageNo { get; set; }

      /// <summary>
      /// Holds Physician Number
      /// </summary>
      public string PhysicianNo { get; set; }

      /// <summary>
      /// Holds Schedule Number
      /// </summary>
      public string ScheduleNo { get; set; }

      /// <summary>
      /// Holds First Name of a Physician
      /// </summary>
      public string PhysicianFirstName { get; set; }

      /// <summary>
      /// Holds Last Name of a Physician
      /// </summary>
      public string PhysicianLastName { get; set; }

      /// <summary>
      /// Usage Date
      /// </summary>
      public DateTime? UsageDate { get; set; }

      /// <summary>
      /// Holds Usage Type
      /// </summary>
      public byte? UsageType { get; set; }

      /// <summary>
      /// Case number
      /// </summary>
      public string CaseNo { get; set; }

      /// <summary>
      /// Holds department PK
      /// </summary>
      public Guid? DepartmentId { get; set; }

      /// <summary>
      /// Holds FacilityPK
      /// </summary>
      public Guid? FacilityId { get; set; }

      /// <summary>
      /// Usage's Reference
      /// </summary>
      public string Reference { get; set; }

      /// <summary>
      /// Usage's Tracking Code
      /// </summary>
      public string TrackingCode { get; set; }
    }

```

The following fields can be populated to the newly created usage:

<style>
td, th {
   border: none!important;
}
</style>
|<div style="width:200px">Property </div> | <div style="width:380px">Explanation</div> |                      
|-----:|:-------|
|**facilityNo**: string <br> <span style="color: #F05D30">**required**</span> <br> *in formData* |Facility for the Usage <br> **If not provided**: 400 Bad Request|
|**usageDate**: string <br> *in formData* |Usage date <br> **If not provided**: Date according to the user Time Zone|
|**departmentNo**: string <span style="color: #F05D30">**required**</span> <br> *in formData* |Department for the Usage <br> **If not provided**: User Default Department in case it is set and matches with user Default Facility. Otherwise, ```none```|
|**patientNo**: string |Patient number <br> If not provided: ```none```|
|**reference**: string <br> *in formData* | Reference for the Usage <br> **If not provided**: Empty|
|**caseNo**: string <br> *in formData* |Number of case <br> **If not provided**: Empty|
|**trackingCode**: string <br> *in formData* |Tracking code of the Usage <br> **If not provided**: Empty|
|**physicianNo**: string <br> *in formData* |Physician number for the Usage <br> **If not provided**: The ```none``` value in case it is not specified or it doesn't match specified facility|
|**usageType**: string <br> *in formData* |**Standard** <br> Auto-Populated|
|**source**: string <br> *in formData* | **Auto** <br> Auto-Populated|

You can create several usages per one request using this example. For this, post the list of usages. As a result, you’ll retrieve a string that contains a unique identifier of created usages divided by the comma separator (,). In case one of the usages has an incorrect value, all items will not be saved.

You'll receive the following response.

``` cs title="Example"
/// <summary>
        /// Create usages.
        /// </summary>
        /// <param name="usages">List of usages.</param>
        /// <returns>Ids of new created Usages - string of Guid joined by ",".</returns>
        public static async Task<string> PostUsages(List<Usage> usages)
        {
          await SetAuthHeader();
          var content = new StringContent(Serialize(new { usages }), Encoding.UTF8, "application/json");
          var response = await Client.PostAsync($"/odata/Usages/BulkAdd", content);
          return JsonConvert.DeserializeObject<ODataSingleValueResponse<string>>(await response.Content.ReadAsStringAsync()).Value;
        }

```


The **Usage Notes** will be populated with data which cannot be mapped in the following format:

```
Not mapped:
Department:<departmentNo>
Patient: <patientNo>
Physician: <physicianNo>
```


### <span style="color: #F05D30">Create Usage Items</span> 

You can create multiple usage items per one request with the ```/odata/UsageItems/BulkAdd``` endpoint. For this, use the following model.

``` cs title="Example"
public class UsageItem
      {
        /// <summary>
        /// Get the usage item ID value.
        /// </summary>
        public Guid? UsageItemId { get; set; }

        /// <summary>
        /// Get the procedure code1 value.
        /// </summary>
        public string ProcedureCode1 { get; set; }

        /// <summary>
        /// Get the procedure name1 value.
        /// </summary>
        public string ProcedureName1 { get; set; }

        /// <summary>
        /// Get the procedure code2 value.
        /// </summary>
        public string ProcedureCode2 { get; set; }

        /// <summary>
        /// Get the procedure name2 value.
        /// </summary>
        public string ProcedureName2 { get; set; }

        /// <summary>
        /// Get or set the procedure1 ID value.
        /// </summary>
        public Guid? Procedure1Id { get; set; }

        /// <summary>
        /// Get or set the procedure2 ID value.
        /// </summary>
        public Guid? Procedure2Id { get; set; }

        /// <summary>
        /// Get the Usage Item created date value.
        /// </summary>
        public DateTime? Date { get; set; }

        /// <summary>
        /// Get or set the case no value.
        /// </summary>
        public string CaseNo { get; set; }

        /// <<summary>
        /// Get or set the facility ID value.
        /// <</summary>
        public Guid? FacilityId { get; set; }

        /// <summary>
        /// Get the name of the department.
        /// </summary>
        public string DepartmentName { get; set; }

        /// <summary>
        /// Get or set the department ID value.
        /// </summary>
        public Guid? DepartmentId { get; set; }

        /// <summary>
        /// Get or set the price extended value.
        /// </summary>
        public decimal? ExtendedPrice { get; set; }

        /// <summary>
        /// Get the patient value.
        /// </summary>
        public string Patient { get; set; }

        /// <summary>
        /// Get the name of the facility.
        /// </summary>
        public string FacilityName { get; set; }

        /// <summary>
        /// Get the facility no.
        /// </summary>
        public string FacilityNo { get; set; }

        /// <summary>
        /// Get the name of the doctor.
        /// </summary>
        public string DoctorName { get; set; }

        /// <summary>
        /// Get or set the doctor ID value.
        /// </summary>
        public Guid? DoctorId { get; set; }

        /// <summary>
        /// Get or set the vendor item no value.
        /// </summary>
        public string VendorItemNo { get; set; }

        /// <summary>
        /// Get or set the inventory description value.
        /// </summary>
        public string InventoryDescription { get; set; }

        /// <summary>
        /// Get the classification value.
        /// </summary>
        public string Classification { get; set; }

        /// <summary>
        /// Get or set the classification2 value.
        /// </summary>
        public string Classification2 { get; set; }

        /// <summary>
        /// Get or set the quantity value.
        /// </summary>
        public int? Quantity { get; set; }

        /// <summary>
        /// Get or set the uom value.
        /// </summary>
        public string UOM { get; set; }

        /// <summary>
        /// Get or set the price value.
        /// </summary>
        public decimal? Price { get; set; }

        /// <<summary>
        /// Get or set the conversion factor value.
        /// <</summary>
        public int? ConversionFactor { get; set; }

        /// <summary>
        /// Get the location no value.
        /// </summary>
        public string LocationNo { get; set; }

        /// <summary>
        /// Get the inventory no value.
        /// </summary>
        public string InventoryNo { get; set; }

        /// <summary>
        /// Get or set the manufacturer value.
        /// </summary>
        public string ManufacturerNo { get; set; }

        /// <summary>
        /// Get or set the manufacturer item no value.
        /// </summary>
        public string ManufacturerItemNo { get; set; }

        /// <summary>
        /// Get or set the tracking lot no value.
        /// </summary>
        public string LotNo { get; set; }

        /// <summary>
        /// Get or set the tracking serial no value.
        /// </summary>
        public string SerialNo { get; set; }

        /// <summary>
        /// Get or set the tracking expiration date value.
        /// </summary>
        public DateTime? ExpirationDate { get; set; }

        /// <summary>
        /// Get or set the item notes.
        /// </summary>
        public string ItemNotes { get; set; }

        /// <summary>
        /// Get the line no value.
        /// </summary>
        public int? LineNo { get; set; }

        /// <summary>
        /// Get or set the usage ordinal no value.
        /// </summary>
        public int? UsageOrdinalNo { get; set; }

        /// <summary>
        /// Get the usage ID value.
        /// </summary>
        public Guid? UsageId { get; set; }
      }

```

To create usage items, the usage ID is required.

The following fields can be populated to add usage items:


<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Property</div>   |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**usageId**: string <br> <span style="color: #F05D30">**required**</span> <br> *in formData* | ID for the Usage to create Line Items <br> **If not provided**: 400 Bad Request |
|**lineItemNo**: string <br> *in formData* |It is generated automatically and recalculated within active Usage Line Items <br> **If not provided**: Auto-populated |
|**inventoryNo**: string <br> *in formData* | It is validated by Facility (Inventory Group) <br> **If not provided**: Empty |
|**inventoryDescription**: string <br> *in formData* | It is populated from an existing Inventory in case it is mapped by Inventory No and Inventory Locations values <br> **If not provided**: Empty |
|**locationNo**: string <br> <span style="color: #F05D30">**required**</span> <br> *in formData* | It is populated from ```locationNo``` in case a specified location exists within the Usage Facility <br> **If not provided**: Usage Default Location |
|**vendorItemNo**: string <br> *in formData* | Is matched with appropriate Inventory Vendor data <br> **If not provided**: Empty |
|**manufacturerNo** : string <br> *in formData* | It is populated from Inventory Vendor in case the item is matched by ```vendorItemNo``` <br> **If not provided**: ```none``` |
|**manufacturerItemNo**: string <br> *in formData* | It is populated from Inventory Vendor in case the item is matched by ```vendorItemNo``` <br> **If not provided**: Empty |
|**lotNo**: string <br> *in formData* | It is populated from ```lotNo``` <br> **If not provided**: Empty |
|**serialNo**: string <br> *in formData* |It is populated from ```serialNo``` <br> **If not provided**: Empty |
|**expirationDate**: string <br> *in formData* | It is populated from ```expirationDate``` <br> **If not provided**: Empty |
|**quantity**: string <br> *in formData* | Quantity in Line Items <br> **If not provided**: 1 |
|**uom**: string <br> *in formData* | Can be matched with Inventory UOM <br> **If not provided**: EA |
|**conversionFactor**: string <br> *in formData* | It is populated from appropriate Inventory UOM Conversion Factor in case item is added as Inventory Item, and the specified UOM value matched with Inventory UOM <br> **If not provided**: 1 |
|**itemNotes**: string <br> *in formData* | It is populated from Item Notes <br> **If not provided**: Empty |

You'll receive the following response.

``` cs title="Example"
/// <summary>
        /// Posts the usage items.
        /// </summary>
        /// <param name="usageItems">List of usage items.</param>
        /// <returns>ID of new created Usage Items.</returns>
        public static async Task PostUsageItems(List<UsageItem> usageItems)
        {
          await SetAuthHeader();
          var content = new StringContent(Serialize(new { usageItems }), Encoding.UTF8, "application/json");
          var response = await Client.PostAsync("/odata/UsageItems/BulkAdd", content);
          await response.Content.ReadAsStringAsync();
        }

```

Usage Line Items Notes are populated with data which cannot be mapped in the following format:

```
Not mapped:
Department:<departmentNo>
Patient: <patientNo>
Physician: <physicianNo>

```

### <span style="color: #F05D30">Create Procedures</span> 
You can create multiple Procedures per one request with /odata/UsageProcedures/BulkAdd endpoint. For this, use the following model.

``` cs title="Example"
{
      /// <summary>
      /// Usage Procedure DTO
      /// </summary>
      public class UsageProcedure
      {
        /// <summary>
        /// Usage Procedure Id
        /// </summary>
        public Guid? UsageProcedureId { get; set; }

        /// <summary>
        /// Usage Id
        /// </summary>
        public Guid? UsageId { get; set; }

        /// <summary>
        /// Holds Procedure No to add
        /// </summary>
        public string ProcedureNo { get; set; }
      }

```

To create usage Procedure, Usage ID, and Procedure No are required. Usage Procedures are populated from procedureNo in case it matches Procedure No and Facility. The status of the procedure is not taken into account. You can add procedures only with unique values. The order of procedures is the same as it was provided in the request.

The following fields can be populated to add Usage Procedure:
     

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Property</div>     |  <div style="width:380px">Explanation</div>  |                      
|-----:|:-------|
|**usageID**: string <span style="color: #F05D30">**required**</span> <br> *in formData* |ID for the Usage to create Procedure <br> **If not provided**: 400 Bad Request |
|**procedureNo**: string <span style="color: #F05D30">**required**</span> <br> *in formData* | Populated from ```procedureNo``` in case it is matched by Procedure No and Facility. You can add procedures only with unique values. <br> **If not provided**: 400 Bad Request |

You'll receive the following response.

``` cs title="Example"
/// <summary>
        /// Posts the usage procedures.
        /// </summary>
        /// <param name="usageProcedures">List of usage procedures.</param>
        /// <returns>ID of new created Usage Procedures.</returns>
        public static async Task PostUsageProcedures(List<UsageProcedure> usageProcedures)
    {
          await SetAuthHeader();
          var content = new StringContent(Serialize(new { usageProcedures }), Encoding.UTF8, "application/json");
          var response = await Client.PostAsync("/odata/UsageProcedures/BulkAdd", content);
          await response.Content.ReadAsStringAsync();
    }

```

The **Usage Notes** field is populated with procedureNo, in case procedure with specified procedureNo doesn't exist or it exists within another Facility.

### <span style="color: #F05D30">Submit Usages</span> 

After appropriate items are inserted, you can submit the Usage with the ```/odata/Usages/BulkSubmit``` endpoint. For this, use the following model.

``` cs title="Example"
public class Usage
      public class Usage
      {
        /// <summary>
        /// Usage identidier
        /// </summary>
        public Guid? UsageId { get; set; }
      }

```



The following fields can be populated to submit Usage:

<style>
td, th {
   border: none!important;
}
</style>
| <div style="width:200px">Property</div>    |   <div style="width:380px">Explanation</div>     | 
|-----:|:-------|
|**usageID**: string <span style="color: #F05D30">**required**</span> <br> *in formData* | ID for the Usage to submit <br> **If not provided**: 400 Bad Request |    

You'll receive the response with 200 HTTP Status, in case all data is correct. If there is at least one line item with invalid data, the request will be sent but the response code will contain 400 Bad Request.

If the structure of the request is correct, you'll receive the 200 HTTP response and those usages that can be submitted will be submitted.

There can be the following main reasons for invalid data:

 - Incomplete line item
 - The line item with quantity 0
 - The line item with negative quantity and required tracking
 - Usage has been already submitted by another user.

``` cs title="Example"
/// <summary>
        /// Submits the usages.
        /// </summary>
        /// <param name="usageIds">List of usages.</param>
        /// <returns>Result of usages submittions.</returns>
        public static async Task<Dictionary<Guid, string>> SubmitUsages(List<Usage> usageIds)
        {
          await SetAuthHeader();
          var content = new StringContent(Serialize(new { usageIds }), Encoding.UTF8, "application/json");
          var response = await Client.PostAsync("/odata/Usages/BulkSubmit", content);
          return JsonConvert.DeserializeObject<Dictionary<Guid, string>>(
            JsonConvert.DeserializeObject<ODataErrorResponse>(await response.Content.ReadAsStringAsync())
              .Description
              .Message);
        }

```
## <span style="color: #F05D30">AP Batch and Export Invoices</span> 
To queue the batch and export it, you can use the following flow:

 - Create AP Batch
 - Retrieve AP Batch list (by ID)
 - Retrieve Invoices of AP Batch
 - Add Invoice to AP Batch
 - Export AP Batch
 - Submit to Queued

### <span style="color: #F05D30">Create AP Batch</span> 

The ```/odata/Batches``` endpoint helps you to create a new AP batch in the Pending status and use it for further exporting.

!!! note 

    You can use the following model for the request. But for successful AP batch creating, you can enter only the required batchNo and, if needed, add a reference.

``` json title="Model"
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
      "lastUpdatedByUserName": "string",
    }

```

<style>
td, th {
   border: none!important;
}
</style>
| Properties     |  Explanation |  |
|-----:|:-------|:-------|
|**apBatchedInvoiceId**:<br> string *(uuid)* | Unique Identifier of the AP Batched Invoice |  |
|**batchNo**: string | Identification Number of the Batch | |
|**reference**: string | Information concerning the Transaction | |
|**batchStatusId**: <br> integer *(int32)* | Unique Identifier of the AP Batch Status | |
|**batchStatus**: <br> string | Status of the AP Batch | |
|**batchTotal**: <br> number *(double)* | Total of the Batch | |
|**invoiceCount**: <br> integer *(int32)* | Count of the Invoices |  |
|**isScheduledExporting**: <br> boolean |Is Exporting of the AP Batch scheduled or not? |  |
|**lastExportDate**: <br> string *(date-time)* |Last Date when the AP Batch was exported |  |
|**dateCreated**: <br> string *(date-time)* | Date when the AP Batch was created |  |
|**createdBy**: <br> string *(uuid)* | Unique Identifier of the user who created the AP Batched Invoice |  |
|**createdByUserName**: <br> string | Name of the user who created the AP Batched Invoice |  |
|**lastUpdated**: string <br> *(date-time)* | Last Date when the AP Batched Invoice was updated |  |
|**lastUpdatedBy**: <br> string *(uuid)* | Unique Identifier of the last user who updated the AP Batched Invoice |  |
|**lastUpdatedByUserName**: <br> string | Name of the last user who updated the AP Batched Invoice |  |

As a result, response will contain AP Batch ID.

``` json title="Request Example"
{
      "batchNo": "123"
    }

```
``` json title="Response Example"
{
      "@odata.context": "https://api-demo.envi.net/odata/$metadata#Edm.Guid"
      "value;: "453bf1fe-7f48-4fd1-8ce5-be74f1002e84"
    }

```

``` cs title="Code Example"
/// <summary>
    /// Create batch.
    /// </summary>
    /// <returns>Task.</returns>
    private static async Task Batch()
    {
      // POST Request
      // Create Batch Model, only BatchNo is required
      var newBatch = new APBatch { BatchNo = "Batch No" };
      // Send request
      var batchPK = (await PostBatch(newBatch)).Value;
    }

    /// <summary>
    /// Create batch.
    /// </summary>
    /// <param name="batch">List of usages.</param>
    /// <returns>Id of new created batch - Guid.</returns>
    public static async Task<ODataSingleValueResponse<Guid>> PostBatch(APBatch batch)
    {
      await SetAuthHeader();
      var content = new StringContent(Serialize(batch), Encoding.UTF8, "application/json");
      var response = await Client.PostAsync($"/odata/Batches", content);
      return JsonConvert.DeserializeObject<ODataSingleValueResponse<Guid>>(await response.Content.ReadAsStringAsync());
    }

```

### <span style="color: #F05D30">Retrieve AP Batch List (by ID)</span> 
The ```odata/Batches``` endpoint helps you to see the list of AP Batches. To retrieve the specified AP Batch, add its ID and use the ```odata/Batches(batchID)```. Use the GET method for these endpoints.

You can find the model and possible request parameters in the [Operations](AP_Batch.md#get-the-list-of-ap-batches) section.

### <span style="color: #F05D30">Retrieve Invoices of AP Batch </span> 
To retrieve the list of vouchered invoices that can be added to the AP Batch, use the ```odata/Batches(BatchId)/Invoices``` endpoint with the GET method. The model is the same as the AP Matched invoice.

You can find the model and possible request parameters in the [Operations](AP_Batch.md#get-the-specified-ap-batched-invoice) section.

### <span style="color: #F05D30">Add Invoice to AP Batch </span> 
The ```odata/Batches(Batchid)/Invoices``` endpoint with the POST method helps you to include vouchered invoices to the AP batch. For this, specify the required Matched Invoice ID.

``` json title="Request Example"
{
      "apMatchedInvoiceId": "5a654132-c718-4da8-b5cb-9667566f4712"
    }

```
``` cs title="Code Example"
/// <summary>
    /// Add Invoices to Batch
    /// </summary>
    /// <param name="batchId">The batch id</param>
    /// <param name="invoices">List of Invoice id</param>
    /// <returns>Result of insertion</returns>
    private static async Task<bool> AddBatchInvoice(Guid batchId, List<Guid> invoices)
    {
      await SetAuthHeader();
      var content = new StringContent(Serialize(invoices), Encoding.UTF8, "application/json");
      var response = await Client.PostAsync($"odata/Batches({batchId})/Invoices", content);
      return response.IsSuccessStatusCode;
    }

```

### <span style="color: #F05D30">Export AP Batch </span> 
The ```odata/Batches(BatchId)/Export``` endpoint with the POST method helps you to export AP Batch. For this, specify the required AP Batch ID.

!!! note 

    AP Batch can be exported in case it contains at least one invoice.

After sending the valid request, the response will contain a successful result.


``` json title="Response Example"
{
      "@odata.context": "https://api-demo.envi.net/odata/$metadata#Edm.String",
      "value": "Batch is successfully exported"
    }

```
``` cs title="Code Example"
/// <summary>
    /// Submit Batch to Export
    /// </summary>
    /// <param name="batchId">The batch id</param>
    /// <returns>Result of submitting</returns>
    private static async Task<bool> Export(Guid batchId)
    {
      await SetAuthHeader();
      var response = await Client.PostAsync($"odata/Batches({batchId})/Export", null);
      return response.IsSuccessStatusCode;
    }

```

### <span style="color: #F05D30">Submit to Queued</span> 
The ```odata/Batches(batchId)/SubmitToQueued``` endpoint with the POST method helps you to submit the AP batch to the Queued status. For this, specify the required AP Batch ID.

``` cs title="Code Example"
/// <summary>
    /// Submit Batch to Queue
    /// </summary>
    /// <param name="batchId">The batch id</param>
    /// <returns>Result of submitting</returns>
    private static async Task<bool> SubmitToQueue(Guid batchId)
    {
      await SetAuthHeader();
      var response = await Client.PostAsync($"odata/Batches({batchId})/SubmitToQueued", null);
      return response.IsSuccessStatusCode;
    }

```
