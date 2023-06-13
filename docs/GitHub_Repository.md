# GitHub Repository

Our [GitHhub Repository](https://github.com/envi/Envi.SDK) сontains a source code of SDK and examples of how to use Envi OData public API. It consists of three projects:

 - **API.Common.Entities**–contains DTO classes (models) and enums that will be used by API and SDK in the nearest future.
 - **Envi.SDK**–contains generic helper classes representing different kinds of OData request or response messages. The **Program** class includes the following examples of API invocation:
    - Obtaining the **JWT token**, using the access token for auth, and refreshing the **JWT token** when it expires.
    - Using simple **GET**, **POST**, **PUT**, and **PATCH** calls based on the Inventory module. Generally, all implemented modules use the same pattern.
    - Retrieving **Inventory Master Interface** data using API.
    - Using **Batch Request** (in case multiple requests are sent in a batch).
 - **Postman Collections**–contains available collections for testing HTTP requests in a quick and easy way.