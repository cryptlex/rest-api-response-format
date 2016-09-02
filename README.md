# rest-api-response-format
REST API response format using HTTP status codes

The **swagger.yaml** file for following sample responses is available at:

https://github.com/adnan-kamili/swagger-sample-template

## Rest API Success Responses

1- GET single resource - HTTP Response Code: **200**
```javascript
    HTTP/1.1 200
    Content-Type: application/json

    {
        "id": 10,
        "name": "shirt",
        "color": "red",
        "price": "$23"
    }
```
2- GET resource list - HTTP Response Code: **200**
```javascript
    HTTP/1.1 200
    X-Pagination-Count: 100
    X-Pagination-Page: 5
    X-Pagination-Limit: 20
    Content-Type: application/json
    
    [
      {
        "id": 10,
        "name": "shirt",
        "color": "red",
        "price": "$23"
      }
    ]
```

3- POST - HTTP Response Code: **201**
```javascript
    HTTP/1.1  201
    Content-Type: application/json
 
    {
      "message": "The item was created successfully"
    }
```
4- PATCH - HTTP Response Code: **200/204** 

**Request Content-Type: application/merge-patch+json** - https://tools.ietf.org/html/rfc7396

If updated entity is to be sent after the update
```javascript
    HTTP/1.1  200
    Content-Type: application/json
 
    {
        "id": 10,
        "name": "shirt",
        "color": "red",
        "price": "$23"
    }
```
If updated entity is not to be sent after the update
```javascript
    HTTP/1.1  204
```
5- DELETE - HTTP Response Code: **204**
```javascript
    HTTP/1.1  204
```


## Rest API Error Responses

1- GET resource - HTTP Response Code: **404**

```javascript
    HTTP/1.1  404
    Content-Type: application/json
 
    {
      "message": "The item does not exist"
    }
```
2- DELETE resource - HTTP Response Code: **404**
```javascript
    HTTP/1.1  404
    Content-Type: application/json
 
    {
      "message": "The item does not exist"
    }
```
3- POST -  HTTP Response Code: **400**
```javascript
    HTTP/1.1  400
    Content-Type: application/json
    
    {
        "message": "Validation errors in your request", /* skip or optional error message */
        "errors": [
            {
                "message": "Oops! The value is invalid",
                "code": 34,
                "field": "email"
            },
            {
                "message": "Oops! The format is not correct",
                "code": 35,
                "field": "phoneNumber"
            }
        ]
    }
```
4- PATCH -  HTTP Response Code: **400/404**
```javascript
    HTTP/1.1  400
    Content-Type: application/json
    
    {
        "message": "Validation errors in your request", /* skip or optional error message */
        "errors": [
            {
                "message": "Oops! The format is not correct",
                "code": 35,
                "field": "phoneNumber"
            }
        ]
    }
    
    
    HTTP/1.1  404
    Content-Type: application/json
 
    {
      "message": "The item does not exist"
    }
```
5- VERB Unauthorized - HTTP Response Code: **401**
```javascript
    HTTP/1.1  401
    Content-Type: application/json
 
    {
      "message": "Authentication credentials were missing or incorrect"
    }
```
6- VERB Forbidden - HTTP Response Code: **403**
```javascript
    HTTP/1.1  403
    Content-Type: application/json
 
    {
      "message": "The request is understood, but it has been refused or access is not allowed"
    }
```
7- VERB Too Many Requests - HTTP Response Code: **429**
```javascript
    HTTP/1.1  429
    Content-Type: application/json
 
    {
      "message": "The request cannot be served due to the rate limit having been exhausted for the resource"
    }
```
8- VERB Internal Server Error - HTTP Response Code: **500**
```javascript
    HTTP/1.1  500
    Content-Type: application/json
 
    {
      "message": "Something is broken"
    }
```
9- VERB Service Unavailable - HTTP Response Code: **503**
```javascript
    HTTP/1.1  503
    Content-Type: application/json
 
    {
      "message": "The server is up, but overloaded with requests. Try again later!"
    }
```
