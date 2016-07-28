# rest-api-response-format

Rest API Success Responses

1- GET single resource - HTTP Response Code: 200

    {
        "data": {
            "field1": "value1",
            "field2": "value2"
        },
        "message": null /* skip or optional success message */
    }

2- GET resource list - HTTP Response Code: 200

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
        ],
        "message": null /* skip or optional success message */
    }

3- POST - HTTP Response Code: 201

    {
        "message": "resource {{id}} was created"
    }
    
4- PUT - HTTP Response Code: 201

    {
        "message": "resource {{id}} was updated"
    }
    
5- DELETE - HTTP Response Code: 204

    {
        "message": "resource {{id}} was deleted"
    }
