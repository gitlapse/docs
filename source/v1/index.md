---
title: GitLapse API Reference

language_tabs:
  - c: Git 
  - ruby: Ruby
  - shell: cURL 

toc_footers:
   - API v1 Status <div class="led-red" markdown="1"></div><div class="led-green" markdown="1"></div> 
   - <a href='http://gitlapse.com'> © gitlapse 2016 </a><a href='http://gitlapse.com/terms'> Terms </a>
  
includes:
  - errors

search: true
---


# API v1 Reference 
Gitlapse API v1 lets you build Consumer apps on top of Gitlapse. 

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
curl -v -H "Accept: application/json" -H "Content-type: application/json" -X POST -d '{:SHA => blob_sha_value, :content => blob_content_value}' http://api.gitlapse.com/v1/lapses
```
```ruby
gem install gitlapse
```
You can install gitlapse on your system either from curl or gem.

`gem install gitlapse`
### copy\paste this oneline of code into your terminal

curl "http://api.gitlapse.com/v1/lapses/:SHA"
anonymous is the shared username
repo is name of the git directory


## Philosophy 

Gitlapse API design is based on the understanding of the necessity for APIs to appeal to developers` emotion of laziness while building API consumer applications. Developers are encouraged to expect predictable, resource-oriented endpoints. 

Gitlapse delivers affordance via:

* Remaining functionally minimal and least cognitive. 
* Implementing a high scope mandatory versioning with whole numbers, v1, v2, v3, etc. to interface with the Gitlapse backends. 
	* Gitlapses API adopts the standard of offering two base endpoints per resource, For example for the `lapses` Resource, Develoeprs can set their expectations to find: 
		* `POST http://api.gitlapse.com/v1/lapses/`
		* `POST http://api.gitlapse.com/v1/lapses/:SHA`
		* `GET  http://api.gitlapse.com/v1/lapses/`
		* `GET  http://api.gitlapse.com/v1/lapses/:SHA`

* Supporting cross-origin resource sharing, allowing you to interact securely with it, from a client-side web-based applications.
* All API endpoints are conveniently reachable over HTTPS via git extensions, cURL, and SDKs through COPY\PASTE examples.
* All API respones - including errors - are returned in the JSON format -along with standard HTTP Status codes - that is easily digested by consumer applications. 
* All error responses return most relevant links to the documentation and keywords for IRC #channel help. 

## Data Policy
Gitlapse data policy dictats that all anonymous lapses are automatically deleted within a max duration of 84hours from their upload, and before that they are only available through their generated SHA links, making them private to you and to those whom you shared the lapse link with.

##Contribute 
You can always <a href='https://github.com/gitlapse/docs'>Contribute to Gitlapse API Interface Design Process</a>, We will be happy to keep tweeking our next API version more & more to your liking!

As much as we are yearning to include more Git Vendors such as Github, Bitbucket, Codeplex, etc. into our API; We are currently hearting this for our next versions of the API.

## IRC 
Join the crowd #gitlapse @freenode. 

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
