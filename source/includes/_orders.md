# Orders

The `orders` API endpoint allows you to create, view, update, and delete Premium Package Orders.

## Order Properties

Attribute | Type | Description
--------- | ------- | -----------
`order_id` | string | Order id, the unique identifier for the resource.
`trans_id` | string | Transaction id, unique identifier for this order in Payment platform.
`title` | string | Order title
`date` | date | The date the order was created.
`items` | array | Array of package IDs that are included in this order.  
`cart_data` | object | Detailed information about cart/order items. Check the response JSON to get a clear idea how data are fomatted in this attribute.
`total` | string | Grand total of the order. The amount paid by the customer.
`order_status` | string | Order status. Options are `Pending`, `Processing`, `Completed`, `Expired`, `Cancelled`
`payment_status` | string | Payment status. Options are `Pending`, `Processing`, `Completed`, `Expired`, `Cancelled`, `Gifted`, `Disputed`, `Refunded`
`uid` | string | User id of the customer associated with this order.
`order_notes` | object | All notes added to this order.
`payment_method` | string | The payment method used to place this order.
`tax` | string | Total tax for this order.
`cart_discount` | string | Total cart discount.
`coupon_discount` | string | Total coupon discount.
`currency` | object | The object contains the currency `sign` and `code`
`IP` | string | The IP address from where the order was placed.
`billing_info` | object | The object contains the Billing details of the customer.
`expire_date` | date | The date when the order will be expired.
`auto_renew` | int | Order auto renew status. Default `0`
`coupon_code` | string | The coupon code applied to theis order.
`subtotal` | string | The subtotal of the order before applying discounts.

## Get All Orders

```shell
curl -X GET \
  https://yorusite.com/wp-json/wpdm/v1/orders \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	"items_per_page": 10,
	"payment_status": "Completed"
}'
```

> The JSON response looks like the following example:

```json
[
    {
        "order_id": "5c9f89523c467",
        "trans_id": "250140068332",
        "title": "WPDM Order# 5c9f89523c467",
        "date": "March 30, 2019",
        "items": [
            3901,
            5649
        ],
        "cart_data": {
            "3901": {
                "quantity": "1",
                "variation": [],
                "price": "10.00",
                "files": [],
                "license": {
                    "id": "statdard",
                    "info": {
                        "name": "Standard",
                        "description": "",
                        "use": "1"
                    }
                },
                "ID": 3901,
                "post_title": "Premium Package ( WPPM Free Trial Item )",
                "prices": 0,
                "variations": [],
                "discount_amount": 0
            },
            "5649": {
                "quantity": "1",
                "variation": [],
                "price": "12.00",
                "files": [],
                "license": {
                    "id": "",
                    "info": ""
                },
                "ID": 5649,
                "post_title": "Einstein, Quote",
                "prices": 0,
                "variations": [],
                "discount_amount": 0
            }
        },
        "total": "11",
        "order_status": "Completed",
        "payment_status": "Completed",
        "uid": "1",
        "order_notes": {
            "messages": {
                "1": {
                    "note": "Send me the documentation link.",
                    "by": "Customer"
                },
                "2": {
                    "note": "Here is the doc https://www.wpdownloadmanager.com/docsfor/download-manager-pro/",
                    "by": "Customer"
                }
            }
        },
        "payment_method": "TestPay",
        "tax": "0",
        "cart_discount": "0",
        "discount": "0",
        "coupon_discount": "11",
        "currency": {
            "sign": "$",
            "code": "USD"
        },
        "download": "1",
        "IP": "::1",
        "ipn": "",
        "unit_prices": "",
        "billing_info": {
            "first_name": "Shahriar",
            "last_name": "Alam",
            "company": "W3 Eden",
            "country": "BD",
            "state": "A",
            "address_1": "Chittagong",
            "address_2": "Chnadgaon",
            "city": "Chittagong",
            "postcode": "4212",
            "phone": "+0101725111222",
            "order_email": "shahriar@wpdm.com"
        },
        "expire_date": "March 29, 2020",
        "auto_renew": "0",
        "coupon_code": "50off",
        "subtotal": "22"
    },
    {
        "order_id": "5c9fc5bada534",
        "trans_id": "250140068399",
        "title": "Hello There",
        "date": "March 30, 2019",
        "items": [
            3901,
            5649
        ],
        "cart_data": {
            "3901": {
                "quantity": "1",
                "variation": [],
                "price": "10.00",
                "files": [],
                "license": {
                    "id": "statdard",
                    "info": {
                        "name": "Standard",
                        "description": "",
                        "use": "1"
                    }
                },
                "ID": 3901,
                "post_title": "Premium Package ( WPPM Free Trial Item )",
                "prices": 0,
                "variations": [],
                "discount_amount": 0
            },
            "5649": {
                "quantity": "1",
                "variation": [],
                "price": "12.00",
                "files": [],
                "license": {
                    "id": "",
                    "info": ""
                },
                "ID": 5649,
                "post_title": "WPDM Pro",
                "prices": 0,
                "variations": [],
                "discount_amount": 0
            }
        },
        "total": "11",
        "order_status": "Completed",
        "payment_status": "Completed",
        "uid": "1",
        "order_notes": {
            "messages": {
                "1": {
                    "note": "Where can I download the invoice?",
                    "by": "Customer"
                }
            }
        },
        "payment_method": "TestPay",
        "tax": "0",
        "cart_discount": "0",
        "discount": "0",
        "coupon_discount": "11",
        "currency": {
            "sign": "$",
            "code": "USD"
        },
        "download": "1",
        "IP": "::1",
        "ipn": "",
        "unit_prices": "",
        "billing_info": {
            "first_name": "Shahriar",
            "last_name": "Alam",
            "company": "W3 Eden",
            "country": "BD",
            "state": "A",
            "address_1": "Chittagong",
            "address_2": "Chnadgaon",
            "city": "Chittagong",
            "postcode": "4212",
            "phone": "+0101725111222",
            "order_email": "shahriar@wpdm.com"
        },
        "expire_date": "March 29, 2020",
        "auto_renew": "0",
        "coupon_code": "50off",
        "subtotal": "22"
    }
]
```

