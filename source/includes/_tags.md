# Package Tags

The `tags` API endpoint allows you to create, view, update, and delete package tags.

## Package Tag Properties

Attribute | Type | Description
--------- | ------- | -----------
`term_id` | integer | Tag id, the unique identifier for the resource.
`name` | string | Tag name.
`slug` | string | Tag slug.
`description` | string | Tag details/description/content.
`taxonomy` | string | Taxonomy name. Readonly Attribute.
`parent` | integer | Tag parent. Always `0` (non-hierarchical taxonomy).
`count` | integer | Number of packages under this Tag.

## Get All Tags

```shell
curl -X GET \
  https://yoursite.com/wp-json/wpdm/v1/tags \
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
        "term_id": 1496,
        "name": "add-on",
        "slug": "add-on",
        "term_group": 0,
        "term_taxonomy_id": 1496,
        "taxonomy": "post_tag",
        "description": "",
        "parent": 0,
        "count": 5,
        "filter": "raw",
        "term_order": "0"
    },
    {
        "term_id": 1502,
        "name": "locked",
        "slug": "locked",
        "term_group": 0,
        "term_taxonomy_id": 1502,
        "taxonomy": "post_tag",
        "description": "",
        "parent": 0,
        "count": 2,
        "filter": "raw",
        "term_order": "0"
    }
]
```

This endpoint retrieves all tags. Use query parameters to filter results.

### HTTP Request

<span class="http-request"><span class="http-verb http-get">GET</span><span class="api-endpoint">/wp-json/wpdm/v1/tags</span></span>

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
`orderby` | `name` | Field(s) to order terms by. Accepts term fields `name`, `slug`, `term_id`.
`order` | `ASC` | Whether to order terms in ascending or descending order. Accepts `ASC` (ascending) or `DESC` (descending).
`hide_empty` | `false` | Whether to hide terms not assigned to any posts. Accepts `true` or `false`.
`number` | `0` | Maximum number of terms to return. Accepts `0` (all) or any positive number
`offset` | empty | The number by which to offset the terms query.
`include` | empty | Array or comma/space-separated string of term ids to include. Default empty array.
`exclude` | empty | Array or comma/space-separated string of term ids to exclude. If `include` is non-empty, `exclude` is ignored. Default empty array.

## Create a Tag

```shell
curl -X POST \
  https://yoursite.com/wp-json/wpdm/v1/tags \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	 "name": "add-on",
     "slug": "add-on",
     "description": ""
}'
```

> The JSON response looks like the following example:

```json
{
    "term_id": 1496,
    "name": "add-on",
    "slug": "add-on",
    "term_group": 0,
    "term_taxonomy_id": 1496,
    "taxonomy": "post_tag",
    "description": "",
    "parent": 0,
    "count": 5,
    "filter": "raw",
    "term_order": "0"
}
```

This endpoint creates a new Tag and sets Tag properties based on POST data.

### HTTP Request

<span class="http-request"><span class="http-verb http-post">POST</span><span class="api-endpoint">/wp-json/wpdm/v1/tags</span></span>

## Get a Tag

```shell
curl -X GET \
  https://yoursite.com/wp-json/wpdm/v1/tags/1496 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "term_id": 1496,
    "name": "add-on",
    "slug": "add-on",
    "term_group": 0,
    "term_taxonomy_id": 1496,
    "taxonomy": "post_tag",
    "description": "",
    "parent": 0,
    "count": 5,
    "filter": "raw",
    "term_order": "0"
}
```

This endpoint retrieves a specific Tag by ID (`term_id` ).

### HTTP Request

<span class="http-request"><span class="http-verb http-get">GET</span><span class="api-endpoint">/wp-json/wpdm/v1/tags/:id</span></span>

## Update a Tag

```shell
curl -X PUT \
  https://yoursite.com/wp-json/wpdm/v1/tags/1496 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	 "name": "add-on",
     "slug": "add-on",
     "description": ""
}'
```

> The JSON response looks like the following example:

```json
{
    "term_id": 1496,
    "name": "add-on",
    "slug": "add-on",
    "term_group": 0,
    "term_taxonomy_id": 1496,
    "taxonomy": "post_tag",
    "description": "",
    "parent": 0,
    "count": 5,
    "filter": "raw",
    "term_order": "0"
}
```

This endpoint updates a specific Tag by ID (`term_id` ).

### HTTP Request

<span class="http-request"><span class="http-verb http-put">PUT</span><span class="api-endpoint">/wp-json/wpdm/v1/tags/:id</span></span>

## Delete a Tag

```shell
curl -X DELETE \
  https://yoursite.com/wp-json/wpdm/v1/tags/1496 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
    "term_id": 1496,
    "name": "add-on",
    "slug": "add-on",
    "term_group": 0,
    "term_taxonomy_id": 1496,
    "taxonomy": "post_tag",
    "description": "",
    "parent": 0,
    "count": 5,
    "filter": "raw",
    "term_order": "0"
}
```

This endpoint deletes a specific Tag by ID (`term_id` ).

### HTTP Request

<span class="http-request"><span class="http-verb http-delete">DELETE</span><span class="api-endpoint">/wp-json/wpdm/v1/tags/:id</span></span>