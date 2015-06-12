---
title: API Reference

language_tabs:
  - json
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
`GET http://www.tastytab.com/api/v1/cutomers?access_token=8de9358df65b86b643a206cb795355a2`


```json
{
  "access_token": "8de9358df65b86b643a206cb795355a2"
  "customer" {
    "name": "Rahul"
  }
}
```

```ruby
require 'httparty'

response = HTTParty.get('http://www.tastytab.com/api/v1/?access_token=8de9358df65b86b643a206cb795355a2')

response.body
```


> Make sure to replace sample access token `8de9358df65b86b643a206cb795355a2` with your API key.

```json
{
  "success": "Success"
}
```

```ruby
{
  "success": "Success"
}
```


TastyTab uses access token to allow access to the API. You can register a new TastyTab access token by contacting us.

TastyTab expects for the access_token to be included in all API requests to the server in a header that looks like the following:

`access_token: "8de9358df65b86b643a206cb795355a2"`

<aside class="notice">
You must replace <code>8de9358df65b86b643a206cb795355a2</code> with your personal access token.
</aside>





# Customers

## Registration

```json
{
  "access_token": "8de9358df65b86b643a206cb795355a2"
  "customer" {
    "email": "user@example.com",
    "password": "testing",
    "pos_customer_id": 5
  }
}
```

```ruby
require 'unirest'

response = Unirest.post "http://localhost:3000/api/v1/customers/registrations", headers:{ "Accept" => "application/json" }, parameters: {customer: {email: "user@example.com", password: "testing", pos_customer_id: 5}}

response.raw_body
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

```ruby
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

```json
{
  "access_token": "8de9358df65b86b643a206cb795355a2"
  "customer" {
    "email": "user@example.com",
    "password": "testing"
  }
}
```

```ruby
require 'unirest'

response = Unirest.post "http://tastytab.com/api/v1/customers/sessions", headers:{ "Accept" => "application/json" }, parameters: {customer: {email: "user@example.com", password: "testing"}}
response.raw_body
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

```ruby
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

## Sync Restaurant Data

```json
{
  "access_token": "8de9358df65b86b643a206cb795355a2"
  "restaurant" {
    "id": 1
  }
}
```

```ruby
require 'unirest'

response = Unirest.get "http://localhost:3000/api/v1/24/app_sync.json?access_token=trap"

response.raw_body
```

> The above command returns JSON structured like this:

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

```ruby
{
  "id": 24,
  "name": "Burger King",
  "logo" {
    "logo" {
      "url": "/images/fallback/default.png",
      "thumb" {
        "url": "/images/fallback/thumb_default.png"
      }
    }
  }
  "Remove remaining hash for brevity.."
}
```


The App Sync API will return entire restaurant hash in a nested & easy to parse format. This hash includes restaurant menus, menu categories, food items, and food item reviews.


These hash may contain duplicate data, so remember to remove any redundant data.


### HTTP Request

`GET http://tastytab.com/api/v1/:id/app_sync?access_token=8de9358df65b86b643a206cb795355a2`


Replace `:id` with restaurant id. Also, remember to replace access_token with your own access_token.


Data will only be sent if it has changed since last sync. We continuously run sync task in background to make sure everything stays in sync.

To optimize things try to set sync interval & sync time in accounts setting, and make sync request accordingly.




