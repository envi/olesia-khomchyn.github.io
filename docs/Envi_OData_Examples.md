In this section, you can find some simple examples of the request preparation and request sending for the Inventory module using the C# programming language.

To communicate with Envi API, do the following:

1. Obtain a JWT access token.
2. Send an HTTP request to a resource URL:
    1. Specify the ```Authorization``` header with a valid ```access_token```.
    2. Specify other request headers, such as ```Content-Type``` or ```API-version```.
    3. Prepare request payload (body) for the POST, PUT, or PATCH request.
    4. Construct correct query options as a part of the URL for the GET request.
3. Handle the response.

!!! note 

    OData protocol has additional metadata information included in a response.


## <span style="color: #F05D30">Obtaining a JWT access token</span> 

The following example, written in the C# programming language, shows how to obtain a JWT token and how to use ```refresh_token``` in case ```access_token``` gets expired. For your convenience, introduce a class for representation of the authentication response. In JSON format, the authentication response looks like this.

``` json title="Example"
{
    "access_token": "access token information",
    "token_type": "bearer",
    "expires_in": 59,
    "refresh_token": "refresh token information"
    }

```
So, the following C# class will look like this.

``` cs title="Example"
public class JWT
        {
            public JWT()
            {
                IssuedAt = DateTime.Now;
            }

            [JsonProperty("access_token")]
            public string AccessToken { get; set; }

            [JsonProperty("token_type")]
            public string TokenType { get; set; }

            [JsonProperty("expires_in")]
            public int ExpiresIn { get; set; }

            [JsonProperty("refresh_token")]
            public string RefreshToken { get; set; }

            [JsonIgnore]
            public DateTime IssuedAt { get; }

            [JsonIgnore]
            public bool IsValid => IssuedAt.AddSeconds(ExpiresIn) > DateTime.Now;
        }
```

In the original JSON, there are two additions except for properties:

 - ```IssuedAt``` property – holds the date and time information when the token is received. The value of the property is populated in the constructor, so each time you de-serialize an authentication request, this property will be populated with the current date and time.
 - ```IsValid``` property – holds some simple logic to indicate whether ```access_token``` is still valid based on the IssuedAt value.

The example uses the ```Newtonsoft.Json``` nugget package to perform serialization or deserialization. To preserve correct behavior, additional properties are marked with the ```JsonIgnore``` attribute and all others–with the ```JsonProperty``` attribute.

To communicate with API, use an instance of the ```HttpClient``` standard .net class. The ```Private``` field is intended to hold the ```HttpClient``` instance and appropriate property with additional logic for instance creation in case it does not exist.

``` cs title="Example"
/// <summary>
    /// Base address of OData API Service
    /// </summary>
    private static readonly string _baseAddress = "https://api-demo.envi.net";

    /// <summary>
    /// Holds instance of correctly initialized HTTP Client
    /// </summary>
    private static HttpClient _client;

    private static HttpClient Client
    {
        get
        {
            if (_client == null)
            {
                _client = new HttpClient {
                    BaseAddress = new Uri(_baseAddress)
                };
                _client.DefaultRequestHeaders.Accept.Add(newMediaTypeWithQualityHeaderValue("application/json"));
            }

            return _client;
        }
    }

```
The following two methods actually perform this job.

``` cs title="Example"
/// <summary>
    /// Holds instance of obtained JWT token
    /// </summary>
    private static JWT _token;
    private static async Task<JWT> GetToken()
    {
      if (_token == null)
      {
        List<KeyValuePair<string, string>> requestData = new List<KeyValuePair<string, string>> {
          new KeyValuePair<string, string>("grant_type", "password"),
          new KeyValuePair<string, string>("client_id", "your_cliet_id_goes_here"),
          new KeyValuePair<string, string>("username", "user_name"),
          new KeyValuePair<string, string>("password", "password")
        };

    _token = await RequestToken(requestData);
      }

      if (!_token.IsValid)
      {
        List<KeyValuePair<string, string>> requestData = new List<KeyValuePair<string, string>> {
          new KeyValuePair<string, string>("grant_type", "refresh_token"),
          new KeyValuePair<string, string>("client_id", "your_cliet_id_goes_here"),
          new KeyValuePair<string, string>("refresh_token", _token.RefreshToken)
        };

    _token = await RequestToken(requestData);
      }return _token;
    }

```

``` cs title="Example" 
private static async Task<JWT> RequestToken(List<KeyValuePair<string, string>> requestData)
    {
      var response = await Client.PostAsync("oauth2/token", new FormUrlEncodedContent(requestData));
      var content = await response.Content.ReadAsStringAsync();

      return JsonConvert.DeserializeObject<JWT>(content);
    }

```

## <span style="color: #F05D30">Sending HTTP request to a resource URL</span> 

The examples are based on the Inventory module, so let’s introduce the .net class, which represents the Inventory entity and two additional classes, which will be helpful for response de-serialization.

