---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
 # - ruby
 # - python
 # - javascript

toc_footers:
 # - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - posts
  - errors

search: true
---

# Introduction

Welcome to the KK API! You can use our API to access KK API endpoints, which can get information on various 'Mind Your Own Businesses'es.

This example API documentation page was created with [Slate](https://github.com/tripit/slate).

# Usage

## Access Token

> To authorize, use these headers:

```shell
curl "api_endpoint_here"
  -H "access-token: xxxxxxxxxxx"
  -H "client: xxxxxxxxxxx"
  -H "expiry: xxxxxxxxxxx"
  -H "uid: xxxxxxxxxxx"
  -H "token-type: xxxxxxxxxxx"
```

> Make sure to replace `xxxxxxxxxxx` with your respective field from the response headers in any API response.

KK uses access tokens to allow access to the API.

KK expects for the access token, client. expiry, uid and token-type to be included in all API requests to the server in a header that looks like the following:

`access-token: xxxxxxxxxxx`

`client: xxxxxxxxxxx`

`expiry: xxxxxxxxxxx`

`uid: xxxxxxxxxxx`

`token-type: xxxxxxxxxxx`


<aside class="notice">
You must replace <code>xxxxxxxxxxx</code> with our respective field from the response headers in any API response.
</aside>

# Auth

## Log In


```shell
curl http://localhost:3000/auth/sign_in 
  -X POST  
  -F "email=user_admin@gmail.com" 
  -F "password=Pras1234" 

  
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "email": "user_admin@gmail.com",
    "name": "Prasanna Mishra",
    "image": null,
    "roles": [
      "admin"
    ],
    "admin": true
  }
}
```

This endpoint logs in a user.

### HTTP Request

`POST http://localhost:3000/auth/sign_in`

### Parameters

Parameter | Description
--------- | -----------
email | Self Explanatory.
password | Self Explanatory.

<!-- <aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside> -->
## Sign Up

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

