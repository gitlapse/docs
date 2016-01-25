# Bittorrents
## GET v1/bittorrents/:repo

```perl
# Sample Request for Listing a Specific Repo tracker URL 
```
```c
```
```shell
```
```ruby
require 'gittracker'
bittracker_url = Gitlapse.tracker(SHA)
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
  "tracker":{
    "SHA": "bigsha",
    "content": "tracker_content",
    "url": "https://gittracker.com?SHA='bigsha'"
  }
}
```

This endpoint allows you to show a specific tracker URL via its SHA. 
### Resource URL 
GET `https://api.gittracker.com/v1/lapses/:SHA`

### Resource Information 
Info				| Value           	 
--------- 			| ------- 
Response formats		| JSON 
Requires authentication?    	| False 

### Parameters 
Parameter |     Type	| Description
--------- | ------- 	| -----------
SHA 	  | Required    | Specify a SHA of a tracker 
Host      | Optional    | Specify a git host i.e. github, bitbucket, etc.
Username  | Optional    | Specify a username 
Repo 	  | Optional    | Specify a repo name 
Branch 	  | Optional    | Specify a branch in the repo 
Fields	  | Optional    | Selects which fields of the JSON response to list back


