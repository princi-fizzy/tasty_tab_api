# Customers

## Registration

```json
{
  "access_token": "sample_api_access_token"
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
  "access_token": "sample_api_access_token"
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

`http://localhost:3000/api/v1/customers/sessions.json?access_token=sample_api_access_token`

### URL Parameters

Parameter | Description
--------- | -----------
email | Registered email id of the customer
password | Associated password

