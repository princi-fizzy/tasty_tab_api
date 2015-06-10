---
title: API Reference

language_tabs:
  - ruby

toc_footers:
  - <a href='http://www.tastytab.com/'>TastyTab's documentation</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the TastyTab's API! You can use our API to sync restaurant data, authenticate restaurants, fetch customer data etc.

You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Technical Overview

**Base API Endpoint**: `http://tastytab.com/api/v1/`

JSON is returned in all API responses, including errors.


# Authentication

To interact with TastyTab's API you need to authenticate yourself by including provided `access_token` via query string parameter.

Some sensitive requests also require `waiter_token` & `manager_token`.

### HTTP REQUEST
`GET /api/v1/?access_token=8de9358df65b86b643a206cb795355a2`




> To authorize, use this code:

```ruby
require 'httparty'

response = HTTParty.get('http://www.tastytab.com/api/v1/?access_token=8de9358df65b86b643a206cb795355a2')

response.body
```

> Make sure to replace sample access token `8de9358df65b86b643a206cb795355a2` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Customers

## Registration

```ruby
require 'unirest'

response = Unirest.post "http://localhost:3000/api/v1/customers/registrations", headers:{ "Accept" => "application/json" }, parameters: {customer: {email: "user@example.com", password: "testing", pos_customer_id: 5}}

response.raw_body
#=> "{"id":8,"pos_customer_id":"5","first_name":null,"last_name":null,"email":"user@example.com","birth_date":null,"phone_area_code":null,"phone_number":null,"restaurant_opt_out":null,"tasty_tab_opt_out":null,"restaurant_id":null,"created_at":"2015-06-10T11:41:44.475Z","updated_at":"2015-06-10T11:41:44.475Z","auth_token":"zE21sfz4Ugkjuk4NH9U9"}"
```


> The above command returns JSON structured like this:

```json
{
  "id": 9,
  "pos_customer_id": "5",
  "first_name": null,
  "last_name": null,
  "email": "user@example.com",
  "birth_date": null,
  "phone_area_code": null,
  "phone_number": null,
  "restaurant_opt_out": null,
  "tasty_tab_opt_out": null,
  "restaurant_id": null,
  "created_at": "2015-06-10T11:45:48.813Z",
  "updated_at": "2015-06-10T11:45:48.813Z",
  "auth_token": "fUQRZPyxQ2c9oUiUJxn5"
}
```

This endpoint registers a new customer.

### HTTP Request

`GET http://tastytab.com/api/v1/customers/registrations`

### Query Parameters

Parameter | Description
--------- | -----------
email | Make sure it doesn't already exists.
password | Password must be atleast 6 characters long.
pos_customer_id | It must be unique. Each customer is assigned a unique pos id.

<aside class="success">
Customer has been registered. Yay!
</aside>

## Create a new session

```ruby
require 'unirest'

response = Unirest.post "http://tastytab.com/api/v1/customers/sessions", headers:{ "Accept" => "application/json" }, parameters: {customer: {email: "user@example.com", password: "testing"}}
response.raw_body
# => "{"id":2,"pos_customer_id":"2","first_name":"Rahul1","last_name":null,"email":"rahul1@fizzysoftware.com","birth_date":null,"phone_area_code":null,"phone_number":null,"restaurant_opt_out":null,"tasty_tab_opt_out":null,"restaurant_id":null,"created_at":"2015-05-11T10:00:58.000Z","updated_at":"2015-06-10T12:55:35.401Z","auth_token":"92LSsBmtWdzMwuzSWc6y"}"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "pos_customer_id": "2",
  "first_name": "Rahul1",
  "last_name": null,
  "email": "rahul1@fizzysoftware.com",
  "birth_date": null,
  "phone_area_code": null,
  "phone_number": null,
  "restaurant_opt_out": null,
  "tasty_tab_opt_out": null,
  "restaurant_id": null,
  "created_at": "2015-05-11T10:00:58.000Z",
  "updated_at": "2015-06-10T12:54:50.224Z",
  "auth_token": "92LSsBmtWdzMwuzSWc6y"
}
```

This endpoint generates an auth_token, which should be used to make all future customer related requests.

<aside class="warning">You should keep this access_token secret.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
email | Registered email id of the customer
password | Associated password


# App Sync

```ruby
require 'unirest'

response = Unirest.get "http://localhost:3000/api/v1/24/app_sync.json?access_token=trap"

response.raw_body
# => "{"id":24,"name":"Burger King","logo":{"logo":{"url":"/images/fallback/default.png","thumb":{"url":"/images/fallback/thumb_default.png"}}}, "Remove remaining hash for brevity.."}"

```



```json

{
  "id": 24,
  "name": "Burger King",
  "logo": {
    "logo": {
      "url": "/images/fallback/default.png",
      "thumb": {
        "url": "/images/fallback/thumb_default.png"
      }
    }
  }
  "Remove remaining hash for brevity.."
}


```

