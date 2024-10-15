# Usage Guide

{% hint style="info" %}
Read carefully before start&#x20;
{% endhint %}



This document provides detailed information about the API endpoints and their usage for interacting with shopmore e-commerce Resful API. The API is designed to allow developers to build custom applications and integrations with our platform.

#### **User Authentication**

**POST /signup**

* **Description:** Creates a new user account.

Request Body

```bash
POST /api/vi/users/register
content-type: application/json

{
    "username": "testing",
    "email": "testing@gmail.com",
    "phoneNumber": "+23480352562",
    "gender": "male",
    "password": "communication",
    "acceptedTerms": true
}
```

Response body

```json
{
    "status": "success",
    "message": "User sign up successfully",
    "data": {
        "User": {
            "active": true,
            "role": "user",
            "otpExpiry": null,
            "isEmailVerified": false,
            "isPhoneVerified": false,
            "userCreatedAt": "2024-09-04T02:15:15.928Z",
            "id": 1,
            "email": "test@gmail.com",
            "acceptedTerms": true,
            "username": "test_0",
            "gender": "male",
            "ip": "::1",
            "country": null,
            "otp": null
        }
    }
}
```

POST/users

* Description: To login a user by email and password

Request Body&#x20;

```bash
POST /api/vi/users/signin
content-type: application/json

{
    "email": "testing@gmail.com",
    "password": "communication",
}
```



Response Body

```json
{
    "status": "success",
    "message": "User sign up successfully",
        "user": {
            "active": true,
            "role": "user",
            "otpExpiry": null,
            "isEmailVerified": false,
            "isPhoneVerified": false,
            "userCreatedAt": "2024-09-04T02:15:15.928Z",
            "id": 1,
            "email": "test@gmail.com",
            "acceptedTerms": true,
            "username": "test_0",
            "gender": "male",
            "ip": "::1",
            "country": null,
            "otp": null
        }
    }
}
```



Product

**GET /products**

* To retrieve all products

Request Header

```bash
GET /api/v1/products
```

Request Params

<table><thead><tr><th width="134">params</th><th width="160">value</th><th>Uses</th></tr></thead><tbody><tr><td>rating[lt]</td><td>4</td><td><p></p><p>Search products query by rating E.g gte, lt, gt, lte.</p></td></tr><tr><td>sort</td><td>-price, name, quantity</td><td>Sort products query by -price is DESC, name is ASC is also set to default</td></tr><tr><td>limit</td><td><br>name, price,  imageUrl</td><td>Limiting the attribute of products</td></tr><tr><td>price</td><td>22.3</td><td><p></p><p>Search products query by price E.g 55.99, 22.3</p></td></tr><tr><td>category</td><td>Electronics</td><td><p></p><p>Search products query by category E.g Clothing,<br>Electronics</p><p><br></p></td></tr><tr><td>name</td><td>WD 2TB Elements Portable</td><td><p>Search by the name of the products</p><p></p></td></tr><tr><td>subcategory</td><td>Accessories</td><td><p></p><p>Search products query by subcategory E.g Men's<br>Computers and Laptops<br>Accessories</p></td></tr><tr><td>page</td><td>3</td><td>Search by product pagination </td></tr></tbody></table>



Response Body

```json

    "status": "SUCCESS",
    "total": 2,
    "data": {
        "products": [
                {
                    "id": 1,
                    "name": "Cocoa Butter cream",
                    "price": 56.99,
                    "description": "it is a body lotion rub it on your body smoothly after you bath",
                    "currency": "USD",
                    "imageUrl": "https://fakestoreapi.com/img/61U7T1koQqL._AC_SX679_.jpg",
                    "quantity": 1000,
                    "productAddedAt": "2024-09-07T13:26:24.313Z",
                    "subcategoryId": 1,
                    "subcategoryname": null,
                    "categoryid": 1,
                    "categoryname": "Health and Beauty"
                },
                {
                    "id": 2,
                    "name": "Cloths",
                    "price": 46.99,
                    "description": "Fitted wears on your body smoothly comfortable",
                    "currency": "USD",
                    "imageUrl": "https://fakestoreapi.com/img/61U7T1koQqL._AC_SX679_.jpg",
                    "quantity": 1000,
                    "productAddedAt": "2024-09-07T13:26:24.313Z",
                    "subcategoryId": 1,
                    "subcategoryname": null,
                    "categoryid": 2,
                    "categoryname": "Cloths"
          ]
         }
```

Product

**GET /products**

* Description To get a  product by id&#x20;

Request Header

```bash
GET /api/v1/products/1/get-product
```

Response Body

```json
 "status": "SUCCESS",
    "data": {
        "products":{
                    "id": 1,
                    "name": "Cocoa Butter cream",
                    "price": 56.99,
                    "description": "it is a body lotion rub it on your body smoothly after you bath",
                    "currency": "USD",
                    "imageUrl": "https://fakestoreapi.com/img/61U7T1koQqL._AC_SX679_.jpg",
                    "quantity": 1000,
                    "productAddedAt": "2024-09-07T13:26:24.313Z",
                    "subcategoryId": 1,
                    "subcategoryname": null,
                    "categoryid": 1,
                    "categoryname": "Health and Beauty"
                }
    }
```

