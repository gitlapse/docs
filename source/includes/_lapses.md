# Lapses

## GET v1/lapses
```perl
# Sample Request for Listing a Specific Collection of Lapses URLs
```
```c
git lapse path/fileA, path/fileB, path/fileC

git lapse SHA_A, SHA_B, SHA_C
```
```shell

curl -v -H "Accept: application/json" -H "Content-type: application/json" -X  https://api.gitlapse.com/v1/lapses?SHAs="d670460b4b4aece5915caf5c68d12f560a9fe3e4,d670460b4b4aece5915caf5c68d12f560a9fe3e4,d670460b4b4aece5915caf5c68d12f560a9fe3e4"`
```

```ruby
# Make sure you run `gem install gitlapse` or Add gitlapse to your Bundler Gemfile before executing this code!

require 'gitlapse'
Gitlapse.lapses(blobs=["path/fileA", "path/fileB"])
```

```perl
# Sample Response of Listing a Specific Collection of Lapses URLs
```

```json
{ "user_info": {},
  "repo_info": {},
  "lapses":{
    "lapse":{
      "SHA": "zSHA",
      "content": "lapse_content",
      "URL": "https://gitlapse.com/SHA?zSHA"
    },
    "lapse":{
      "SHA": "zSHA",
      "content": "lapse_content",
      "URL": "https://gitlapse.com/SHA?zSHA"

    }
  }
}
```

```perl
# Sample Request for Listing Lapses URLs of a whole Git Repo branch
```
```c
git lapse master, ["path/fileA", "path/fileB"]

```
```shell
curl -v -H "Accept: application/json" -H "Content-type: application/json" -X  https://api.gitlapse.com/v1/lapses?repo="myrepo",branch="master"
```
```ruby
# Make sure you run `gem install gitlapse` or Add gitlapse to your Bundler Gemfile before executing this code!
require 'gitlapse'
Gitlapse.lapses(repo="path/myrepo",branch="master")
```

```perl
# Sample Response
```
```json
{ "user_info": {
  "username":"zotherstupidguy",
    "about":"someone who cares"
	       },
  "repo_info": {},
  "lapses":{
    "lapse":{
      "SHA": "big sha",
      "content": "lapse_content",
      "url": "url"
    },
    "lapse":{
      "SHA": "big sha",
      "content": "lapse_content",
      "url": "url"
    },
    "lapse":{
      "SHA": "big sha",
      "content": "lapse_content",
      "url": "url"
    }
  }
}
```

This endpoint allows you to list lapses. 

### Resource URL 
GET `https://api.gitlapse.com/v1/lapses`
### Resource Information 

Info				| Value           	 
--------- 			| ------- 
Response formats		| JSON 
Requires authentication?    	| False 


### Parameters 
Parameter |     Type	| Description
--------- | ------- 	| -----------
Host      | Optional    | Specify a git host i.e. github, bitbucket, private, etc.
Username  | Optional    | Specify a username 
Repo 	  | Optional    | Specify a repo name 
Branch 	  | Optional    | Specify a branch in the repo 
SHAs	  | Optional 	| Specify a collection of SHAs
Fields	  | Optional    | Selects which fields of the JSON response to list back


## GET v1/lapses/:SHA

```perl
# Sample Request for Listing a Specific Lapse URL via its SHA
```
```c
git lapse sample.rb
```
```shell
curl -v -H "Accept: application/json" -H "Content-type: application/json" -X  https://api.gitlapse.com/v1/lapses/:SHA
```
```ruby
require 'gitlapse'
mylapse_url = Gitlapse.get(SHA)
```
```perl
# Sample Response
```
```json
{ "user_info": {
  "username":"zotherstupidguy",
    "about":"someone who cares"
	       },
  "repo_info": {},
  "lapse":{
    "SHA": "bigsha",
    "content": "lapse_content",
    "url": "https://gitlapse.com?SHA='bigsha'"
  }
}
```

This endpoint allows you to show a specific lapse URL via its SHA. 
### Resource URL 
GET `https://api.gitlapse.com/v1/lapses/:SHA`

### Resource Information 
Info				| Value           	 
--------- 			| ------- 
Response formats		| JSON 
Requires authentication?    	| False 

