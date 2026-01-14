# Packages

The `packages` API endpoint allows you to create, view, update, and delete packages.

## Package Properties

Attribute | Type | Description
--------- | ------- | -----------
`id` | integer | Package id, the unique identifier for the resource.
`title` | string | Package title.
`slug` | string | Package slug.
`description` | string | Package details/description/content.
`excerpt` | string | Package excerpt.
`author` | integer | Package author id (WordPress user id).
`status` | string | Package status (post status). Options: `draft`, `pending`, `private` and `publish`. Defaults to `publish`.
`parent` | string | Package parent. Defaults to `0` (no parent).
`tags` | array | Array of tag terms.
`categories` | array | Array of category ids (custom taxonomy term ids for `wpdmcategory`).
`thumbnail` | string | Featured image URL.
`additional_previews` | array | Array of additional preview image URLs.
`version` | string | Package version.
`link_label` | string | Package link label. It is the download button text.
`quota` | integer | Package quota. Defaults to `0` (unlimited).
`download_limit_per_user` | integer | Package download limit per user.
`view_count` | integer | Total views of the package.
`download_count` | integer | Total downloads of the package.
`package_size` | string | Total size of attached files.
`access` | array | Array of user roles who are allowed to access the package.
`user_access` | array | Array of usernames who are allowed to access the package (related to Advanced Access Control add-on).
`individual_file_download` | string | Single file download status. Options: `-1` (Global), `1` (Enable), `0` (Disable).
`cache_zip` | string | Cache Zip File status. Options: `-1` (Global), `1` (Enable), `0` (Disable).
`template` | string | Link template for the package.
`page_template` | string | Page template for the package.
`files` | object | Array of attached file names key by file ids.
`fileinfo` | array | Array of attached file info key by the file ids.
`package_dir` | string | The attached directory.
`publish_date` | date-time | Download Available From date.
`expire_date` | date-time | Download Expire on date.
`terms_lock` | string | Term lock status. Use value `1` to activate lock.
`terms_title` | string | Term lock title.
`terms_conditions` | string | Term lock terms and agreements text.
`terms_check_label` | string | Term lock agree button text.
`password_lock` | string | Password lock status. Use value `1` to activate lock.
`password` | string | Package passwords. If you are using multiple passwords then separate each password by []. `[password1][password2]`
`password_usage_limit` | string | Usage limit of each package password.
`linkedin_lock` | string | Linkedin lock status. Use value `1` to activate lock.
`linkedin_message` | string | Linkedin lock message.
`linkedin_url` | string | Linkedin URL.
`tweet_lock` | string | Tweet lock status. Use value `1` to activate lock.
`tweet_message` | string | Tweet lock message.
`twitterfollow_lock` | string | Twitter follow lock status. Use value `1` to activate lock.
`twitter_handle` | string | The Twitter handle to follow.
`facebooklike_lock` | string | Facebook like lock status. Use value `1` to activate lock.
`facebook_like` | string | Facebook URL to lock.
`email_lock` | string | Email lock status. Use value `1` to activate lock.
`email_lock_title` | string | Email lock title.
`email_lock_msg` | string | Email lock message.
`email_lock_idl` | string | Email lock download option. Options: `0` (Mail Download Link), `1` (Download Instantly), `2` (Wait For Approval).
`icon` | string | Package icon URL.
`base_price` | integer | Package base price.
`sales_price` | integer | Package sales price.
`sales_price_expire` | date-time | Package sales price expire date. Format `2019-08-31 12:00 am`
`pay_as_you_want` | string | Enable/disable pay as you want feature. Set `1` to enable.
`license` | array | Array of license with price and status info.
`discount` | array | Array of role based discount data.
`enable_license` | string | Enable license for the package using value `1`
`enable_license_key` | string | License Key Required if value is set to `1`
`free_downloads` | array | Array of files available for free download in a premium package.
`meta_input` | array | Array of custom meta values keyed to their keys.

## Get All Packages

```shell
curl -X GET \
  https://yoursite.com/wp-json/wpdm/v1/packages \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	"number_of_posts": 5,
	"tag": "add-on,free"
}'
```

