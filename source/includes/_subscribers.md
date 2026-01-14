# Subscribers

The `subscribers` API endpoint allows you to create, view, update, and delete subscribers.

## Subscriber Properties

Attribute | Type | Description
--------- | ------- | -----------
`id` | integer | Subscriber id, the unique identifier for the resource.
`post_title` | string | The Package name from where the email was captured.
`pid` | integer | The Package id from where the email was captured.
`email` | string | User's email address.
`date` | date | The date of the download.
`custom_data` | array | Additional custom fields data added by the Quick Form.
`request_status` | string | Download link request status.

## Get All Subscribers

```shell
curl -X GET \
  https://yoursite.com/wp-json/wpdm/v1/subscribers \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	"items_per_page": 10,
	"page": 2,
	"package_id": 12
}'
```

> The JSON response looks like the following example:

```json
[
    {
        "post_title": "Multiple Locks",
        "id": "3",
        "email": "username@example.com",
        "pid": "30",
        "date": "March 29, 2019",
        "custom_data": {
            "name": "Shahriar Alam",
            "country": "Bangladesh",
            "Company": "W3 Eden, Inc.",
            "phone": "01720000001"
        },
        "request_status": "1"
    },
    {
        "post_title": "PDF Stamper",
        "id": "2",
        "email": "imwpdm@example.com",
        "pid": "12",
        "date": "March 29, 2019",
        "custom_data": {
            "name": "Shafaet Alam",
            "country": "Bangladesh",
            "Company": "W3 Eden, Inc.",
            "phone": "01120000001"
        },
        "request_status": "1"
    },
    {
        "post_title": "Directory Add-on",
        "id": "11",
        "email": "restapi@example.com",
        "pid": "30",
        "date": "March 29, 2019",
        "custom_data": {
            "name": "Shahnur Alam",
            "country": "Bangladesh",
            "Company": "W3 Eden, Inc.",
            "phone": "09120000001"
        },
        "request_status": "1"
    }
]
```

This endpoint retrieves all subscribers. Use query parameters to filter results.

### HTTP Request

<span class="http-request"><span class="http-verb http-get">GET</span><span class="api-endpoint">/wp-json/wpdm/v1/subscribers</span></span>

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
`items_per_page` | `10` | Number of records to retrieve.
`page` | `0` | The page number.
`start_date` | empty | Filter subscribers by date.
`end_date` | empty | Filter subscribers by date.
`package_id` | empty | Filter subscribers by Package. Set `package_id` to get subscribers of a specific package.

## Create a Subscriber

```shell
curl -X POST \
  https://yoursite.com/wp-json/wpdm/v1/subscribers \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	 "post_title": "Multiple Locks",
     "email": "shahriar@example.com",
     "pid": "30",
     "date": "March 29, 2019",
     "custom_data": {
         "name": "Shahriar Alam",
         "country": "Bangladesh",
         "Company": "W3 Eden, Inc.",
         "phone": "01700007911"
     },
     "request_status": "1"
}'
```

> The JSON response looks like the following example:

```json
{
    "post_title": "Multiple Locks",
    "id": "1",
    "email": "shahriar@example.com",
    "pid": "30",
    "date": "March 29, 2019",
    "custom_data": {
        "name": "Shahriar Alam",
        "country": "Bangladesh",
        "Company": "W3 Eden, Inc.",
        "phone": "01700007911"
    },
    "request_status": "1"
}
```

This endpoint creates a new Subscriber and sets Subscriber properties based on POST data.

### HTTP Request

<span class="http-request"><span class="http-verb http-post">POST</span><span class="api-endpoint">/wp-json/wpdm/v1/subscribers</span></span>

## Get a Subscriber

```shell
curl -X GET \
  https://yoursite.com/wp-json/wpdm/v1/subscribers/1 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "post_title": "Multiple Locks",
    "id": "1",
    "email": "shahriar@example.com",
    "pid": "30",
    "date": "March 29, 2019",
    "custom_data": {
        "name": "Shahriar Alam",
        "country": "Bangladesh",
        "Company": "W3 Eden, Inc.",
        "phone": "01700007911"
    },
    "request_status": "1"
}
```

This endpoint retrieves a specific Subscriber by ID.

### HTTP Request

<span class="http-request"><span class="http-verb http-get">GET</span><span class="api-endpoint">/wp-json/wpdm/v1/subscribers/:id</span></span>

## Update a Subscriber

```shell
curl -X PUT \
  https://yoursite.com/wp-json/wpdm/v1/subscribers/1 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	 "post_title": "Multiple Locks",
     "email": "shahriar@example.com",
     "pid": "30",
     "date": "March 29, 2019",
     "custom_data": {
         "name": "Shahriar Alam",
         "country": "Bangladesh",
         "Company": "W3 Eden, Inc.",
         "phone": "01700007911"
     },
     "request_status": "1"
}'
```

> The JSON response looks like the following example:

```json
{
    "post_title": "Multiple Locks",
    "id": "1",
    "email": "shahriar@example.com",
    "pid": "30",
    "date": "March 29, 2019",
    "custom_data": {
        "name": "Shahriar Alam",
        "country": "Bangladesh",
        "Company": "W3 Eden, Inc.",
        "phone": "01700007911"
    },
    "request_status": "1"
}
```

This endpoint updates a specific Subscriber by ID.

### HTTP Request

<span class="http-request"><span class="http-verb http-put">PUT</span><span class="api-endpoint">/wp-json/wpdm/v1/subscribers/:id</span></span>

## Delete a Subscriber

```shell
curl -X DELETE \
  https://yoursite.com/wp-json/wpdm/v1/subscribers/1 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "post_title": "Multiple Locks",
    "id": "1",
    "email": "shahriar@example.com",
    "pid": "30",
    "date": "March 29, 2019",
    "custom_data": {
        "name": "Shahriar Alam",
        "country": "Bangladesh",
        "Company": "W3 Eden, Inc.",
        "phone": "01700007911"
    },
    "request_status": "1"
}
```

This endpoint deletes a specific Subscriber by ID.

### HTTP Request

<span class="http-request"><span class="http-verb http-delete">DELETE</span><span class="api-endpoint">/wp-json/wpdm/v1/subscribers/:id</span></span>