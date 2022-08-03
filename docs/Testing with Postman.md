To get started with the Envi OData API, we recommend to use a tool like Postman to test example requests. Postman is a tool that lets you construct, execute, and test HTTP requests in a quick and easy way. In this tutorial, you’ll learn how to set up environment and collection in Postman to work with different sample queries and see the results.

To run the collection in Postman, using our Github repository, perform the following:

1. Install **Postman** packaged app.
2. Sign in or register in Postman, and then open the app.
3. Go the [Download from Github](https://github.com/envi/Envi.SDK/tree/master/Envi.SDK/PostmanCollection). Import the **Envi.SDK.Examples.json** file from the Github repository.
4. Each endpoint requires its URL to the environment and an access token. Use your token for each request. For more information about access token, go to the Authentication article.

Once you have successfully imported the collection, you obtain a collection of requests for the most common operations, supported by the **Envi OData API**.

!!! note 

    For testing OData API with provided collection, specify environment before sending any request. The environment should contain variable with name url and value that represents base url of api (for example, https://api-demo.envi.net).
    ![image](img/postman.png)
    If you want to edit any of your environments or create a new one, click the **Manage your Environments** button (:material-cog:).


<style>
td, th {
   border: none!important;
}
</style>
| Properties     |   Explanation     |        |       |   |
|-----:|:-------|:-------|:-------| :-------|
|**usageID**: string <span style="color: #F05D30">**required**</span> <br> *in formData* | ID for the Usage to submit <br> **If not provided**: 400 Bad Request |         |       |    |

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