> The JSON response looks like the following example:

```json
[
  {
      "id": 241,
      "title": "The Quotable Einstein",
      "slug": "the-quotable-einstein",
      "description": "No problem can be solved from the same level of consciousness that created it.",
      "excerpt": "An A to Z Glossary of Quotations",
      "author": 1,
      "status": "publish",
      "parent": 0,
      "tags": [
          "books",
          "einstein"
      ],
      "categories": [
          16
      ],
      "thumbnail": "https://example.com/wp-content/uploads/2016/01/the-quotable-einstein.jpg",
      "additional_previews": [
          "https://example.com/wp-content/uploads/2019/04/the-quotable-einstein-front.jpg",
          "https://example.com/wp-content/uploads/2019/04/the-quotable-einstein-back.jpg"
      ],
      "version": "1.0.0",
      "link_label": "Download",
      "quota": 0,
      "download_limit_per_user": 100,
      "view_count": 80,
      "download_count": 14,
      "package_size": "811.84 KB",
      "access": [
          "subscriber",
          "administrator"
      ],
      "user_access": [
          "admin"
      ],
      "individual_file_download": "1",
      "cache_zip": "-1",
      "template": "link-template-calltoaction1",
      "page_template": "page-template-1col-flat",
      "files": {
          "1": "The Quotable Einstein.pdf"
      },
      "fileinfo": {
          "1": {
              "title": "The Quotable Einstein",
              "password": "",
              "license_price": {
                  "standard": "",
                  "extended": "",
                  "unlimited": ""
              },
              "price": ""
          }
      },
      "package_dir": "",
      "publish_date": "2019-04-01 12:00 am",
      "expire_date": "2019-08-31 12:00 am",
      "terms_lock": "1",
      "terms_title": "Agree to terms",
      "terms_conditions": "You can't redistribute without prior authorization.",
      "terms_check_label": "I Agree",
      "password_lock": "1",
      "password": "[123][456]",
      "password_usage_limit": "2",
      "linkedin_lock": "1",
      "linkedin_message": "LinkedIn Share Lock message",
      "linkedin_url": "https://www.wpdownloadmanager.com/",
      "tweet_lock": "1",
      "tweet_message": "Custom tweet message",
      "twitterfollow_lock": "1",
      "twitter_handle": "AHMShahriarAlam",
      "facebooklike_lock": "1",
      "facebook_like": "",
      "email_lock": "1",
      "email_lock_title": "Subscribe To Download",
      "email_lock_msg": "",
      "email_lock_idl": "0",
      "icon": "https://example.com/wp-content/plugins/download-manager/assets/file-type-icons/arrow.png",
      
      "base_price": "12.00",
      "sales_price": "10.00",
      "sales_price_expire": "2019-08-31 12:00 am",
      "pay_as_you_want": "0",
      "license": {
          "standard": {
              "active": "1"
          },
          "extended": {
              "price": "22",
              "active": "1"
          },
          "unlimited": {
              "price": "32",
              "active": "1"
          }
      },
      "discount": {
          "subscriber": "10",
          "contributor": "20",
          "author": "30",
          "editor": "40",
          "administrator": "50"
      },
      "enable_license": "1",
      "enable_license_key": "1",
      "free_downloads": [
              "/Applications/XAMPP/xamppfiles/htdocs/wpdm/wp-content/uploads/2019/04/sample.pdf"
          ],
      "meta_input":{
      	"custom_meta" : "Hello There"
      }    
  },
  {
      "title": "The Alchemist",
      "slug": "the-alchemist",
      "description": "The Alchemist follows the journey of an Andalusian shepherd boy named Santiago.",
      "excerpt": "The Alchemist is a novel by Brazilian author Paulo Coelho.",
      "author": 1,
      "status": "publish",
      "parent": 0,
      "tags": [
          "novel",
          "paulo-coelho"
      ],
      "categories": [
          16
      ],
      "thumbnail": "https://example.com/wp-content/uploads/2019/01/the-alchemist.jpg",
      "additional_previews": [
          "https://example.com/wp-content/uploads/2019/03/the-alchemist-cover.jpg",
          "https://example.com/wp-content/uploads/2019/03/the-alchemist-map.jpg"
      ],
      "version": "3.0.0",
      "link_label": "Download",
      "quota": 0,
      "download_limit_per_user": "100",
      "view_count": 80,
      "download_count": 14,
      "package_size": "811.84 KB",
      "access": [
          "guest",
          "subscriber",
          "administrator"
      ],
      "user_access": [
          "admin"
      ],
      "individual_file_download": "1",
      "cache_zip": "-1",
      "template": "link-template-calltoaction1",
      "page_template": "page-template-1col-flat",
      "files": {
          "1": "The Alchemist.pdf"
      },
      "fileinfo": {
          "1": {
              "title": "The Alchemist",
              "password": "",
              "license_price": {
                  "standard": "",
                  "extended": "",
                  "unlimited": ""
              },
              "price": ""
          }
      },
      "package_dir": "",
      "publish_date": "2019-04-01 12:00 am",
      "expire_date": "2019-08-31 12:00 am",
      "terms_lock": "1",
      "terms_title": "Agree to terms",
      "terms_conditions": "You can't redistribute without prior authorization.",
      "terms_check_label": "Checkbox Label",
      "password_lock": "1",
      "password": "[123][456]",
      "password_usage_limit": "2",
      "linkedin_lock": "1",
      "linkedin_message": "LinkedIn Share Lock message",
      "linkedin_url": "https://www.wpdownloadmanager.com/",
      "tweet_lock": "1",
      "tweet_message": "Custom tweet message",
      "twitterfollow_lock": "1",
      "twitter_handle": "Shahriar",
      "facebooklike_lock": "1",
      "facebook_like": "",
      "email_lock": "1",
      "email_lock_title": "Subscribe To Download",
      "email_lock_msg": "",
      "email_lock_idl": "0",
      "icon": "https://example.com/wp-content/plugins/download-manager/assets/file-type-icons/arrow.png",
      
      "base_price": "12.00",
      "sales_price": "10.00",
      "sales_price_expire": "2019-08-31 12:00 am",
      "pay_as_you_want": "0",
      "license": {
          "standard": {
              "active": "1"
          },
          "extended": {
              "price": "22",
              "active": "1"
          },
          "unlimited": {
              "price": "32",
              "active": "1"
          }
      },
      "discount": {
          "subscriber": "10",
          "contributor": "20",
          "author": "30",
          "editor": "40",
          "administrator": "50"
      },
      "enable_license": "1",
      "enable_license_key": "1",
      "free_downloads": [
              "/Applications/XAMPP/wpdm/wp-content/uploads/2019/04/The-Alchemist-free-sample.pdf"
          ],
      "meta_input":{
      	"meta_key" : "Hello"
      }    
  }
]
```

