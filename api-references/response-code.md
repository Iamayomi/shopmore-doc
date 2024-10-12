# Response code

Shopmore API uses HTTP response codes to indicate success or failure of requests. Specifically, codes in the 2xx range indicate success, codes in the 4xx range indicate an error that resulted from the provided arguments (e.g. instead of an integer a string is supplied) and 500 error code indicate an internal Shopmore error. Please be aware that you will receive an error too, in case you will try to access an endpoint via non HTTPs connection.

Responses code

* **200 OK:** The request was successful.
* **201 Created:** A new resource was created.
* **400 Bad Request:** The server cannot process the request due to invalid syntax or missing parameters.
* **401 Unauthorized:** The client is not authenticated.
* **403 Forbidden:** The client is authenticated but lacks permission to access the resource.
* **404 Not Found:** The requested resource could not be found.
* **500 Internal Server Error:** A generic error occurred on the server.

{% hint style="info" %}
All errors return JSON consisting of a type (invalid\_request\_error or api\_error) and a message describing the error
{% endhint %}







