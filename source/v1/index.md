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
Crafting software is a crucial human endeavor, at its core it is a synthesis of writing and reading sourcecode. Gitlapse improves the software reading experiance by converting sourcecode text files into watchable videos. Gitlapse API v1 lets you build exciting Consumer Apps on top of Gitlapse. 

Note: API v1 doesn`t require authentication, yet fair usage apply. 

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
* All API respones including errors  are returned in the JSON format by default, along with standard HTTP Status codes that is easily digested by consumer applications. 
* All error responses return most relevant links to the documentation and keywords for IRC #channel help. 

## Data Policy
Gitlapse data policy dictats that all unauthenticated lapses are automatically deleted within a max duration of 84hours from their upload, and before that they are only available through their generated SHA links, making them private to you and to those whom you had shared the lapse link with.

##Contribute 
You can always <a href='https://github.com/gitlapse/docs'>Contribute to Gitlapse API Interface Design</a>, We love to keep tweeking our next API version more & more to your liking! And as much as we are yearning to support more Git hosts such as Github, Bitbucket, Codeplex, etc. We are currently hearting this to our upcoming versions of the API.

## IRC 
Join the crowd #gitlapse @freenode. 

# Lapses

## GET v1/lapses
This endpoint allows you to acquire lapses in bulk.

```c
git lapse fileA, fileB, fileC 
```
```shell
# Using cURL 
curl https://api.gitlapse.com/v1/lapses?SHAs="d670460b4b4aece5915caf5c68d12f560a9f3333, d670460b4b4aece5915caf5c68d12f560a9f4444, d670460b4b4aece5915caf5c68d12f560a9f6666"
```
```ruby
# Example Request 
`GET https://api.gitlapse.com/v1/lapses?SHAs="d670460b4b4aece5915caf5c68d12f560a9fe3e4,d670460b4b4aece5915caf5c68d12f560a9fe3e4,d670460b4b4aece5915caf5c68d12f560a9fe3e4"`

gem install gitlapse
```
```json
{
  "glossary": {
    "title": "example glossary",
      "GlossDiv": {
	"title": "S",
	"GlossList": {
	  "GlossEntry": {
	    "ID": "SGML",
	    "SortAs": "SGML",
	    "GlossTerm": "Standard Generalized Markup Language",
	    "Acronym": "SGML",
	    "Abbrev": "ISO 8879:1986",
	    "GlossDef": {
	      "para": "A meta-markup language, used to create markup languages such as DocBook.",
	      "GlossSeeAlso": ["GML", "XML"]
	    },
	    "GlossSee": "markup"
	  }
	}
      }
  }
}
```



### Resource URL 
`https://api.gitlapse.com/v1/lapses`
### Resource Information 

Info				| Value           	 
--------- 			| ------- 
Response formats		| JSON 
Requires authentication?    	| False 

curl -v -H "Accept: application/json" -H "Content-type: application/json" -X POST -d '{:SHA => blob_sha_value, :content => blob_content_value}' https://api.gitlapse.com/v1/lapses

### Parameters 
Parameter |     Type	| Description
--------- | ------- 	| -----------
Repo 	  | Required    | Specify a repo name 
Branch 	  | Required    | Specify a branch in the repo 
SHAs	  | Optional 	| Specify a collection of SHAs
Fields	  | Optional    | Selects which fields of the JSON response to retrive back




<!---
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
-->
