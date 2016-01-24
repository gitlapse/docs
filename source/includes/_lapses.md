# Lapses

## GET v1/lapses
```perl
# Sample Request for Acquiring a Specific Collection of Lapses 
```
```c
git lapse path/file1, path/file2, path/file3

git lapse master, ["path/file1", "path/file2"]
```
```shell
curl -v -H "Accept: application/json" -H "Content-type: application/json" -X  https://api.gitlapse.com/v1/lapses?repo="myrepo",branch="master"

curl -v -H "Accept: application/json" -H "Content-type: application/json" -X  https://api.gitlapse.com/v1/lapses?SHAs="d670460b4b4aece5915caf5c68d12f560a9fe3e4,d670460b4b4aece5915caf5c68d12f560a9fe3e4,d670460b4b4aece5915caf5c68d12f560a9fe3e4"`
```

```ruby
# Make sure you run `gem install gitlapse` or Add gitlapse to your Gemfile

require 'gitlapse'
Gitlapse.lapses(repo="path/myrepo",branch="master", lapses=["path/file1", "path/file2"])
Gitlapse.lapses(repo="path/myrepo",branch="master")
```

```perl
# Sample Response of Acquiring a Specific Collection of Lapses 
```

```json
{ "user_info": {},
  "repo_info": {},
  "lapses":{
    "lapse":{
      "SHA": "big sha",
      "content": "content"
    },
    "lapse":{
      "SHA": "big sha",
      "content": "content"
    },
    "lapse":{
      "SHA": "big sha",
      "content": "content"
    }
  }
}
```

```c
git lapse post  
```
```shell
curl -v -H "Accept: application/json" -H "Content-type: application/json" -X  https://api.gitlapse.com/v1/lapses?repo="myrepo",branch="master"
```
```ruby
require 'gitlapse'
Gitlapse.lapses(repo="myrepo",branch="master")
`
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
      "content": "content"
    },
    "lapse":{
      "SHA": "big sha",
      "content": "content"
    },
    "lapse":{
      "SHA": "big sha",
      "content": "content"
    }
  }
}
```

This endpoint allows you to acquire lapses. 

### Resource URL 
`https://api.gitlapse.com/v1/lapses`
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
# Sample Request using get a Lapse via its SHA 
```
```c
git lapse sample.rb
```
```shell
curl -v -H "Accept: application/json" -H "Content-type: application/json" -X  https://api.gitlapse.com/v1/lapses/:SHA
```
```ruby
require 'gitlapse'
mylapse = Gitlapse.get(SHA)
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
    "content": "content"
  }
}
```

This endpoint allows you to acquire a specific lapse via its SHA. 
### Resource URL 
`https://api.gitlapse.com/v1/lapses/:SHA`

### Resource Information 
Info				| Value           	 
--------- 			| ------- 
Response formats		| JSON 
Requires authentication?    	| False 

### Parameters 
Parameter |     Type	| Description
--------- | ------- 	| -----------
SHA 	  | Required    | Specify a SHA of a lapse 
Repo 	  | Optional    | Specify a repo name 
Branch 	  | Optional    | Specify a branch in the repo 
Fields	  | Optional    | Selects which fields of the JSON response to acquire 

## POST v1/lapses
### Resource URL 
### Resource Information 
git lapse fileA, fileB, fileC 
### Parameters 
### Sample Request 
### Sample Result

## POST v1/lapses/:SHA
### Resource URL 
### Resource Information 
git lapse fileA, fileB, fileC 
### Parameters 
