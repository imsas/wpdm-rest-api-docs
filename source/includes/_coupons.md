# Coupons

The `coupons` API endpoint allows you to create, view, update, and delete coupons.

## Coupon Properties

Attribute | Type | Description
--------- | ------- | -----------
`ID` | integer | Coupon id, the unique identifier for the resource.
`code` | string | The coupon code.
`description` | string | The coupon description.
`type` | string | Coupon type. Options are `percent` and `fixed`
`discount` | string | The discount amount.
`min_order_amount` | string | The required min order amount for this coupon.
`max_order_amount` | string | The limit of maximun order total for this coupon.
`product` | string | Associated product id. If set to `0` the coupon is global, applicable to any product.
`allowed_emails` | string | Limit the coupon only to specified email addresses.
`expire_date` | date | Coupon expiration date. After this date the coupon will be invalid.
`usage_limit` | integer | Maximum usage of the copuon.
`used` | integer | The number of times this coupon has been used.

## Get All Coupons

```shell
curl -X GET \
  https://yorusite.com/wp-json/wpdm/v1/coupons \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	"items_per_page": 10,
	"type": "percent"
}'
```

> The JSON response looks like the following example:

```json
[
    {
        "ID": "9",
        "code": "wc2019",
        "description": "Happy New Year!",
        "type": "percent",
        "discount": "19",
        "min_order_amount": "10",
        "max_order_amount": "0",
        "product": "0",
        "allowed_emails": "",
        "expire_date": "May 12, 2019",
        "usage_limit": "50",
        "used": "5"
    },
    {
        "ID": "6",
        "code": "50off",
        "description": "USD $50 discount!",
        "type": "fixed",
        "discount": "50",
        "min_order_amount": "0",
        "max_order_amount": "0",
        "product": "0",
        "allowed_emails": "",
        "expire_date": "December 12, 2019",
        "usage_limit": "0",
        "used": "7"
    }
]
```

This endpoint retrieves all Coupons. Use query parameters to filter result.

### HTTP Request

<span class="http-request"><span class="http-verb http-get">GET</span><span class="api-endpoint">/wp-json/wpdm/v1/coupons</span></span>

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
`items_per_page` | `10` | Number of coupons to retrive.
`page` | `0` | The page number.
`product` | empty | Filter coupons of a specific product.
`type` | empty | Filter coupons by copuon type. Options are `percent` and `fixed`

## Create a Coupon

```shell
curl -X POST \
  https://yorusite.com/wp-json/wpdm/v1/coupons \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
     "code": "wc2019",
     "description": "Happy New Year 2019! Grab the offer!",
     "type": "percent",
     "discount": "19",
     "min_order_amount": "10",
     "max_order_amount": "0",
     "product": "0",
     "allowed_emails": "lazy@one.com",
     "expire_date": "October 12, 2019",
     "usage_limit": "5",
     "used": "0"
}'
```

> The JSON response looks like the following example:

```json
{
    "ID": "5",
    "code": "wc2019",
    "description": "Happy New Year 2019! Grab the offer!",
    "type": "percent",
    "discount": "19",
    "min_order_amount": "10",
    "max_order_amount": "0",
    "product": "0",
    "allowed_emails": "lazy@one.com",
    "expire_date": "October 12, 2019",
    "usage_limit": "5",
    "used": "0"
}
```

This endpoint creates a new Coupon and sets Coupon properties based on POST data.

### HTTP Request

<span class="http-request"><span class="http-verb http-post">POST</span><span class="api-endpoint">/wp-json/wpdm/v1/coupons</span></span>

## Get a Coupon

```shell
curl -X GET \
  https://yorusite.com/wp-json/wpdm/v1/coupons/5 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "ID": "5",
    "code": "wc2019",
    "description": "Happy New Year 2019! Grab the offer!",
    "type": "percent",
    "discount": "19",
    "min_order_amount": "10",
    "max_order_amount": "0",
    "product": "0",
    "allowed_emails": "lazy@one.com",
    "expire_date": "October 12, 2019",
    "usage_limit": "5",
    "used": "0"
}
```

This endpoint retrieves a specific Coupon by ID.

### HTTP Request

<span class="http-request"><span class="http-verb http-get">GET</span><span class="api-endpoint">/wp-json/wpdm/v1/coupons/:id</span></span>

## Update a Coupon

```shell
curl -X PUT \
  https://yorusite.com/wp-json/wpdm/v1/coupons/5 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
     "code": "wc2019",
     "description": "Happy New Year 2019! Grab the offer!",
     "type": "percent",
     "discount": "19",
     "min_order_amount": "10",
     "max_order_amount": "0",
     "product": "0",
     "allowed_emails": "lazy@one.com",
     "expire_date": "October 12, 2019",
     "usage_limit": "5",
     "used": "0"
}'
```

> The JSON response looks like the following example:

```json
{
    "ID": "5",
    "code": "wc2019",
    "description": "Happy New Year 2019! Grab the offer!",
    "type": "percent",
    "discount": "19",
    "min_order_amount": "10",
    "max_order_amount": "0",
    "product": "0",
    "allowed_emails": "lazy@one.com",
    "expire_date": "October 12, 2019",
    "usage_limit": "5",
    "used": "0"
}
```

This endpoint updates a specific Coupon by ID.

### HTTP Request

<span class="http-request"><span class="http-verb http-put">PUT</span><span class="api-endpoint">/wp-json/wpdm/v1/coupons/:id</span></span>

## Delete a Coupon

```shell
curl -X DELETE \
  https://yorusite.com/wp-json/wpdm/v1/coupons/5 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "ID": "5",
    "code": "wc2019",
    "description": "Happy New Year 2019! Grab the offer!",
    "type": "percent",
    "discount": "19",
    "min_order_amount": "10",
    "max_order_amount": "0",
    "product": "0",
    "allowed_emails": "lazy@one.com",
    "expire_date": "October 12, 2019",
    "usage_limit": "5",
    "used": "0"
}
```

This endpoint deletes a specific Coupon by ID.

### HTTP Request

<span class="http-request"><span class="http-verb http-delete">DELETE</span><span class="api-endpoint">/wp-json/wpdm/v1/coupons/:id</span></span>