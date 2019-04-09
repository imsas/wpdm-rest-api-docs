# Download Stats

The `stats` API endpoint allows you to create, view, update, and delete package download stats.

## Download Stat Properties

Attribute | Type | Description
--------- | ------- | -----------
`id` | integer | Download Stat id, the unique identifier for the resource.
`post_title` | string | Downloaded Package name.
`pid` | integer | Downloaded Package id.
`uid` | integer | The id of the user if downloaded as logged in user, otherwise empty.
`oid` | string | Order id if the stat is associated with a premium package order.
`year` | integer | Downloaded year.
`month` | integer | Downloaded month.
`day` | integer | Downloaded day.
`day` | integer | Downloaded day.
`timestamp` | string | Unix timestamp of the download time.
`ip` | string | The IP from whre the download was initiated.

## Get All Stats

```shell
curl -X GET \
  https://yorusite.com/wp-json/wpdm/v1/stats \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	"items_per_page": 10,
	"page": 2
}'
```

> The JSON response looks like the following example:

```json
[
    {
        "post_title": "Premium WordPress Theme",
        "id": "393",
        "pid": "5209",
        "uid": "1",
        "oid": "",
        "year": "2019",
        "month": "4",
        "day": "5",
        "timestamp": "1554477927",
        "ip": "127.0.0.1"
    },
    {
        "post_title": "Stock Photos",
        "id": "392",
        "pid": "5185",
        "uid": "1",
        "oid": "",
        "year": "2019",
        "month": "4",
        "day": "5",
        "timestamp": "1554476883",
        "ip": "127.0.0.1"
    },
    {
        "post_title": "Web Fonts",
        "id": "391",
        "pid": "5185",
        "uid": "1",
        "oid": "",
        "year": "2019",
        "month": "4",
        "day": "5",
        "timestamp": "1554476337",
        "ip": "127.0.0.1"
    }
]
```

This endpoint retrieves all Download Stats. Use query parameters to filter result.

### HTTP Request

`GET https://example.com/wp-json/wpdm/v1/stats`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
`items_per_page` | `10` | Number of records to retrive.
`page` | `0` | The page number.
`start_date` | empty | Filter stats by date.
`end_date` | empty | Filter stats by date.
`package_id` | empty | Filter stats by Package. Set `package_id` to get download stats of a specific package.
`user_id` | empty | Filter stats by user. Set `user_id` to get download history of a user.

## Create a Download Stat

```shell
curl -X POST \
  https://yorusite.com/wp-json/wpdm/v1/stats \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	 "post_title": "Stock Photos",
     "pid": "5209",
     "uid": "1",
     "oid": "",
     "year": "2019",
     "month": "4",
     "day": "5",
     "timestamp": "1554477927",
     "ip": "127.0.0.1"
}'
```

> The JSON response looks like the following example:

```json
{
    "post_title": "Stock Photos",
    "id": "393",
    "pid": "5209",
    "uid": "1",
    "oid": "",
    "year": "2019",
    "month": "4",
    "day": "5",
    "timestamp": "1554477927",
    "ip": "127.0.0.1"
}
```

This endpoint creates a new Download Stat and sets Download Stat properties based on POST data.

### HTTP Request

`POST https://example.com/wp-json/wpdm/v1/stats`

## Get a Download Stat

```shell
curl -X GET \
  https://yorusite.com/wp-json/wpdm/v1/stats/393 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "post_title": "Stock Photos",
    "id": "393",
    "pid": "5209",
    "uid": "1",
    "oid": "",
    "year": "2019",
    "month": "4",
    "day": "5",
    "timestamp": "1554477927",
    "ip": "127.0.0.1"
}
```

This endpoint retrieves a specific Download Stat by ID.

### HTTP Request

`GET https://example.com/wp-json/wpdm/v1/stats/<id>`

## Update a Download Stat

```shell
curl -X PUT \
  https://yorusite.com/wp-json/wpdm/v1/stats/393 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	 "post_title": "Stock Photos",
     "pid": "5209",
     "uid": "1",
     "oid": "",
     "year": "2019",
     "month": "4",
     "day": "5",
     "timestamp": "1554477927",
     "ip": "127.0.0.1"
}'
```

> The JSON response looks like the following example:

```json
{
    "post_title": "Stock Photos",
    "id": "393",
    "pid": "5209",
    "uid": "1",
    "oid": "",
    "year": "2019",
    "month": "4",
    "day": "5",
    "timestamp": "1554477927",
    "ip": "127.0.0.1"
}
```

This endpoint updates a specific Download Stat by ID.

### HTTP Request

`PUT https://example.com/wp-json/wpdm/v1/stats/<id>`

## Delete a Download Stat

```shell
curl -X DELETE \
  https://yorusite.com/wp-json/wpdm/v1/stats/393 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "post_title": "Stock Photos",
    "id": "393",
    "pid": "5209",
    "uid": "1",
    "oid": "",
    "year": "2019",
    "month": "4",
    "day": "5",
    "timestamp": "1554477927",
    "ip": "127.0.0.1"
}
```

This endpoint deletes a specific Download Stat by ID.

### HTTP Request

`DELETE https://example.com/wp-json/wpdm/v1/stats/<id>`