The Inventory entity is generated based on the Inventory description from the metadata endpoint.

The following classes are provided for the default metadata level ``` minimal```.

``` cs title="Example"
public class Inventory
      {
      public Guid? InventoryId { get; set; }
      public Guid? OrganizationId { get; set; }
      public string OrganizationName { get; set; }
      public Guid? InventoryGroupId { get; set; }
      public string InventoryNo { get; set; }
      public string InventoryGroupName { get; set; }
      public string InventoryDescription { get; set; }
      public string InventoryDescription2 { get; set; }
      public string StockUOM { get; set; }
      public string ARBillingCode { get; set; }
      public string HCPCSCode { get; set; }
      public string Notes { get; set; }
      public DateTime? DateAdded { get; set; }
      public Guid? AddedId { get; set; }
      public string AddedByName { get; set; }
      public DateTime? LastUpdated { get; set; }
      public Guid? LastUpdatedBy { get; set; }
      public string LastUpdatedByName { get; set; }
      public bool? ActiveStatus { get; set; }
      public string UNSPSC { get; set; }
      public bool? IsLatex { get; set; }
      public Guid? ClassificationId { get; set; }
      public string ClassificationName { get; set; }
      public Guid? Classification2Id { get; set; }
      public string Classification2Name { get; set; }
      public string DefaultExpenseLedgerNo { get; set; }
      public string DefaultAssetLedgerNo { get; set; }
      public Guid? PeriopCategoryId { get; set; }
      public string PeriopCategory { get; set; }
      public string ItemType { get; set; }
      public bool Billable { get; set; }
      public byte? SystemTypeId { get; set; }
      public string SystemType { get; set; }
      }

```


## <span style="color: #F05D30">Retrieving entities list</span> 

The following generic class represents the response for the endpoint, which returns a paged list of entities.

Envi API response returns an object that contains a list with entities of the requested type, link to metadata endpoint with entity type description (```odata.context```), the number of entities in the database that conform to specified criteria (```odata.count```), and URL for the next page of data retrieving (```odata.nextLink```).

Before performing the request, set the authorization information in the request header. It is recommended to do verification of ```access_token``` validity each time before request sending since its guarantees that the request will not return a 401 error code.

``` cs title="Example"
public class ODataListResponse<T>
    {
        [JsonProperty("@odata.context")]
        public string ODataContext { get; set; }

        [JsonProperty("@odata.count")]
        public int ODataCount { get; set; }

        [JsonProperty("@odata.nextLink")]
        public string ODataNextLink { get; set; }

        public List<T> Value { get; set; }
    }

```
The following method will help to do this job.
``` cs title="Example"
private static async Task<bool> SetAuthHeader()
    {
      var auth = await GetToken();
      if (auth != null)
      {
        Client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("bearer", auth.AccessToken);
      }

      return auth != null;
    }
    
```
```SetAuthHeader``` method returns a Boolean value that will be not omitted but awaited. And, the following method performs actually the call itself.

``` cs title="Example"
private static async Task<ODataListResponse> GetInventoryList()
    {
      SetAuthHeader();
      var response = await Client.GetAsync("/odata/Inventory");
      return JsonConvert.DeserializeObject<ODataListResponse>(await response.Content.ReadAsStringAsync());
    }    
```

The OData protocol uses the system query options ```$skip``` and ```$top``` to implement server-driven paging, which allows clients to request a specific subset of data from a large collection.  In addition to these options, OData pagination also utilizes ```odata.nextLink```.

The ```odata.nextLink``` is a URL included in each list type response to show more results are available beyond what was returned in the first request.

When you make a request to an OData API, it may return only a subset of the total results (for example, 100 out of 1000). If there are other results, the API will include ```odata.nextLink``` in the response, which you can use to retrieve the next subset of the requested collection.

If the response does not include ```odata.nextLink```, it means that all records have been retrieved.

The following method allows you to retrieve all entities in the collection by using ```odata.nextLink```. 

``` cs title="Example"
private static async Task<ODataListResponse> GetInventoryList()
{
			var result = new List<T>();

			while (!string.IsNullOrEmpty(requestUri))
			{
				var list = await Get<ODataListResponse<T>>(requestUri);
				if (list.Value.Any())
				{
					result.AddRange(list.Value);
				}

				requestUri = list.ODataNextLink;
				if (!string.IsNullOrEmpty(requestUri))
				{
					requestUri = requestUri.Replace(_baseAddress, string.Empty);
				}
			}

			return result;
		}
```




## <span style="color: #F05D30">Retrieving entity details</span> 
The following method retrieves details of an Inventory item by the specified ID.

``` cs title="Example"
private static async Task<Inventory> GetInventoryById(Guid inventoryId)
    {
      await SetAuthHeader();
      var response = await Client.GetAsync($"/odata/Inventory({inventoryId})");
      return JsonConvert.DeserializeObject(await response.Content.ReadAsStringAsync());
    } 
```

