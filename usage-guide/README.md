# Usage Guide

####

This document provides detailed information about the API endpoints and their usage for interacting with shopmore e-commerce Resful API. The API is designed to allow developers to build custom applications and integrations with our platform.

#### **User Authentication**

**POST /signup**

* **Description:** Creates a new user account.

Request Body

```bash
POST /api/vi/users
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
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiaWF0IjoxNzI1NDE2MTI3LCJleHAiOjE3MzMxOTIxMjd9.P3bCCa6MU8AA9eioa_2D447fj49ewYFgNV_ZJKXn3RY",
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
            "password": "$2a$10$3BIbaDrw2dUN2T29c9Aw8uaEhTeOt58gznmmuDyk/7/y9gp96i5oG",
            "phoneNumber": "080900974006",
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

Request

```bash
GET /api/v1/products
```



Response

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