This endpoint retrieves all packages. Use query parameters to filter packages.

### HTTP Request

<span class="http-request"><span class="http-verb http-get">GET</span><span class="api-endpoint">/wp-json/wpdm/v1/packages</span></span>

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
`number_of_posts` | 10 | Maximum number of items to be returned in result set.
`author` | empty | Send comma separated ids, not an array. `"1,2,5"` 
`tag` | empty | Send comma separated tag slugs, not an array. `"free,popular,new"` 
`categories` | empty | Send array of category terms. `["Business","Travel"]` 
`search` | empty | Limit results to those matching a string. `keyword` 

## Create a Package

```shell
curl -X POST \
  https://yoursite.com/wp-json/wpdm/v1/packages \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	 "title": "The Alchemist",
     "description": "The Alchemist follows the journey of an Andalusian shepherd boy named Santiago.",
     "excerpt": "The Alchemist is a novel by Brazilian author Paulo Coelho.",
     "status": "publish",
     "tags": [
        "novel",
        "paulo-coelho"
     ],
     "categories": [
        16
     ],
     "thumbnail": "https://example.com/wp-content/uploads/2019/01/the-alchemist.jpg",
     "additional_previews": [
        "https://example.com/wp-content/uploads/2019/03/the-alchemist-cover.jpg",
        "https://example.com/wp-content/uploads/2019/03/the-alchemist-map.jpg"
     ]
}'
```

