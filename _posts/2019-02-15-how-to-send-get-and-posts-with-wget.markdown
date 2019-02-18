---
layout: post
title:  "How to send GET and POST requests with wget?"
date:   2019-02-15 15:44:00 +0100
categories: jekyll update blogging linux
tags: [tips,tricks,wget]
---


* GET request 

```
wget -S --header="Accept-Encoding: gzip, deflate" -O response.txt http://server:8080/application/params

```

* POST request 

```
wget -S --header="Accept-Encoding: gzip, deflate" --header='Accept-Charset: UTF-8' --header='Content-Type: application/json' -O response.json --post-data '{"param1":"myspecialValue1","param2":"my special value 2"}' http://server:8080/application2/params2

```

This post duplicates [post from wordpress blog](https://jacekkowalczyk.wordpress.com/2013/04/10/how-to-send-get-and-post-request-with-wget/)
