# GitHub Repositry

Our [Github Repository](https://github.com/envi/Envi.SDK) сontains a source code of SDK and examples of how to use Envi OData public API.It consists of three projects:

 - **Api.Common.Entities** – contains DTO classes (models) and enums that will be used by API and SDK in the nearest future.
 - **Envi.SDK** – contains generic helper classes which represent different kinds of OData request or response messages. The **Program** class contains the following examples of API invocation:
    - Obtaining the **JWT token**, using access token for auth, and refreshing the **JWT token** when it expires.
    - Using simple **GET**, **POST**, **PUT**, and **PATCH** calls based on Inventory module. Generally, all implemented modules use the same pattern.
    - Retrieving **Inventory Master Interface** data using API.
    - Using **Batch Request** (in case multiple requests are sent in a batch).
 - **Postman Collections** – contains available collections for testing HTTP requests in a quick and easy way.