> The JSON response looks like the following example:

```json
{
      "id": 6488,
      "title": "The Alchemist",
      "slug": "the-alchemist",
      "description": "The Alchemist follows the journey of an Andalusian shepherd boy named Santiago.",
      "excerpt": "The Alchemist is a novel by Brazilian author Paulo Coelho.",
      "author": 1,
      "status": "publish",
      "parent": 0,
      "tags": [
          "novel",
          "paulo-coelho"
      ],
      "categories": [
          16
      ],
      "thumbnail": "https://example.com/wp-content/uploads/2019/01/the-alchemist.jpg",
      "additional_previews": [
          "https://example.com/wp-content/uploads/2019/03/the-alchemist-cover.jpg",
          "https://example.com/wp-content/uploads/2019/03/the-alchemist-map.jpg"
      ],
      "version": "3.0.0",
      "link_label": "Download",
      "quota": 0,
      "download_limit_per_user": "100",
      "view_count": 80,
      "download_count": 14,
      "package_size": "811.84 KB",
      "access": [
          "guest",
          "subscriber",
          "administrator"
      ],
      "user_access": [
          "admin"
      ],
      "individual_file_download": "1",
      "cache_zip": "-1",
      "template": "link-template-calltoaction1",
      "page_template": "page-template-1col-flat",
      "files": {
          "1": "The Alchemist.pdf"
      },
      "fileinfo": {
          "1": {
              "title": "The Alchemist",
              "password": "",
              "license_price": {
                  "standard": "",
                  "extended": "",
                  "unlimited": ""
              },
              "price": ""
          }
      },
      "package_dir": "",
      "publish_date": "2019-04-01 12:00 am",
      "expire_date": "2019-08-31 12:00 am",
      "terms_lock": "1",
      "terms_title": "Agree to terms",
      "terms_conditions": "You can't redistribute without prior authorization.",
      "terms_check_label": "Checkbox Label",
      "password_lock": "1",
      "password": "[123][456]",
      "password_usage_limit": "2",
      "linkedin_lock": "1",
      "linkedin_message": "LinkedIn Share Lock message",
      "linkedin_url": "https://www.wpdownloadmanager.com/",
      "tweet_lock": "1",
      "tweet_message": "Custom tweet message",
      "twitterfollow_lock": "1",
      "twitter_handle": "Shahriar",
      "facebooklike_lock": "1",
      "facebook_like": "",
      "email_lock": "1",
      "email_lock_title": "Subscribe To Download",
      "email_lock_msg": "",
      "email_lock_idl": "0",
      "icon": "https://example.com/wp-content/plugins/download-manager/assets/file-type-icons/arrow.png",
      
      "base_price": "12.00",
      "sales_price": "10.00",
      "sales_price_expire": "2019-08-31 12:00 am",
      "pay_as_you_want": "0",
      "license": {
          "standard": {
              "active": "1"
          },
          "extended": {
              "price": "22",
              "active": "1"
          },
          "unlimited": {
              "price": "32",
              "active": "1"
          }
      },
      "discount": {
          "subscriber": "10",
          "contributor": "20",
          "author": "30",
          "editor": "40",
          "administrator": "50"
      },
      "enable_license": "1",
      "enable_license_key": "1",
      "free_downloads": [
              "/Applications/XAMPP/wpdm/wp-content/uploads/2019/04/The-Alchemist-free-sample.pdf"
          ],
      "meta_input":{
      	"meta_key" : "Hello"
      }    
  }
```

This endpoint creates a new Package and sets package properties based on POST data.

### HTTP Request

<span class="http-request"><span class="http-verb http-post">POST</span><span class="api-endpoint">/wp-json/wpdm/v1/packages</span></span>

## Get a Package

