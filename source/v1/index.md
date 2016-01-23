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
