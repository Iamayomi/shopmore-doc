# Endpoints

The current version of the API consumes data – information about users, product, cart, order, review details and about your domain. Apart from that, via the API you can login/signup a user in your domain, where a user can perform some funstionalities. Please make sure, that you are accessing the URLs below, under HTTPs connections, otherwise you will receive an error.

{% hint style="info" %}
Use these endpoints all response will return JSON
{% endhint %}



**Endpoints**

* Users

<table><thead><tr><th width="410">Endpoint</th><th>Uses</th></tr></thead><tbody><tr><td>POST api/v1/auth/register</td><td>create new user</td></tr><tr><td>POST api/v1/auth/signin</td><td>user login in</td></tr><tr><td>POST api/v1/auth/{ID}/verify-email</td><td>user verify email</td></tr><tr><td>POST api/v1/auth/reset-password</td><td>user reset password</td></tr><tr><td>POST api/v1/auth/verify-password-reset-code</td><td>user verify password reset</td></tr><tr><td>POST api/v1/auth/{ID}/verify-phone</td><td>user verify phone</td></tr><tr><td>PATCH api/v1/auth/reset-password</td><td>user reset password </td></tr><tr><td>POST api/v1/auth/forget-password</td><td>user forget password</td></tr><tr><td>GET api/v1/users/{ID}getUser-profile</td><td>get user profile</td></tr><tr><td>POST api/v1/users/change-password</td><td>user change password</td></tr><tr><td>PATCH api/v1/users/update-me</td><td>update my profile</td></tr><tr><td>PATCH api/v1/users/delete-myAccount</td><td>user delete my password</td></tr></tbody></table>



* Products

| Endpoints                                 | Uses               |
| ----------------------------------------- | ------------------ |
| GET api/v1/auth/products                  | lists all products |
| GET api/v1/auth/products/{ID}/get-product | get a product      |

{% hint style="info" %}
**Note:** The params for product search is at [usage-guide.md](../usage-guide.md "mention")page
{% endhint %}



* Carts&#x20;

| Endpoints                               |                     |
| --------------------------------------- | ------------------- |
| POST api/v1/auth/carts/{ID}/add-to-cart | add product to cart |
| GET api/v1/auth/carts/get-cart          | get a cart          |
| DELETE api/v1/auth/carts/remove-cart    | remove  cart        |



* Reviews

<table><thead><tr><th width="439">Endpoint</th><th>Use</th></tr></thead><tbody><tr><td>POST api/v1/auth/reviews{ID}/add-review-product</td><td>add review to product</td></tr></tbody></table>



* Checkouts

<table><thead><tr><th width="409">Endpoint</th><th>Use</th></tr></thead><tbody><tr><td>POST api/v1/checkouts/{ID}/checkout-session</td><td>product checkout</td></tr></tbody></table>