This endpoint retrieves all Orders. Use query parameters to limit the response.

### HTTP Request

`GET https://example.com/wp-json/wpdm/v1/orders`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
`items_per_page` | `10` | Number of orders to retrive.
`page` | `0` | The page number.
`start_date` | empty | Limit response to orders created after a given date-time. Example, `2019-01-31 12:00 am`
`end_date` | empty | Limit response to orders created before a given date-time. Example, `2019-03-22 12:00 am`
`order_status` | empty | Limit response to orders by a provided status. Options are `Pending`, `Processing`, `Completed`, `Expired`, `Cancelled`
`payment_status` | empty | Filter orders by payment status. Options are `Pending`, `Processing`, `Completed`, `Expired`, `Cancelled`, `Gifted`, `Disputed`, `Refunded`
`payment_method` | empty | Filter orders by payment method.
`uid` | empty | Get all orders owned by a specific user.

## Create a Order

```shell
curl -X POST \
  https://yorusite.com/wp-json/wpdm/v1/orders \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
     "date": "April 7, 2019",
     "items": [
         3901
     ],
     "cart_data": {
        "3901": {
            "quantity": 1,
            "variation": [],
            "price": "10.00",
            "files": [],
            "license": {
                "id": "",
                "info": ""
            },
            "ID": 3901,
            "post_title": "Premium Package ( WPPM Free Trial Item )",
            "prices": 0,
            "variations": [],
            "discount_amount": 0
        }
     },
     "total": "10",
     "order_status": "Completed",
     "payment_status": "Completed",
     "uid": "1",
     "order_notes": "",
     "payment_method": "TestPay",
     "tax": "0",
     "cart_discount": "0",
     "discount": "0",
     "coupon_discount": "0",
     "currency": {
        "sign": "$",
        "code": "USD"
     },
     "download": "0",
     "IP": "::1",
     "ipn": "",
     "unit_prices": "",
     "billing_info": {
        "first_name": "Shahriar",
        "last_name": "Alam",
        "company": "W3 Eden",
        "country": "BD",
        "state": "A",
        "address_1": "Chittagong",
        "address_2": "Chnadgaon",
        "city": "Chittagong",
        "postcode": "4212",
        "phone": "+8801720000000",
        "order_email": "shahriar@wpdm.com"
     },
     "expire_date": "April 6, 2020",
     "auto_renew": "0",
     "coupon_code": "",
     "subtotal": "10"
}'
```

