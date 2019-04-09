# Package Categories

The `categories` API endpoint allows you to create, view, update, and delete package categories.

## Package Category Properties

Attribute | Type | Description
--------- | ------- | -----------
`term_id` | integer | Category id, the unique identifier for the resource.
`name` | string | Category name.
`slug` | string | Category slug.
`description` | string | Category details/description/content.
`taxonomy` | string | Taxonomy name. Readonly Attribute.
`icon` | string | Category icon URL.
`parent` | integer | Category parent. Default is `0` ( no parent ).
`count` | integer | Number of packages in this Category.
`role_access` | array | Array of user roles who has access to this category.
`user_access` | array | Array of usernames who has access to this category.

## Get All Categories

```shell
curl -X GET \
  https://yorusite.com/wp-json/wpdm/v1/categories \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	"orderby": "name",
	"number": "10"
}'
```

> The JSON response looks like the following example:

```json
[
    {
        "term_id": 16,
        "name": "Flat UI",
        "slug": "flat-ui",
        "term_group": 0,
        "term_taxonomy_id": 16,
        "taxonomy": "wpdmcategory",
        "description": "Best UI resources for free.",
        "parent": 0,
        "count": 9,
        "filter": "raw",
        "term_order": "4",
        "icon": "http://example.com/wp-content/uploads/2019/02/flat-ui.jpg",
        "role_access": [
            "subscriber",
            "contributor",
            "administrator"
        ],
        "user_access": [
            "admin"
        ]
    },
    {
        "term_id": 11,
        "name": "Free PSD",
        "slug": "free-psd",
        "term_group": 0,
        "term_taxonomy_id": 11,
        "taxonomy": "wpdmcategory",
        "description": "Unlimited PSD files.",
        "parent": 0,
        "count": 3,
        "filter": "raw",
        "term_order": "5",
        "icon": "http://example.com/wp-content/uploads/2019/02/free-psd.jpg",
        "role_access": [
             "contributor",
             "administrator"
        ],
        "user_access": ""
    }
]
```

This endpoint retrieves all Categories. Use query parameters to filter result.

### HTTP Request

`GET https://example.com/wp-json/wpdm/v1/categories`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
`orderby` | `name` | Field(s) to order terms by. Accepts term fields `name`, `slug`, `term_id`.
`order` | `ASC` | Whether to order terms in ascending or descending order. Accepts `ASC` (ascending) or `DESC` (descending).
`hide_empty` | `false` | Whether to hide terms not assigned to any posts. Accepts `true` or `false`.
`number` | `0` | Maximum number of terms to return. Accepts `0` (all) or any positive number
`offset` | empty | The number by which to offset the terms query.
`parent` | `0` | Parent term ID to retrieve direct-child terms of.
`include` | empty | Array or comma/space-separated string of term ids to include. Default empty array.
`exclude` | empty | Array or comma/space-separated string of term ids to exclude. If `include` is non-empty, `exclude` is ignored. Default empty array.

## Create a Category

```shell
curl -X POST \
  https://yorusite.com/wp-json/wpdm/v1/categories \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	 "name": "Flat UI",
     "slug": "flat-ui",
     "description": "Best UI resources for free.",
     "parent": 0,
     "icon": "http://example.com/wp-content/uploads/2019/02/flat-ui.jpg",
     "role_access": [
         "subscriber",
         "contributor",
         "administrator"
     ],
     "user_access": [
         "admin"
     ]
}'
```

> The JSON response looks like the following example:

```json
{
    "term_id": 16,
    "name": "Flat UI",
    "slug": "flat-ui",
    "term_group": 0,
    "term_taxonomy_id": 16,
    "taxonomy": "wpdmcategory",
    "description": "Best UI resources for free.",
    "parent": 0,
    "count": 9,
    "filter": "raw",
    "term_order": "4",
    "icon": "http://example.com/wp-content/uploads/2019/02/flat-ui.jpg",
    "role_access": [
        "subscriber",
        "contributor",
        "administrator"
    ],
    "user_access": [
        "admin"
    ]
}
```

This endpoint creates a new Category and sets Category properties based on POST data.

### HTTP Request

`POST https://example.com/wp-json/wpdm/v1/categories`

## Get a Category

```shell
curl -X GET \
  https://yorusite.com/wp-json/wpdm/v1/categories/16 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "term_id": 16,
    "name": "Flat UI",
    "slug": "flat-ui",
    "term_group": 0,
    "term_taxonomy_id": 16,
    "taxonomy": "wpdmcategory",
    "description": "Best UI resources for free.",
    "parent": 0,
    "count": 9,
    "filter": "raw",
    "term_order": "4",
    "icon": "http://example.com/wp-content/uploads/2019/02/flat-ui.jpg",
    "role_access": [
        "subscriber",
        "contributor",
        "administrator"
    ],
    "user_access": [
        "admin"
    ]
}
```

This endpoint retrieves a specific Category by ID (`term_id` ).

### HTTP Request

`GET https://example.com/wp-json/wpdm/v1/categories/<id>`

## Update a Category

```shell
curl -X PUT \
  https://yorusite.com/wp-json/wpdm/v1/categories/16 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	 "name": "Flat UI",
     "slug": "flat-ui",
     "description": "Best UI resources for free.",
     "parent": 0,
     "icon": "http://example.com/wp-content/uploads/2019/02/flat-ui.jpg",
     "role_access": [
         "subscriber",
         "contributor",
         "administrator"
     ],
     "user_access": [
         "admin"
     ]
}'
```

> The JSON response looks like the following example:

```json
{
    "term_id": 16,
    "name": "Flat UI",
    "slug": "flat-ui",
    "term_group": 0,
    "term_taxonomy_id": 16,
    "taxonomy": "wpdmcategory",
    "description": "Best UI resources for free.",
    "parent": 0,
    "count": 9,
    "filter": "raw",
    "term_order": "4",
    "icon": "http://example.com/wp-content/uploads/2019/02/flat-ui.jpg",
    "role_access": [
        "subscriber",
        "contributor",
        "administrator"
    ],
    "user_access": [
        "admin"
    ]
}
```

This endpoint updates a specific Category by ID (`term_id` ).

### HTTP Request

`PUT https://example.com/wp-json/wpdm/v1/categories/<id>`

## Delete a Category

```shell
curl -X DELETE \
  https://yorusite.com/wp-json/wpdm/v1/categories/16 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "term_id": 16,
    "name": "Flat UI",
    "slug": "flat-ui",
    "term_group": 0,
    "term_taxonomy_id": 16,
    "taxonomy": "wpdmcategory",
    "description": "Best UI resources for free.",
    "parent": 0,
    "count": 9,
    "filter": "raw",
    "term_order": "4",
    "icon": "http://example.com/wp-content/uploads/2019/02/flat-ui.jpg",
    "role_access": [
        "subscriber",
        "contributor",
        "administrator"
    ],
    "user_access": [
        "admin"
    ]
}
```

This endpoint deletes a specific Category by ID (`term_id` ).

### HTTP Request

`DELETE https://example.com/wp-json/wpdm/v1/categories/<id>`