```shell
curl -X GET \
  https://yoursite.com/wp-json/wpdm/v1/packages/23 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
      "id": 6488,
      "title": "The Alchemist",
      "slug": "the-alchemist",
      "description": "The Alchemist follows the journey of an Andalusian shepherd boy named Santiago.",
      "excerpt": "The Alchemist is a novel by Brazilian author Paulo Coelho.",
      "author": 1,
      "status": "publish",
      "parent": 0,
      "tags": [
          "novel",
          "paulo-coelho"
      ],
      "categories": [
          16
      ],
      "thumbnail": "https://example.com/wp-content/uploads/2019/01/the-alchemist.jpg",
      "additional_previews": [
          "https://example.com/wp-content/uploads/2019/03/the-alchemist-cover.jpg",
          "https://example.com/wp-content/uploads/2019/03/the-alchemist-map.jpg"
      ],
      "version": "3.0.0",
      "link_label": "Download",
      "quota": 0,
      "download_limit_per_user": "100",
      "view_count": 80,
      "download_count": 14,
      "package_size": "811.84 KB",
      "access": [
          "guest",
          "subscriber",
          "administrator"
      ],
      "user_access": [
          "admin"
      ],
      "individual_file_download": "1",
      "cache_zip": "-1",
      "template": "link-template-calltoaction1",
      "page_template": "page-template-1col-flat",
      "files": {
          "1": "The Alchemist.pdf"
      },
      "fileinfo": {
          "1": {
              "title": "The Alchemist",
              "password": "",
              "license_price": {
                  "standard": "",
                  "extended": "",
                  "unlimited": ""
              },
              "price": ""
          }
      },
      "package_dir": "",
      "publish_date": "2019-04-01 12:00 am",
      "expire_date": "2019-08-31 12:00 am",
      "terms_lock": "1",
      "terms_title": "Agree to terms",
      "terms_conditions": "You can't redistribute without prior authorization.",
      "terms_check_label": "Checkbox Label",
      "password_lock": "1",
      "password": "[123][456]",
      "password_usage_limit": "2",
      "linkedin_lock": "1",
      "linkedin_message": "LinkedIn Share Lock message",
      "linkedin_url": "https://www.wpdownloadmanager.com/",
      "tweet_lock": "1",
      "tweet_message": "Custom tweet message",
      "twitterfollow_lock": "1",
      "twitter_handle": "Shahriar",
      "facebooklike_lock": "1",
      "facebook_like": "",
      "email_lock": "1",
      "email_lock_title": "Subscribe To Download",
      "email_lock_msg": "",
      "email_lock_idl": "0",
      "icon": "https://example.com/wp-content/plugins/download-manager/assets/file-type-icons/arrow.png",
      
      "base_price": "12.00",
      "sales_price": "10.00",
      "sales_price_expire": "2019-08-31 12:00 am",
      "pay_as_you_want": "0",
      "license": {
          "standard": {
              "active": "1"
          },
          "extended": {
              "price": "22",
              "active": "1"
          },
          "unlimited": {
              "price": "32",
              "active": "1"
          }
      },
      "discount": {
          "subscriber": "10",
          "contributor": "20",
          "author": "30",
          "editor": "40",
          "administrator": "50"
      },
      "enable_license": "1",
      "enable_license_key": "1",
      "free_downloads": [
              "/Applications/XAMPP/wpdm/wp-content/uploads/2019/04/The-Alchemist-free-sample.pdf"
          ],
      "meta_input":{
      	"meta_key" : "Hello"
      }    
  }
```

This endpoint retrieves a specific Package by ID.

### HTTP Request

<span class="http-request"><span class="http-verb http-get">GET</span><span class="api-endpoint">/wp-json/wpdm/v1/packages/:id</span></span>

## Update a Package