> The JSON response looks like the following example:

```json
{
    "order_id": "5caa1c94aaf0f",
    "trans_id": "",
    "title": "WPDM Order# 5caa1c94aaf0f",
    "date": "April 7, 2019",
    "items": [
        3901
    ],
    "cart_data": {
        "3901": {
            "quantity": 1,
            "variation": [],
            "price": "10.00",
            "files": [],
            "license": {
                "id": "",
                "info": ""
            },
            "ID": 3901,
            "post_title": "Premium Package ( WPPM Free Trial Item )",
            "prices": 0,
            "variations": [],
            "discount_amount": 0
        }
    },
    "total": "10",
    "order_status": "Completed",
    "payment_status": "Completed",
    "uid": "1",
    "order_notes": "",
    "payment_method": "TestPay",
    "tax": "0",
    "cart_discount": "0",
    "discount": "0",
    "coupon_discount": "0",
    "currency": {
        "sign": "$",
        "code": "USD"
    },
    "download": "0",
    "IP": "::1",
    "ipn": "",
    "unit_prices": "",
    "billing_info": {
        "first_name": "Shahriar",
        "last_name": "Alam",
        "company": "W3 Eden",
        "country": "BD",
        "state": "A",
        "address_1": "Chittagong",
        "address_2": "Chnadgaon",
        "city": "Chittagong",
        "postcode": "4212",
        "phone": "+8801720000000",
        "order_email": "shahriar@wpdm.com"
    },
    "expire_date": "April 6, 2020",
    "auto_renew": "0",
    "coupon_code": "",
    "subtotal": "10"
}
```

This endpoint creates a new Order and sets Order properties based on POST data.

### HTTP Request

`POST https://example.com/wp-json/wpdm/v1/orders`

## Get an Order

```shell
curl -X GET \
  https://yorusite.com/wp-json/wpdm/v1/orders/5caa1c94aaf0f \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "order_id": "5caa1c94aaf0f",
    "trans_id": "",
    "title": "WPDM Order# 5caa1c94aaf0f",
    "date": "April 7, 2019",
    "items": [
        3901
    ],
    "cart_data": {
        "3901": {
            "quantity": 1,
            "variation": [],
            "price": "10.00",
            "files": [],
            "license": {
                "id": "",
                "info": ""
            },
            "ID": 3901,
            "post_title": "Premium Package ( WPPM Free Trial Item )",
            "prices": 0,
            "variations": [],
            "discount_amount": 0
        }
    },
    "total": "10",
    "order_status": "Completed",
    "payment_status": "Completed",
    "uid": "1",
    "order_notes": "",
    "payment_method": "TestPay",
    "tax": "0",
    "cart_discount": "0",
    "discount": "0",
    "coupon_discount": "0",
    "currency": {
        "sign": "$",
        "code": "USD"
    },
    "download": "0",
    "IP": "::1",
    "ipn": "",
    "unit_prices": "",
    "billing_info": {
        "first_name": "Shahriar",
        "last_name": "Alam",
        "company": "W3 Eden",
        "country": "BD",
        "state": "A",
        "address_1": "Chittagong",
        "address_2": "Chnadgaon",
        "city": "Chittagong",
        "postcode": "4212",
        "phone": "+8801720000000",
        "order_email": "shahriar@wpdm.com"
    },
    "expire_date": "April 6, 2020",
    "auto_renew": "0",
    "coupon_code": "",
    "subtotal": "10"
}
```

This endpoint retrieves a specific Order by ID.

### HTTP Request

`GET https://example.com/wp-json/wpdm/v1/orders/<id>`

## Update an Order

```shell
curl -X PUT \
  https://yorusite.com/wp-json/wpdm/v1/orders/5caa1c94aaf0f \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	 "order_status": "Completed",
     "payment_status": "Completed"
}'
```

> The JSON response looks like the following example:

