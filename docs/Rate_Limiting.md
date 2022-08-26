To maintain performance and availability across Envi OData API as well as avoid unexpected load spikes on our servers, it is critical to maintain application traffic within the limits of the API capacity.

Without rate limiting, each user may request as often as they like, which can lead to overusing of requests that affects other consumers. After rate limiting is enabled, users are limited to a fixed number of requests per second, minute, hour, or week.

We are using rate limiting solution to protect our API from malicious overuse. It is also important to mention that now apps do not consume more resources than permitted. To communicate with the rate-limited API after reaching the limit, API returns specific HTTP Status Code 429 with the following message:

!!! note ""

    API calls quota exceeded! Maximum admitted &lt;Requests_Amount&gt; per &lt;Period_Of_Time&gt;.



In case you have the limit set to 1000 requests per hour and request limit is reached, you will receive HTTP Status Code 429 with the following reason:


!!! note ""

    429 API calls quota exceeded! Maximum admitted 1000 per Hour.



In addition, the response contains the **Retry-After** header. Value of the header contains a number of seconds that you should wait before performing the new request to the API. For example, **Retry-After: 1256**.

Global rate limiting rules are set for every API user. If you need to increase your requests rate limit for some reason, contact our [support team](mailto:support@envi.com).