---
title: WordPress Download Manager REST API Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: cURL

toc_footers:
  - <a href='https://www.wpdownloadmanager.com/docsfor/download-manager-pro/'>Download Manager Documentation</a>
  - <a href='https://www.wpdownloadmanager.com/support/forum/download-manager-pro/'>Support Forum</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - packages
  - categories
  - tags
  - stats
  - subscribers
  - orders
  - coupons
  - licenses
  - errors

search: true
---

# Introduction

This website documents the [WordPress Download Manager](https://www.wpdownloadmanager.com/) REST API. This REST API allows a HTTP client to create, read, update, and delete WordPress Download Manager data using requests in JSON format. WordPress Download Manager REST API uses standard HTTP verbs which are understood by most HTTP clients. This API is built on top of WordPress REST API and lives at `/wpdm/v1` namespace.

You can view code examples in the dark area to the right; switch the programming language of the examples with the tabs in the top right.

If anything is missing or seems incorrect, please check the [GitHub issues](https://github.com/imsas/wpdm-rest-api-docs/issues) for existing known issues or [create a new issue](https://github.com/imsas/wpdm-rest-api-docs/issues/new).

# Authentication

```shell
# Here we are sending a GET request. Adjust the HTTP verb based on your request.
# Sending base64 encoded userrname:password.
curl -X GET \
  "api_endpoint_here" \
  -H 'Authorization: Basic YWRtaW46YWRtaW4='
  
# Sending API key as bearer token. We will use this Authorization in the rest of the examples.
curl -X GET \
  "api_endpoint_here" \
  -H 'Authorization: Bearer 613efe9acb0d5c2b'  
```

Authentication is done via the API key which you can find in your WPDM REST API settings. Pass the API key as a bearer token in an Authorization header.

`Authorization: Bearer {key}`

Alternatively you can also use Basic Auth over https by sending username, password.

`Authorization: Basic {base64("username:password")}`

In both Authentication procedure what you can do via API depends on the associated user capabilities. Unauthenticated requests will return an HTTP 401 response.

<aside class="notice">Use HTTPS for all requests to connect securely. Keep your API key a secret!</aside>