# Licenses

The `licenses` API endpoint allows you to create, view, update, and delete licenses.

## License Properties

Attribute | Type | Description
--------- | ------- | -----------
`id` | integer | License id, the unique identifier for the resource.
`domain` | array | Array of domains where the license key has been applied.
`licenseno` | string | The license key.
`status` | string | Is the license INVALID or VALID.
`oid` | string | The order id associated with this license key.
`pid` | string | The package id associated with this license key.
`activation_date` | date | License activation date.
`expire_date` | date | License expire date.
`domain_limit` | integer | Maximum number of domains this license can be linked to.

## Get All Licenses

```shell
curl -X GET \
  https://yorusite.com/wp-json/wpdm/v1/licenses \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	"items_per_page": 10,
	"pid": 34
}'
```

> The JSON response looks like the following example:

```json
[
    {
        "id": "13",
        "domain": [
            "wpfanatic.com",
            "profiles.io"
        ],
        "licenseno": "02813-16550-26999-54314",
        "status": "1",
        "oid": "5a682a4e1e492",
        "pid": "804",
        "activation_date": "May 1, 2019",
        "expire_date": "May 1, 2020",
        "domain_limit": "10"
    },
    {
        "id": "9",
        "domain": [
            "wpdm.info"
        ],
        "licenseno": "02813-16550-26999-54314",
        "status": "1",
        "oid": "5a682a4e1e494",
        "pid": "804",
        "activation_date": "April 1, 2019",
        "expire_date": "April 30, 2019",
        "domain_limit": "5"
    }    
]
```

This endpoint retrieves all Licenses. Use query parameters to filter result.

### HTTP Request

<span class="http-request"><span class="http-verb http-get">GET</span><span class="api-endpoint">/wp-json/wpdm/v1/licenses</span></span>

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
`items_per_page` | `10` | Number of licenses to retrive.
`page` | `0` | The page number.
`pid` | empty | Retrieve licenses of a specific package.
`licenseno` | empty | Get the license details using the key.
`oid` | empty | Get license key assciated with an order id.

## Create a License

```shell
curl -X POST \
  https://yorusite.com/wp-json/wpdm/v1/licenses \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
     "domain": [
         "wpdownloadmanager.com",
         "example.io"
     ],
     "licenseno": "02813-16550-26999-54314",
     "status": "1",
     "oid": "5a682a4e1e494",
     "pid": "804",
     "activation_date": "April 1, 2019",
     "expire_date": "April 1, 2020",
     "expire_period": "0",
     "domain_limit": "5"
}'
```

> The JSON response looks like the following example:

```json
{
    "id": "9",
    "domain": [
        "wpdownloadmanager.com",
        "example.io"
    ],
    "licenseno": "02813-16550-26999-54314",
    "status": "1",
    "oid": "5a682a4e1e494",
    "pid": "804",
    "activation_date": "April 1, 2019",
    "expire_date": "April 1, 2020",
    "expire_period": "0",
    "domain_limit": "5"
}
```

This endpoint creates a new License and sets License properties based on POST data.

### HTTP Request

<span class="http-request"><span class="http-verb http-post">POST</span><span class="api-endpoint">/wp-json/wpdm/v1/licenses</span></span>

## Get a License

```shell
curl -X GET \
  https://yorusite.com/wp-json/wpdm/v1/licenses/9 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "id": "9",
    "domain": [
        "wpdownloadmanager.com",
        "example.io"
    ],
    "licenseno": "02813-16550-26999-54314",
    "status": "1",
    "oid": "5a682a4e1e494",
    "pid": "804",
    "activation_date": "April 1, 2019",
    "expire_date": "April 1, 2020",
    "expire_period": "0",
    "domain_limit": "5"
}
```

This endpoint retrieves a specific License by ID.

### HTTP Request

<span class="http-request"><span class="http-verb http-get">GET</span><span class="api-endpoint">/wp-json/wpdm/v1/licenses/:id</span></span>

## Update a License

```shell
curl -X PUT \
  https://yorusite.com/wp-json/wpdm/v1/licenses/9 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
     "domain": [
         "wpdownloadmanager.com",
         "example.io"
     ],
     "licenseno": "02813-16550-26999-54314",
     "status": "1",
     "oid": "5a682a4e1e494",
     "pid": "804",
     "activation_date": "April 1, 2019",
     "expire_date": "April 1, 2020",
     "expire_period": "0",
     "domain_limit": "5"
}'
```

> The JSON response looks like the following example:

```json
{
    "id": "9",
    "domain": [
        "wpdownloadmanager.com",
        "example.io"
    ],
    "licenseno": "02813-16550-26999-54314",
    "status": "1",
    "oid": "5a682a4e1e494",
    "pid": "804",
    "activation_date": "April 1, 2019",
    "expire_date": "April 1, 2020",
    "expire_period": "0",
    "domain_limit": "5"
}
```

This endpoint updates a specific License by ID.

### HTTP Request

<span class="http-request"><span class="http-verb http-put">PUT</span><span class="api-endpoint">/wp-json/wpdm/v1/licenses/:id</span></span>

## Delete a License

```shell
curl -X DELETE \
  https://yorusite.com/wp-json/wpdm/v1/licenses/9 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "id": "9",
    "domain": [
        "wpdownloadmanager.com",
        "example.io"
    ],
    "licenseno": "02813-16550-26999-54314",
    "status": "1",
    "oid": "5a682a4e1e494",
    "pid": "804",
    "activation_date": "April 1, 2019",
    "expire_date": "April 1, 2020",
    "expire_period": "0",
    "domain_limit": "5"
}
```

This endpoint deletes a specific License by ID.

### HTTP Request

<span class="http-request"><span class="http-verb http-delete">DELETE</span><span class="api-endpoint">/wp-json/wpdm/v1/licenses/:id</span></span>