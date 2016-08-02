# rest-api-response-format
REST API response format inspired by Google, Twitter, Amazon and some posts on internet:

## Rest API Success Responses

1- GET single resource - HTTP Response Code: **200**
```javascript
    {
        "data": {
            "field1": "value1",
            "field2": "value2"
        }
    }
```
2- GET resource list - HTTP Response Code: **200**
```javascript
    {
        "_meta": {
            "count": 100,
            "page": 5,
            "limit": 20,
            "links": [
                { "self": "/products?page=5&limit=20" },
                { "first": "/products?page=0&limit=20" },
                { "previous": "/products?page=4&limit=20" },
                { "next": "/products?page=6&limit=20" },
                { "last": "/products?page=26&limit=20" },
            ]
        },
        "data": [
            {
                "field1": "value1",
                "field2": "value2"
            }, {
                "field1": "value1",
                "field2": "value2"
            }
        ]
    }
```
3- DELETE - HTTP Response Code: **204**
```javascript
    {
        "message": "resource with id 1234 was deleted"
    }
```
4- POST - HTTP Response Code: **201**
```javascript
    {
        "message": "resource with id 1234 was created"
    }
```
5- PUT - HTTP Response Code: **201**
```javascript
    {
        "message": "resource with id 1234 was updated"
    }
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
