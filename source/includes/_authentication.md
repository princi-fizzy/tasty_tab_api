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
