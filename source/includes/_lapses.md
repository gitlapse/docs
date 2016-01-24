# Lapses

## GET v1/lapses
```perl
# Sample Request for Acquiring a Specific Collection of Lapses URLs
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
# Sample Response of Acquiring a Specific Collection of Lapses URLs
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
# Sample Request for Acquiring Lapses URLs of a whole Git Repo branch
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

This endpoint allows you to acquire lapses. 

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
Host      | Optional    | Specify a git host i.e. github, bitbucket, etc.
Username  | Optional    | Specify a username 
Repo 	  | Optional    | Specify a repo name 
Branch 	  | Optional    | Specify a branch in the repo 
SHAs	  | Optional 	| Specify a collection of SHAs
Fields	  | Optional    | Selects which fields of the JSON response to acquire back


## GET v1/lapses/:SHA

```perl
# Sample Request for Acquiring a Specific Lapse URL via its SHA
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

This endpoint allows you to acquire a specific lapse URL via its SHA. 
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
Fields	  | Optional    | Selects which fields of the JSON response to acquire back


## POST v1/lapses

git lapse fileA, fileB, fileC 

This endpoint allows you to store a collection of lapses 
### Resource URL 
POST `https://api.gitlapse.com/v1/lapses/:SHA`

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
Fields	  | Optional    | Selects which fields of the JSON response to acquire back


## POST v1/lapses/:SHA
### Resource URL 
### Resource Information 
git lapse fileA, fileB, fileC 
### Parameters 