```shell
curl -X PUT \
  https://yoursite.com/wp-json/wpdm/v1/packages/6488 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json' \
  -d '{
	 "title": "The Alchemist",
     "description": "The Alchemist follows the journey of an Andalusian shepherd boy named Santiago.",
     "excerpt": "The Alchemist is a novel by Brazilian author Paulo Coelho.",
     "status": "publish",
     "tags": [
        "novel",
        "paulo-coelho"
     ],
     "categories": [
        16
     ],
     "thumbnail": "https://example.com/wp-content/uploads/2019/01/the-alchemist.jpg",
     "additional_previews": [
        "https://example.com/wp-content/uploads/2019/03/the-alchemist-cover.jpg",
        "https://example.com/wp-content/uploads/2019/03/the-alchemist-map.jpg"
     ]
}'
```

> The JSON response looks like the following example:

```json
{
      "id": 6488,
      "title": "The Alchemist",
      "slug": "the-alchemist",
      "description": "The Alchemist follows the journey of an Andalusian shepherd boy named Santiago.",
      "excerpt": "The Alchemist is a novel by Brazilian author Paulo Coelho.",
      "author": 1,
      "status": "publish",
      "parent": 0,
      "tags": [
          "novel",
          "paulo-coelho"
      ],
      "categories": [
          16
      ],
      "thumbnail": "https://example.com/wp-content/uploads/2019/01/the-alchemist.jpg",
      "additional_previews": [
          "https://example.com/wp-content/uploads/2019/03/the-alchemist-cover.jpg",
          "https://example.com/wp-content/uploads/2019/03/the-alchemist-map.jpg"
      ],
      "version": "3.0.0",
      "link_label": "Download",
      "quota": 0,
      "download_limit_per_user": "100",
      "view_count": 80,
      "download_count": 14,
      "package_size": "811.84 KB",
      "access": [
          "guest",
          "subscriber",
          "administrator"
      ],
      "user_access": [
          "admin"
      ],
      "individual_file_download": "1",
      "cache_zip": "-1",
      "template": "link-template-calltoaction1",
      "page_template": "page-template-1col-flat",
      "files": {
          "1": "The Alchemist.pdf"
      },
      "fileinfo": {
          "1": {
              "title": "The Alchemist",
              "password": "",
              "license_price": {
                  "standard": "",
                  "extended": "",
                  "unlimited": ""
              },
              "price": ""
          }
      },
      "package_dir": "",
      "publish_date": "2019-04-01 12:00 am",
      "expire_date": "2019-08-31 12:00 am",
      "terms_lock": "1",
      "terms_title": "Agree to terms",
      "terms_conditions": "You can't redistribute without prior authorization.",
      "terms_check_label": "Checkbox Label",
      "password_lock": "1",
      "password": "[123][456]",
      "password_usage_limit": "2",
      "linkedin_lock": "1",
      "linkedin_message": "LinkedIn Share Lock message",
      "linkedin_url": "https://www.wpdownloadmanager.com/",
      "tweet_lock": "1",
      "tweet_message": "Custom tweet message",
      "twitterfollow_lock": "1",
      "twitter_handle": "Shahriar",
      "facebooklike_lock": "1",
      "facebook_like": "",
      "email_lock": "1",
      "email_lock_title": "Subscribe To Download",
      "email_lock_msg": "",
      "email_lock_idl": "0",
      "icon": "https://example.com/wp-content/plugins/download-manager/assets/file-type-icons/arrow.png",
      
      "base_price": "12.00",
      "sales_price": "10.00",
      "sales_price_expire": "2019-08-31 12:00 am",
      "pay_as_you_want": "0",
      "license": {
          "standard": {
              "active": "1"
          },
          "extended": {
              "price": "22",
              "active": "1"
          },
          "unlimited": {
              "price": "32",
              "active": "1"
          }
      },
      "discount": {
          "subscriber": "10",
          "contributor": "20",
          "author": "30",
          "editor": "40",
          "administrator": "50"
      },
      "enable_license": "1",
      "enable_license_key": "1",
      "free_downloads": [
              "/Applications/XAMPP/wpdm/wp-content/uploads/2019/04/The-Alchemist-free-sample.pdf"
          ],
      "meta_input":{
      	"meta_key" : "Hello"
      }    
  }
```

This endpoint updates a specific Package by ID.

### HTTP Request