```json
{
    "order_id": "5caa1c94aaf0f",
    "trans_id": "",
    "title": "WPDM Order# 5caa1c94aaf0f",
    "date": "April 7, 2019",
    "items": [
        3901
    ],
    "cart_data": {
        "3901": {
            "quantity": 1,
            "variation": [],
            "price": "10.00",
            "files": [],
            "license": {
                "id": "",
                "info": ""
            },
            "ID": 3901,
            "post_title": "Premium Package ( WPPM Free Trial Item )",
            "prices": 0,
            "variations": [],
            "discount_amount": 0
        }
    },
    "total": "10",
    "order_status": "Completed",
    "payment_status": "Completed",
    "uid": "1",
    "order_notes": "",
    "payment_method": "TestPay",
    "tax": "0",
    "cart_discount": "0",
    "discount": "0",
    "coupon_discount": "0",
    "currency": {
        "sign": "$",
        "code": "USD"
    },
    "download": "0",
    "IP": "::1",
    "ipn": "",
    "unit_prices": "",
    "billing_info": {
        "first_name": "Shahriar",
        "last_name": "Alam",
        "company": "W3 Eden",
        "country": "BD",
        "state": "A",
        "address_1": "Chittagong",
        "address_2": "Chnadgaon",
        "city": "Chittagong",
        "postcode": "4212",
        "phone": "+8801720000000",
        "order_email": "shahriar@wpdm.com"
    },
    "expire_date": "April 6, 2020",
    "auto_renew": "0",
    "coupon_code": "",
    "subtotal": "10"
}
```

This endpoint updates a specific Order by ID.

### HTTP Request

`PUT https://example.com/wp-json/wpdm/v1/orders/<id>`

## Delete an Order

```shell
curl -X DELETE \
  https://yorusite.com/wp-json/wpdm/v1/orders/5c9f89523c467 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "order_id": "5c9f89523c467",
    "trans_id": "",
    "title": "WPDM Order# 5c9f89523c467",
    "date": "March 30, 2019",
    "items": [
        3901,
        5649
    ],
    "cart_data": {
        "3901": {
            "quantity": "1",
            "variation": [],
            "price": "59.00",
            "files": [],
            "license": {
                "id": "statdard",
                "info": {
                    "name": "Standard",
                    "description": "",
                    "use": "1"
                }
            },
            "ID": 3901,
            "post_title": "WordPress Download Manager Pro",
            "prices": 0,
            "variations": [],
            "discount_amount": 0
        },
        "5649": {
            "quantity": "1",
            "variation": [],
            "price": "49.00",
            "files": [],
            "license": {
                "id": "",
                "info": ""
            },
            "ID": 5649,
            "post_title": "WPDM MailChimp",
            "prices": 0,
            "variations": [],
            "discount_amount": 0
        }
    },
    "total": "54",
    "order_status": "Completed",
    "payment_status": "Completed",
    "uid": "1",
    "order_notes": {
        "messages": {
            "1": {
                "note": "Please send me the documentation link.",
                "by": "Customer"
            },
            "2": {
                "note": "Here is the doc https://www.wpdownloadmanager.com/docsfor/download-manager-pro/",
                "by": "Admin"
            }
        }
    },
    "payment_method": "TestPay",
    "tax": "0",
    "cart_discount": "0",
    "discount": "0",
    "coupon_discount": "54",
    "currency": {
        "sign": "$",
        "code": "USD"
    },
    "download": "1",
    "IP": "127.0.0.1",
    "ipn": "",
    "unit_prices": "",
    "billing_info": {
        "first_name": "Shahriar",
        "last_name": "Alam",
        "company": "W3 Eden",
        "country": "BD",
        "state": "A",
        "address_1": "Chittagong",
        "address_2": "Chnadgaon",
        "city": "Chittagong",
        "postcode": "4212",
        "phone": "+8801711111111",
        "order_email": "shahriar@wpdm.com"
    },
    "expire_date": "March 29, 2020",
    "auto_renew": "0",
    "coupon_code": "50off",
    "subtotal": "108"
}
```

This endpoint deletes a specific Order by ID.

### HTTP Request

`DELETE https://example.com/wp-json/wpdm/v1/orders/<id>`