---
layout: post
title: My blogging platform and workflow
date: 2019-06-05 12:09 +0200
categories: update manuals blogging
tags: [freebsd,blogging,jekyll,markdown,wordpress,tools]

---

I was asked to write something how I am doing my blogging. 

Here it is :-) 

## My blogging story 

I started with some blogs at blogspot.com, later on I switched to wordpress.com and created this [blog](https://jacekkowalczyk.wordpress.com/). 
Few years ago I started using [markdown](https://daringfireball.net/projects/markdown/) as my main notation for making documentation and notes in work and in private live. 

Few months ago I heard about the [Jekyll](https://jekyllrb.com/) which is the recommended framework for [GitHub Pages](https://pages.github.com/). 

I installed Jekyll and created  this blog page (at FreeBSD) . 

```
sudo pkg install ruby ruby26-gems
sudo gem install bundler jekyll

jekyll new jacekkowalczyk82.github.io

cd jacekkowalczyk82.github.io
bundle install 
```

## My platform

* Operating system: [FreeBSD 12](https://www.freebsd.org/)
* Editors: [ghostwriter](https://wereturtle.github.io/ghostwriter/), [geany](https://www.geany.org/), nano, vim. 
* [Jekyll](https://jekyllrb.com/)

If you would like more details about how I setup the jekyll at FreeBSD you can check this [notes](https://gitlab.com/jacekkowalczyk82/freebsd/blob/master/blogging/README.md). 

## My workflow 

* I start usually with making some markdown notes. 
* When I decide that the topic and notes are complete I start new post in my blog repository 

```
cd jacekkowalczyk82.github.io
bundle exec jekyll post "My blogging platform and workflow" 

```

* I edit the new generated post file with editor and write with markdown :-) 

* I am checking the resulting blog post with jekyll development server and web browser pointed to `http://localhost:4000/`:

```
bundle exec jekyll serve

```

* When post is ready I commit it to my github blog repo.

* Finally I am creating new post at my wordpress blog and adding link to the new github blog post. 

* That is it. End of story :-) 

## No, no, not the end - UPDATE

My blogging platform is still jekyll but I am doing it from many machines and OSs: Ubuntu, Antix, OpenBSD. 

### Install development environment for blogging with jekyll on OpenBSD

```
sudo pkg_add ruby


sudo gem27 install bundler jekyll
#gem27 install bundler jekyll
cd <jekyll blog repository>
bundle27 config set path 'vendor/bundle'
bundle27 install
bundle27 exec jekyll serve

# diff tool 
sudo pkg_add kompare 

```

