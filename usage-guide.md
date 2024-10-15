# Usage Guide

####

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

Request Body

```bash
GET /api/v1/products
```



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

Request Body

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

