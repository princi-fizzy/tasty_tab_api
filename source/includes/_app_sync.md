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

response = Unirest.get "http://localhost:3000/api/v1/24/app_sync.json?access_token=8de9358df65b86b643a206cb795355a2"

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


The App Sync API will return entire restaurant hash in a nested & easy to parse format. This hash includes restaurant menus, menu categories, foost


These hash may contain duplicate data, so remember to remove any redundant data.

### HTTP Request

`GET http://tastytab.com/api/v1/:id/app_sync?access_token=8de9358df65b86b643a206cb795355a2`


Replace `:id` with restaurant id. Also, remember to replace access_token with your own access_token.


Data will only be sent if it has changed since last sync. We continuously run sync task in background to make sure everything stays in sync.

To optimize things try to set sync interval & sync time in accounts setting, and make sync request accordingly.



## Sync Restaurant Data With Android

```json
{
  "access_token": "8de9358df65b86b643a206cb795355a2"
  "restaurant" {
    "id": 2
  }
  "app_sync_token" : "testing"
}
```

```ruby
require 'unirest'

response = Unirest.get "http://localhost:3000/api/v1/restaurants/2/app_sync2?access_token=8de9358df65b86b643a206cb795355a2&app_sync_token=testing"

response.raw_body
```
> The above command returns JSON structured like this:


```json
{
    "id": 2,
    "name": "sagar ratna",
    "logo": {
        "logo": {
            "url": "/uploads/restaurant/logo/2/f2.jpg",
            "thumb": {
                "url": "/uploads/restaurant/logo/2/thumb_f2.jpg"
            }
        }
    },
    "pos_sync_interval": "Daily",
    "android_app_sync_token": "1435148022",
    "Remove remaining hash for brevity.."
}
```

```ruby
{
    "id": 2,
    "name": "sagar ratna",
    "logo": {
        "logo": {
            "url": "/uploads/restaurant/logo/2/f2.jpg",
            "thumb": {
                "url": "/uploads/restaurant/logo/2/thumb_f2.jpg"
            }
        }
    },
    "pos_sync_interval": "Daily",
    "android_app_sync_token": "1435148022",
    "Remove remaining hash for brevity.."
}
```
The App Sync API will return entire restaurant hash in a nested & easy to parse format. This hash includes restaurant menus, menu categories, foost

These hash may contain duplicate data, so remember to remove any redundant data.

### HTTP Request

`GET http://tastytab.com/api/v1/restaurants/:id/app_sync2?access_token=8de9358df65b86b643a206cb795355a2`

Replace `:id` with restaurant id. Also, remember to replace access_token with your own access_token.


Data will only be sent if it has changed since last sync. We continuously run sync task in background to make sure everything stays in sync.

To optimize things try to set sync interval & sync time in accounts setting, and make sync request accordingly.
