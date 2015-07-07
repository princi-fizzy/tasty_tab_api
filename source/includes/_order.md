# Order

This is order API and it  will help you to create new order on application database and ethor also , apart from creation of new order we also have api to push food items in existing order .

## New Order Api

```json
{
  "access_token":                  "sample_api_access_token"
  "customer_first_name":           "Sachin"
  "customer_last_name":            "Mathur"
  "birth_date":                    "25-08-1989"
  "email_address":                 "sachin_mathur@tastytab.com"
  "phone_area_code":               "101"
  "phone_number":                  "1234512345"
}


```

```ruby
require 'unirest'

response = Unirest.post "http://192.34.57.207/api/v1/orders?access_token", headers:{ "Accept" => "application/json" }, parameters: {customer_first_name: "Sachin" , customer_last_name: "Mathur" , birth_date: "25-08-1989" , email_address: "sachin_mathur@tastytab.com" , phone_area_code: "101" , phone_number: "1234512345", access_token: "sample_api_access_token"}


response.raw_body
```
> The above command returns JSON structured like this:

```json
{
    "id": 2,
    "pos_id": "QSCSI4OR80",
    "order_type": null,
    "order_status": "STAGED",
    "order_date": "2015-07-07T10:07:28.483Z",
    "restaurant": {
        "id": 3,
        "name": "sagar ratna"
    },
    "table": null,
    "customer": {
        "id": 27,
        "first_name": "Sachin",
        "last_name": "Mathur",
        "email": "sachin_mathur@tastytab.com",
        "phone_number": "1234512345"
    }
}

```


```ruby
{
    "id": 2,
    "pos_id": "QSCSI4OR80",
    "order_type": null,
    "order_status": "STAGED",
    "order_date": "2015-07-07T10:07:28.483Z",
    "restaurant": {
        "id": 3,
        "name": "sagar ratna"
    },
    "table": null,
    "customer": {
        "id": 27,
        "first_name": "Sachin",
        "last_name": "Mathur",
        "email": "sachin_mathur@tastytab.com",
        "phone_number": "1234512345"
    }
}
```

This endpoint create a fresh order on application database and ethor as well . Before creating a new order we have to create a new customer and then book a table for that customer .

|---- Steps ----|

1.  Create a new customer (we have to send parameters to create new cutomer at the time of order creation , and one more thing we have to pass unique email address for customer .)

2.  Book a table for customer . it will only book a table whose availability is true .

3.  Create new order on application as well as on ethor .

4.  Reserve that particular table for customer  .

### HTTP Request

`POST  http://192.34.57.207/api/v1/orders?access_token=sample_api_access_token`

### Query Parameters

Parameter | Description
--------- | -----------
customer_first_name | Make sure it's does not empty  .
customer_last_name | Make sure it's does not empty .
birth_date | Make sure it's does not empty .
email_address | Make sure it's does not empty and it should be unique email address .
phone_area_code | Make sure it's does not empty  .
phone_number | Make sure it's does not empty  .


<aside class="success">
Customer is created and its associated  order is also created on application database and ethor .
</aside>
