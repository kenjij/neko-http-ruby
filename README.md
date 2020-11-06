# neko-http-ruby

Pure Ruby HTTP client using net/http. A simple wrapper to cover routine things.

## Getting Started

Just add the single Ruby file to your directory and:

```ruby
require_relative './neko-http'
```


## Usage

For basic use, class methods are handy. For example:

```ruby
# GET request with query
Neko::HTTP.get('http://example.com/search', {q: 'keyword'})

# POST request with form URL encoded body
params = {data: '8586568332BCF3AB042B7015'}
Neko::HTTP.post_form('http://example.com/search', params)

# POST request with JSON body and additional headers
params = {name: {first: 'Ken', alias: 'KJ'}}
headers = {'Authorization' => 'Bearer 12CDEF78'}
Neko::HTTP.post_form('http://example.com/search', params, headers)
```

Returns some data obtained from Net::HTTPResponse object in a hash.

```ruby
{
  code: res.code.to_i,
  headers: res.to_hash,
  body: res.body,
  message: res.msg
}
```

For more tailored use, or to call on other HTTP methods, create an instance and use its methods.

```ruby
neko = Neko::HTTP.new('https://httpbin.org')
neko.methods
# Some of the available methods
[
  :init_uri,
  :http,
  :headers,
  :delete,
  :headers=,
  :logger=,
  :logger,
  :get,
  :put,
  :patch,
  :close,
  :post,
  ...
]
```
