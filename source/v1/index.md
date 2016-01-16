---
title: GitLapse API Reference

language_tabs:
  - c: Git 
  - ruby: Ruby
  - shell: cURL 

toc_footers:
   - <a href='http://gitlapse.com'> © gitlapse 2016 </a><a href='http://gitlapse.com/terms'> Terms </a>
  
includes:
  - errors

search: true
---


# API v1 Reference 
Gitlapse API v1 lets you build Consumer Web\Mobile apps that POST\GET git lapses. API v1 only supports anonymous opensource and public git lapses, thus no custom authentication required yet fair-usage apply. 

## Quickstart
add this quickstart section to the main homepage of the beta and remove launching soon
### Installation 
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
You can install gitlapse on your system either from curl or gem.

`gem install gitlapse`
### copy\paste this oneline of code into your terminal

curl "http://api.gitlapse.com/v1/lapses/git/anonymous/:repo/"
anonymous is the shared username
repo is name of the git directory



## Philosophy 

Gitlapse API resonate pragmatic RESTful design principles by remaining consistently natural, functionally layred, and more importantly least congitive,to insipre your confidence and freedom to explore and use. Gitlapse API design is based on the understanding of the necessity for APIs to appeal to developers` emotion of laziness.

Inorder to inspire ideas of putting together somthing great, Gitlapse API aims to be intuitive, well-documented, and pragrmatically oinionated. Thus as a Developer you can expect predictable, resource-oriented endpoints that uses HTTP response codes. Moreover Gitlapse API supports cross-origin resource sharing, allowing you to interact securely with it, from a client-side web application.


JSON is returned by all API responses, including errors, although our API libraries convert responses to appropriate language-specific objects. Gitlapse API endpoints can be reached via Git itself (Gitlapse Git Extension), cURL(Standard Https), or through Gitlapse`s Ruby SDK (gem install gitlapse).

While posting, git consumers have the option to include a Software License title & url with each lapse.

To keep the simple things simple, while the complex things possible, Gitlapses API offers you two base endpoints per resource, for example for the lapses Resource: 

- `GET http://api.gitlapse.com/v1/lapses/`
- `GET http://api.gitlapse.com/v1/lapses/:SHA`

Add a photo of the two base URLS & the Eight HTTP verbs


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




## Data Policy
Gitlapse data policy dictats that all anonymous lapses are automatically deleted within a max duration of 84hours from their upload, and before that they are only available through their generated SHA links, making them private to you and to those whom you shared the lapse link with.

##Contribute 
You can always <a href='https://github.com/gitlapse/docs'>Contribute to Gitlapse API Interface Design Process</a>, We will be happy to keep tweeking our next API version more & more to your liking!

As much as we are yearning to include more Git Vendors such as Github, Bitbucket, Codeplex, etc. into our API; We are currently hearting this for our next versions of the API.

## IRC 
Join the crowd #gitlapse @freenode. 

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

<aside class="notice">...</aside>

<aside class="success">...</aside>


<aside class="notice">
You must replace <code>username</code> with your personal API key.
</aside>


# Lapses 

## GET /v1/lapses/:username/:repo

`GET http://api.gitlapse.com/v1/lapses/:username/:repo`
### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
username | anonymous | provide a Gitlapse username, anonymous is the default value.
repo 	 | public    | provide a Gitlapse repo name, public is the default value.

### Optional Query Parameters
Parameter | Default | Description
--------- | ------- | -----------
SHA | false | returns a specific lapse via its SHA 
available | true | If set to false, the result will include kittens that have already been adopted.

Return Value | Description
--------- |  -----------
{collection} | Returns a collection of lapses

<aside class="notice">
Fair usage applies 
</aside>

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

## GET /v1/lapses/:username/:repo/:SHA 
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
`GET http://api.gitlapse.com/v1/lapses/:username/:repo/:SHA`

### URL Parameters
Parameter | Default | Description
--------- | ------- | -----------
SHA | false | returns a specific lapse via its SHA 
available | true | If set to false, the result will include kittens that have already been adopted.

### Optional Query Parameters
Parameter | Default | Description
--------- | ------- | -----------
SHA | false | returns a specific lapse via its SHA 
available | true | If set to false, the result will include kittens that have already been adopted.

Return Value | Description
--------- |  -----------
{lapse} | Returns a specific lapses



## POST /v1/lapses/:username/:repo


# Lapses

## GET v1/lapses
### Resource URL 
### Resource Information 
### Parameters 
### Example Request 
### Example Result

## POST v1/lapses
### Resource URL 
### Resource Information 
### Parameters 
### Example Request 
### Example Result

## GET v1/lapses/:id
### Resource URL 
### Resource Information 
### Parameters 
### Example Request 
### Example Result

## DELETE v1/lapses/:id
### Resource URL 
### Resource Information 
### Parameters 
### Example Request 
### Example Result


# Users
## GET v1/users
### Resource URL 


### Resource Information 
### Parameters 
Parameter | Default | Description
--------- | ------- | -----------
username | anonymous | provide a Gitlapse username, anonymous is the default value.
repo 	 | public    | provide a Gitlapse repo name, public is the default value.

### Optional Query Parameters
Parameter | Default | Description
--------- | ------- | -----------
SHA | false | returns a specific lapse via its SHA 
fileds| true | Choose which fileds of the JSON response to retrive back

### Example Request 

### Example Result
Return Value | Description
--------- |  -----------
{collection} | Returns a collection of lapses



## POST v1/users
### Resource URL 
### Resource Information 
### Parameters 
### Example Request 
### Example Result

## GET v1/users/:id
### Resource URL 
### Resource Information 
### Parameters 
### Example Request 
### Example Result

## DELETE v1/users/:id
### Resource URL 
### Resource Information 
### Parameters 
### Example Request 
### Example Result

# Hosts
## GET v1/hosts
### Resource URL 
### Resource Information 
### Parameters 
### Example Request 
### Example Result

## GET v1/hosts/:id
### Resource URL 
### Resource Information 
### Parameters 
### Example Request 
### Example Result

# System
## GET v1/system
### Resource URL 
### Resource Information 
### Parameters 
### Example Request 
### Example Result