## <span style="color: #F05D30">New entity creation</span> 
To add a new entity using Envi API, do the following:

1. Send the POST request to an appropriate resource, then provide new entity details with filled-in all required fields in JSON format.
2. If it's an Inventory item, populate the Inventory entity.
3. Serialize entity to JSON format and POST it to the Inventory endpoint.
4. Create a new Inventory item with all required fields.

``` cs title="Example"
var inventory = new Inventory
    {
      InventoryGroupId = new Guid("88212fc1-7698-40b3-8642-edd4ff793fcd"),
      InventoryNo = new Random().Next(0, int.MaxValue).ToString(),
      InventoryDescription = "InventoryDescription",
      StockUOM = "EA",
      SystemTypeId = 1,
      ActiveStatus = true
    };
```
During serialization of the request body, serializer settings should be configured to ignore properties with “null” value and use properties names in lower camel case. For this purpose, here is the following helper method.

``` cs title="Example"
private static string Serialize<T>(T target)
    {
      var serializerSettings = new JsonSerializerSettings
      {
        ContractResolver = new CamelCasePropertyNamesContractResolver(),
        NullValueHandling = NullValueHandling.Ignore
      };

      return JsonConvert.SerializeObject(target, serializerSettings);
    }
```
As a result of the POST operation, API returns the ID of a newly created entity. To deserialize the response for default metadata settings correctly, introduce a generic class that represents a single value response.

``` cs title="Example"
public class ODataSingleValueResponse<T>
    {
        [JsonProperty("@odata.context")]
        public string ODataContext { get; set; }

        public T Value { get; set; }
    }
```
The following method posts the new Inventory item to the API endpoint.

``` cs title="Example"
private static async Task<ODataSingleValueResponse<Guid>> PostInventory(Inventory newItem)
    {
      await SetAuthHeader();
      var content = new StringContent(Serialize(newItem), Encoding.UTF8, "application/json");
      var response = await Client.PostAsync("/odata/Inventory", content);
      return JsonConvert.DeserializeObject<ODataSingleValueResponse>(await response.Content.ReadAsStringAsync());
    }
```
## <span style="color: #F05D30">Update existing entity</span> 
To update an existing entity using Envi API, do the following:

1. Send the PUT request to an appropriate resource, and then provide the ID of the entity that will be updated as well as entity details with all required fields filled-in in JSON format.
2. In case of an Inventory item, populate the Inventory entity.
3. Serialize it to the JSON format and PUT it to the Inventory endpoint.
4. Retrieving entity details occurs before entity updating:
```
Inventory inventory = await GetInventoryById("88212fc1-7698-40b3-8642-edd4ff793fcd");
```
5. Then, update some fields with new information:
```
inventory.HCPCSCode = "H0001";
```
```
inventory.UNSPSC = "41120000";
```
6. Send resulting entity back to API:
```
var updateSuccessfull = PutInventory(inventory);
```

```cs  title="Example"
private static async Task<bool> PutInventory(Inventory inventory)
    {
    await SetAuthHeader();
    var content = new StringContent(Serialize(inventory), Encoding.UTF8, "application/json");
    var response = await Client.PutAsync($"odata/Inventory({inventory.InventoryId})", content);
    return response.IsSuccessStatusCode;
    }
```
## <span style="color: #F05D30">Partially update existing entity </span> 

In addition to full entity update, Envi API supports partial update based on the provided data with a help of the PATCH HTTP method. In case of entity patching, only changed fields should be sent to API. For example, if you want to update only Inventory No filed, do the following:

1. Create a new Inventory entity.

2. Set the only fields that have been changed, and then use the PATCH endpoint along with the target entity ID.

``` cs title="Example"
Inventory patch = new Inventory
    {
      InventoryNo = "78-95-1938"
    };
    var updateSuccessfull = await PatchInventory(new Guid("88212fc1-7698-40b3-8642-edd4ff793fcd"), patch);
```
The following method patches an existing Inventory item.

``` cs title="Example"
private static async Task<bool> PatchInventory(Guid entityId, Inventory patch)
    {
      await SetAuthHeader();
      var content = new StringContent(Serialize(patch), Encoding.UTF8, "application/json");
      var response = await Client.PatchAsync($"odata/Inventory({entityId})", content);
      return response.IsSuccessStatusCode;
    }
```

Since .net class HttpClient does not contain implementation of ``` PatchAsync```, for this purpose, use the following extension method.

``` cs title="Example"
public static Task<HttpResponseMessage> PatchAsync(this HttpClient client, string requestUri, HttpContent content)
    {
      HttpRequestMessage request = new HttpRequestMessage {
        Method = new HttpMethod("PATCH"),
        RequestUri = new Uri($"{client.BaseAddress}{requestUri}"),
        Content = content
      };
      return client.SendAsync(request);
    }
```