<span class="http-request"><span class="http-verb http-put">PUT</span><span class="api-endpoint">/wp-json/wpdm/v1/packages/:id</span></span>

## Delete a Package

```shell
curl -X DELETE \
  https://yoursite.com/wp-json/wpdm/v1/packages/6488 \
  -H 'Authorization: Bearer 613efe9acb0d5c2b' \
  -H 'Content-Type: application/json'
```

> The JSON response looks like the following example:

```json
{
      "id": 6488,
      "title": "The Alchemist",
      "slug": "the-alchemist",
      "description": "The Alchemist follows the journey of an Andalusian shepherd boy named Santiago.",
      "excerpt": "The Alchemist is a novel by Brazilian author Paulo Coelho.",
      "author": 1,
      "status": "publish",
      "parent": 0,
      "tags": [
          "novel",
          "paulo-coelho"
      ],
      "categories": [
          16
      ],
      "thumbnail": "https://example.com/wp-content/uploads/2019/01/the-alchemist.jpg",
      "additional_previews": [
          "https://example.com/wp-content/uploads/2019/03/the-alchemist-cover.jpg",
          "https://example.com/wp-content/uploads/2019/03/the-alchemist-map.jpg"
      ],
      "version": "3.0.0",
      "link_label": "Download",
      "quota": 0,
      "download_limit_per_user": "100",
      "view_count": 80,
      "download_count": 14,
      "package_size": "811.84 KB",
      "access": [
          "guest",
          "subscriber",
          "administrator"
      ],
      "user_access": [
          "admin"
      ],
      "individual_file_download": "1",
      "cache_zip": "-1",
      "template": "link-template-calltoaction1",
      "page_template": "page-template-1col-flat",
      "files": {
          "1": "The Alchemist.pdf"
      },
      "fileinfo": {
          "1": {
              "title": "The Alchemist",
              "password": "",
              "license_price": {
                  "standard": "",
                  "extended": "",
                  "unlimited": ""
              },
              "price": ""
          }
      },
      "package_dir": "",
      "publish_date": "2019-04-01 12:00 am",
      "expire_date": "2019-08-31 12:00 am",
      "terms_lock": "1",
      "terms_title": "Agree to terms",
      "terms_conditions": "You can't redistribute without prior authorization.",
      "terms_check_label": "Checkbox Label",
      "password_lock": "1",
      "password": "[123][456]",
      "password_usage_limit": "2",
      "linkedin_lock": "1",
      "linkedin_message": "LinkedIn Share Lock message",
      "linkedin_url": "https://www.wpdownloadmanager.com/",
      "tweet_lock": "1",
      "tweet_message": "Custom tweet message",
      "twitterfollow_lock": "1",
      "twitter_handle": "Shahriar",
      "facebooklike_lock": "1",
      "facebook_like": "",
      "email_lock": "1",
      "email_lock_title": "Subscribe To Download",
      "email_lock_msg": "",
      "email_lock_idl": "0",
      "icon": "https://example.com/wp-content/plugins/download-manager/assets/file-type-icons/arrow.png",
      
      "base_price": "12.00",
      "sales_price": "10.00",
      "sales_price_expire": "2019-08-31 12:00 am",
      "pay_as_you_want": "0",
      "license": {
          "standard": {
              "active": "1"
          },
          "extended": {
              "price": "22",
              "active": "1"
          },
          "unlimited": {
              "price": "32",
              "active": "1"
          }
      },
      "discount": {
          "subscriber": "10",
          "contributor": "20",
          "author": "30",
          "editor": "40",
          "administrator": "50"
      },
      "enable_license": "1",
      "enable_license_key": "1",
      "free_downloads": [
              "/Applications/XAMPP/wpdm/wp-content/uploads/2019/04/The-Alchemist-free-sample.pdf"
          ],
      "meta_input":{
      	"meta_key" : "Hello"
      }    
  }
```

This endpoint deletes a specific Package by ID.

### HTTP Request

<span class="http-request"><span class="http-verb http-delete">DELETE</span><span class="api-endpoint">/wp-json/wpdm/v1/packages/:id</span></span>