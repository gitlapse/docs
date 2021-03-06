# API v1 Reference 

```c
git lapse path/to/your/git/file.rb
```

```shell
# With shell, you can just pass the correct header with each request
curl -v -H "Accept: application/json" -H "Content-type: application/json" -X POST -d '{:SHA => blob_sha_value, :content => blob_content_value}' http://api.gitlapse.com/v1/lapses
```

```ruby
gem install gitlapse
```

Crafting software is a crucial human endeavor, at its core it is a synthesis of writing and reading sourcecode. Gitlapse improves the software reading experiance by converting sourcecode text files into interactive videos. Gitlapse API v1 lets you build exciting Consumer Apps on top of Gitlapse. 

Note: API v1 doesn`t require authentication, yet fair usage apply. 

## Quickstart
add this quickstart section to the main homepage of the beta and remove launching soon
### Installation 

> first, run gem install gitlapse
> if you are using rbenv, run rbenv rehash


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
