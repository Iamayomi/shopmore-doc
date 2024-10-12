# API REFERENCES

```bash
Authorization: Bearer <YOUR_API_KEY>
```

**Endpoints**

* User  Endpoints

<table><thead><tr><th width="410"></th><th></th></tr></thead><tbody><tr><td>POST api/v1/auth/register</td><td>create new user</td></tr><tr><td>POST api/v1/auth/signin</td><td>user login in</td></tr><tr><td>POST api/v1/auth/{ID}/verify-email</td><td>user verify email</td></tr><tr><td>POST api/v1/auth/reset-password</td><td>user reset password</td></tr><tr><td>POST api/v1/auth/verify-password-reset-code</td><td>user verify password reset</td></tr><tr><td>POST api/v1/auth/{ID}/verify-phone</td><td>user verify phone</td></tr><tr><td>PATCH api/v1/auth/reset-password</td><td>user reset password </td></tr><tr><td>POST api/v1/auth/forget-password</td><td>user forget password</td></tr><tr><td>GET api/v1/users/{ID}getUser-profile</td><td>get user profile</td></tr><tr><td>POST api/v1/users/change-password</td><td>user change password</td></tr><tr><td>PATCH api/v1/users/update-me</td><td>update my profile</td></tr><tr><td>PATCH api/v1/users/delete-myAccount</td><td>user delete my password</td></tr></tbody></table>



* Product Endpoints

|                                           |                    |
| ----------------------------------------- | ------------------ |
| GET api/v1/auth/products                  | lists all products |
| GET api/v1/auth/products/{ID}/get-product | get a product      |

* Cart&#x20;

|                                         |                     |
| --------------------------------------- | ------------------- |
| POST api/v1/auth/carts/{ID}/add-to-cart | add product to cart |
| GET api/v1/auth/carts/get-cart          | get a cart          |
| DELETE api/v1/auth/carts/remove-cart    | remove  cart        |



* Review&#x20;

<table><thead><tr><th width="439"></th><th></th></tr></thead><tbody><tr><td>POST api/v1/auth/reviews{ID}/add-review-product</td><td>add review to product</td></tr></tbody></table>



* Checkout&#x20;

<table><thead><tr><th width="409"></th><th></th></tr></thead><tbody><tr><td>POST api/v1/checkouts/{ID}/checkout-session</td><td>product checkout</td></tr></tbody></table>





ERROR CODES

* **400 Bad Request:** The server cannot process the request due to invalid syntax or missing parameters.
* **401 Unauthorized:** The client is not authenticated.
* **403 Forbidden:** The client is authenticated but lacks permission to access the resource.
* **404 Not Found:** The requested resource could not be found.
* **500 Internal Server Error:** A generic error occurred on the server.