### Parameters 
Parameter |     Type	| Description
--------- | ------- 	| -----------
SHA 	  | Required    | Specify a SHA of a lapse 
Host      | Optional    | Specify a git host i.e. github, bitbucket, etc.
Username  | Optional    | Specify a username 
Repo 	  | Optional    | Specify a repo name 
Branch 	  | Optional    | Specify a branch in the repo 
Fields	  | Optional    | Selects which fields of the JSON response to list back


## POST v1/lapses

```perl
# Sample Request for Creating a New Lapse
```
```c
git lapse fileA
```
```shell
curl -v -H "Accept: application/json" -H "Content-Type: application/json" -X POST -d '{ "host":"host", "username":"zotherstupidguy" ,"lapse": {"SHA":"bigsha","content":"blobcontent"}' https://api.gitlapse.com/v1/lapses
```
```ruby
require 'gitlapse'

lapse 		= {"SHA", "blobcontent"}
mylapse_url 	= Gitlapse.post(lapse: lapse)

# Optionally you can include various repo & user information such as reponame, host, username, api-key, etc. 
repo	 	= "hackspree"
host  		= "github"
username 	= "zotherstupidguy"
key	 	= "ageneratedrandomsomeapikey"

Gitlapse.post(api_key: key, repo_info: repo, user_info: username, lapse: lapse)
```
```perl
# Sample Response
```
```json
{ "user_info": {
  "username":"zotherstupidguy",
    "about":"someone who cares"
	       },
  "repo_info": {},
  "lapse":{
    "SHA": "bigsha",
    "content": "lapse_content",
    "url": "https://gitlapse.com?SHA='bigsha'"
  }
}
```

This endpoint allows you to create a new lapse
### Resource URL 
POST `https://api.gitlapse.com/v1/lapses`

### Resource Information 
Info				| Value           	 
--------- 			| ------- 
Response formats		| JSON 
Requires authentication?    	| False 

### Parameters 
Parameter |     Type	| Description
--------- | ------- 	| -----------
Lapse     | Required    | Specify a new lapses(SHA & blob content)
Host      | Optional    | Specify a git host i.e. github, bitbucket, private, etc.
Username  | Optional    | Specify a username 
Repo 	  | Optional    | Specify a repo name 
Branch 	  | Optional    | Specify a branch in the repo 


## DELETE v1/lapses/:SHA

```perl
# Sample Request for Deleting a Lapse
```
```c
git lapse fileA
```
```shell
curl -v -H "Accept: application/json" -H "Content-Type: application/json" -X POST -d '{ "host":"host", "username":"zotherstupidguy" ,"lapse": {"SHA":"bigsha","content":"blobcontent"}' https://api.gitlapse.com/v1/lapses
```
```ruby
require 'gitlapse'

SHA		= "bigsha"
mylapse_url 	= Gitlapse.del(SHA: SHA)

# Optionally you can include various repo & user information such as reponame, host, username, api-key, etc. 
repo	 	= "hackspree"
host  		= "github"
username 	= "zotherstupidguy"
key	 	= "ageneratedrandomsomeapikey"

Gitlapse.del(api_key: key, repo_info: repo, user_info: username, SHA: SHA)
```
```perl
# Sample Response
```
```json
{ "user_info": {
  "username":"zotherstupidguy",
    "about":"someone who cares"
	       },
  "repo_info": {},
  "lapse":{
    "SHA": "bigsha",
    "content": "lapse_content",
    "url": "https://gitlapse.com?SHA='bigsha'"
  }
}
```

This endpoint allows you to delete a lapse via its SHA 
### Resource URL 
DELETE `https://api.gitlapse.com/v1/lapses/:SHA`

### Resource Information 
Info				| Value           	 
--------- 			| ------- 
Response formats		| JSON 
Requires authentication?    	| False 

### Parameters 
Parameter |     Type	| Description
--------- | ------- 	| -----------
SHA       | Required    | Specify a SHA of a lapse 
Host      | Optional    | Specify a git host i.e. github, bitbucket, private, etc.
Username  | Optional    | Specify a username 
Repo 	  | Optional    | Specify a repo name 
Branch 	  | Optional    | Specify a branch in the repo 
