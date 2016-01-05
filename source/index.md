---
title: GitLapse API Reference updated

language_tabs:
  - c: Git 
  - ruby: Ruby
  - shell: cURL 

toc_footers:
  
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://gitlapse.com'> © gitlapse 2016 </a>

includes:
  - errors

search: true
---

# API Reference

```c
git lapse somthing
```
```shell
# With shell, you can just pass the correct header with each request
curl "https://api.gitlapse.com/v1/auth"
-H "Authorization: username"
```
```ruby
gem install gitlapse
```

The Gitlapse API is organized around REST. Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. 

We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. 

We support cross-origin resource sharing, allowing you to interact securely with our API from a client-side web application (though you should never expose your secret API key in any public website`s client-side code). 

JSON is returned by all API responses, including errors, although our API libraries convert responses to appropriate language-specific objects. Gitlapse API endpoints can be reached via Git, curl, or through our ruby SDK.


<aside class="notice">...</aside>

<aside class="success">...</aside>

<aside class="warning">...</aside>

###Start using GitLapse API via running `gem install gitlapse` in your Console.

## Authentication

> To authorize, use this code:

```c
some git
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```ruby
require "gitlapse"
Gitlapse.api_key = "username"
```
> For beta, makeup a username of your choice and use it as API key for debugging purposes. Your choosen username will be used as part of the slug to host your repo on server, i.e. "username/repo_name". Thus, please make sure to replace `username` with your API key.


Gitlapse uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://gitlapse.com/developers).

Gitlapse expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: apikey`

<aside class="notice">
You must replace <code>username</code> with your personal API key.
</aside>

# Github 

```c
# inside your cloned github repo
git lapses all 
```

```shell
curl "http://api.gitlapse.com/v1/github/:username/:reponame/lapses"
  -H "Authorization: username"
```
```ruby
require 'gitlapse'

api = Gitlapse.api_key('meowmeowmeow')
api.github.lapses.get(:reponame)
```


# Lapses 

## Get All Lapses

```c
git lapses all
```

```shell
curl "http://api.gitlapse.com/v1/:username/:reponame/lapses"
  -H "Authorization: username"
```
```ruby
require 'gitlapse'

api = Gitlapse.api_key('meowmeowmeow')
api.lapses.get
```


> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all lapses.

### HTTP Request

`GET http://api.gitlapse.com/v1/:username/:reponame/lapses`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Lapse 
```c
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```ruby
require 'gitlapse'

api = Gitlapse.api_key('username')
api.username
api.repo
api.lapses.get(2)
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

<aside class="warning">If you are not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve
