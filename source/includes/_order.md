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

response = Unirest.get "http://localhost:3000/api/v1/restaurants/2/search", headers:{ "Accept" => "application/json" }, parameters: {search_value: "FRIED ZUCCHINI" , access_token: "sample_api_access_token"}

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
[
    {
        "id": 12,
        "name": "FRIED ZUCCHINI",
        "pos_name": "Fried Zucchini",
        "price": 6.95,
        "description": null,
        "is_out_of_stock": false,
        "item_modifiers": [],
        "food_images": [
            {
                "food_image": {
                    "id": 1,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/1/f1.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/1/thumb_f1.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 2,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/2/f2.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/2/thumb_f2.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 3,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/3/f3.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/3/thumb_f3.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 4,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/4/f4.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/4/thumb_f4.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 5,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/5/f5.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/5/thumb_f5.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 6,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/6/f6.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/6/thumb_f6.jpg"
                            }
                        }
                    }
                }
            }
        ]
    }
]
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

## Get all food items of particular category

```json
{
  "access_token":   "sample_api_access_token"
  "search_value":   "Sides"
}

```

```ruby
require 'unirest'

response = Unirest.get "http://localhost:3000/api/v1/restaurants/2/search", headers:{ "Accept" => "application/json" }, parameters: {search_value: "Sides" , access_token: "sample_api_access_token"}

response.raw_body
```
> The above command returns JSON structured like this:


```json

{
    "food_items": [
        {
            "food_item": {
                "id": 12,
                "name": "FRIED ZUCCHINI",
                "pos_name": "Fried Zucchini",
                "price": 6.95,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [],
                "food_images": [
                    {
                        "food_image": {
                            "id": 1,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/1/f1.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/1/thumb_f1.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 2,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/2/f2.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/2/thumb_f2.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 3,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/3/f3.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/3/thumb_f3.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 4,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/4/f4.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/4/thumb_f4.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 5,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/5/f5.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/5/thumb_f5.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 6,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/6/f6.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/6/thumb_f6.jpg"
                                    }
                                }
                            }
                        }
                    }
                ]
            }
        },
        {
            "food_item": {
                "id": 13,
                "name": "POTATO SKINS",
                "pos_name": "Potato Skins",
                "price": 7.99,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [],
                "food_images": []
            }
        },
        {
            "food_item": {
                "id": 14,
                "name": "GARLIC BREAD",
                "pos_name": "Garlic Bread",
                "price": 3.49,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [],
                "food_images": []
            }
        },
        {
            "food_item": {
                "id": 15,
                "name": "BBQ WINGS",
                "pos_name": "BBQ Wings",
                "price": 6.99,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [
                    {
                        "item_modifier": {
                            "id": 94,
                            "pos_name": "Bleu Cheese",
                            "price": null
                        }
                    },
                    {
                        "item_modifier": {
                            "id": 95,
                            "pos_name": "No Dressing",
                            "price": null
                        }
                    },
                    {
                        "item_modifier": {
                            "id": 96,
                            "pos_name": "Ranch",
                            "price": null
                        }
                    }
                ],
                "food_images": []
            }
        }
    ]
}

```

```ruby
{
    "food_items": [
        {
            "food_item": {
                "id": 12,
                "name": "FRIED ZUCCHINI",
                "pos_name": "Fried Zucchini",
                "price": 6.95,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [],
                "food_images": [
                    {
                        "food_image": {
                            "id": 1,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/1/f1.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/1/thumb_f1.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 2,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/2/f2.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/2/thumb_f2.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 3,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/3/f3.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/3/thumb_f3.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 4,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/4/f4.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/4/thumb_f4.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 5,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/5/f5.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/5/thumb_f5.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 6,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/6/f6.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/6/thumb_f6.jpg"
                                    }
                                }
                            }
                        }
                    }
                ]
            }
        },
        {
            "food_item": {
                "id": 13,
                "name": "POTATO SKINS",
                "pos_name": "Potato Skins",
                "price": 7.99,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [],
                "food_images": []
            }
        },
        {
            "food_item": {
                "id": 14,
                "name": "GARLIC BREAD",
                "pos_name": "Garlic Bread",
                "price": 3.49,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [],
                "food_images": []
            }
        },
        {
            "food_item": {
                "id": 15,
                "name": "BBQ WINGS",
                "pos_name": "BBQ Wings",
                "price": 6.99,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [
                    {
                        "item_modifier": {
                            "id": 94,
                            "pos_name": "Bleu Cheese",
                            "price": null
                        }
                    },
                    {
                        "item_modifier": {
                            "id": 95,
                            "pos_name": "No Dressing",
                            "price": null
                        }
                    },
                    {
                        "item_modifier": {
                            "id": 96,
                            "pos_name": "Ranch",
                            "price": null
                        }
                    }
                ],
                "food_images": []
            }
        }
    ]
}

```


This endpoint search all food items of particular category in a particular restaurant.
### HTTP Request

`GET http://localhost:3000/api/v1/restaurants/2/search?access_token=sample_api_access_token&search_value=Sides`

### URL Parameters

Parameter | Description
--------- | -----------
search_value | It should be valid food item name or valid category name
<aside class="success">
All food items and their details of particular category is fetched from database .
</aside>
