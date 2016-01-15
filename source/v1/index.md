---
title: GitLapse API Reference

language_tabs:
  - c: Git 
  - ruby: Ruby
  - shell: cURL 

toc_footers:
  
  - <a href='#'>Sign Up for a Developer Key</a>

  - <a href='https://github.com/gitlapse/docs'>Contribute to Gitlapse Opensource API</a>

  - <a href='http://gitlapse.com'> © gitlapse 2016 </a>

includes:
  - errors

search: true
---

# API Reference 
nice intro
## Philosophy 
This is philo for all...

> first, run gem install gitlapse
> if you are using rbenv, run rbenv rehash

```c

git lapse path/to/your/git/file

```
```shell

# With shell, you can just pass the correct header with each request
curl -v -H "Accept: application/json" -H "Content-type: application/json" -X POST -d '{:SHA => blob_sha_value, :content => blob_content_value}' http://api.gitlapse.com/v1/git/full_lapse 

```
```ruby
gem install gitlapse
```


## Quickstart
### Installation 
### copy\paste this oneline of code into your terminal

# API Resources

like using legos to put together to build something great.


API must appeal to emotion.. you will love Gitlapse.


API designed for laziness


API designed for lazy

intuitive well-documented oinionated



Gitlapse API is an opensource REST API for everyone who uses git, either on their own machines or via Git hosting services like Github & Bitbucket, you can always contribute to Gitlapse API on https://github.com/gitlapse/docs . 

Gitlapse API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. 

Gitlapse API uses built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. 

Gitlapse API supports cross-origin resource sharing, allowing you to interact securely with it, from a client-side web application (though you should never expose your secret API key in any public website`s client-side code). 

JSON is returned by all API responses, including errors, although our API libraries convert responses to appropriate language-specific objects. Gitlapse API endpoints can be reached via Git itself (Gitlapse Git Extension), cURL(Standard Https), or through Gitlapse`s Ruby SDK (gem install gitlapse).




Gitlapse API resonate pragrammatic intuitive API Design principles by keeping consistency with 'The Good Parts' of Modern Web APIs, that a natural, functionally layred, least congitive use of the API, that We hope will insipre your confidence and freedom to explore and use. 


Gitlapse API resonate pragrammatic API Design principles by remaining consistently natural, functionally layred, and more importantly least congitive,to insipre your confidence and freedom to explore and use.


Simple enough, Gitlapses two base URLs are there, 1)collection /lapses/ 2)specific lapse /lapse/SHA  . with Eight HTTP verbs

#Add a photo of the two base URLS & the Eight HTTP verbs

More complex queries, say for Github or Bitbucket are avialable on their own sections, that also uses the same two base URLs

Two base URLs: 
Collection

keeps the simple things simple, while the complex things possible.

Errors return most relevant links to the documentation and IRC #channel for help. Gitlapse uses the STANDARD HTTP Status code aoviding the bitfall that most API providers do with custom Error messages that requires you to check it out.

Gitlapse API implements high scope mandatory versioning with whole numbers, v1, v2, v3, etc. to interface with the Gitlapse backends.

Functional Minimalism - things as simple as possible but not simpler
least Cognitive load -
Functional Layering: designed advantage was given focused towards the 80percent of the usecases, while keeping complex usecases at a close approach.


and achieveing affordance by suggests how the API can be used 

affordance can be achieved by:
or other interface elements e.g. underlined links or default button styles.
in the physical properties of an object should suggest how it can be used. 


COPY/PASTE URL, HIT THE ENTER BUTTON IN THE BRWOWERS, AND SOMTHING MEANINGFULL HAPPEN

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

