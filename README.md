# rest-api-response-format
REST API response format inspired by Google, Twitter, Amazon and some posts on internet.

The swagger file for following sample responses is available at:

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
4- PATCH - HTTP Response Code: **201**
```javascript
    HTTP/1.1  201
    Content-Type: application/json
 
    {
      "message": "The item was updated successfully"
    }
```
5- DELETE - HTTP Response Code: **204**
```javascript
    HTTP/1.1  204
```


## Rest API Error Responses

1- GET resource - HTTP Response Code: **400/404**

```javascript
    {
        "message": "Sorry, the resource does not exist (404) or malformed query (400)"
    }
```
2- DELETE resource - HTTP Response Code: **404**
```javascript
    {
        "message": "Sorry, the resource does not exist"
    }
```
3- POST -  HTTP Response Code: **400**
```javascript
    {
        "message": null, /* skip or optional error message */
        "errors": [
            {
                "message": "Sorry, the field value is invalid",
                "code": 34,
                "field": "email"
            },
            {
                "message": "Some other error",
                "code": 35,
                "field": "phoneNumber"
            }
        ]
    }
```
4- PATCH -  HTTP Response Code: **400/404**
```javascript
    {
        "message": "Sorry, the resource does not exist (404)"
    }
    or
    {
        "message": null, /* skip or optional error message for 400 */
        "errors": [
            {
                "message": "Sorry, the field value is invalid",
                "code": 34,
                "field": "email"
            },
            {
                "message": "Sorry, the field value is invalid",
                "code": 35,
                "field": "phoneNumber"
            }
        ]
    }
```
5- VERB Unauthorized - HTTP Response Code: **401**
```javascript
    {
        "message": "you are not authorized to access the resource"
    }
```
6- VERB Forbidden - HTTP Response Code: **403**
```javascript
    {
        "message": "you are not allowed to access the resource"
    }
```
7- VERB Server Error - HTTP Response Code: **5XX**
```javascript
    {
        "message": "server error message"
    }
```
