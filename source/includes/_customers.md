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

We have an API to  register a customer on the application.

|--------- Important points to create new customers ----------|

1 . First there are two ways to import customer in the application


      i)  Import customer while syncing from eThor .

      ii) User has a facility to register themself as a customer .

      iii)  When user register on application , they are required to fill the various fields such as : first name , last name , birth date , email address , password ,phone code , phone number .

      iv) Email address , password , phone code , phone number are the mandatory fields

      v) If customer with particular details are not present on the eThor , then it will also create the customer on eThor also .

      vi) Every customer has unique customer id on eThor , whenever a customer registration is done ,customer is also create on the eThor on background and once the customer is created on ethor , it will return the customer ID as (pos_customer_id) and save this ID in customer table .

      vi) In case customer register themself on application , and if customer is already present on the eThor , then it will return their unique customer id and save in the application's database .

      vii) Customer is associated with restaurant , Every customer can be associated with one or more restaurant at a time .



### HTTP Request

POST http://192.34.57.207/api/v1/customers/registrations?access_token=sample_api_access_token

### Query Parameters

Parameter | Description
--------- | -----------
customer[email] | Make sure it doesn’t already exists.
customer[first_name] | It should contain the first name of customer , it can be blank.
customer[last_name] | It should contain the last name of customer , it can be blank.
customer[birth_date] | It should contain the birth date of customer.
customer[password] | Password must be atleast 6 characters long.
customer[phone_area_code] | It cannot be blank.
customer[phone_number] | It cannot be blank.


<aside class="success">
Customer has been registered for a particular restaurant (restaurant is based on access token ).
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

