---
layout: post
title: How to convert markdown to html pdf pptx with pandoc
date: 2019-03-20 14:56 +0100

categories: update manuals tools
tags: [tips,tricks,markdown,pandoc]

---


I started using markdown few years ago. I loved it so much that right now I am using it at work for writing my notes, manuals and other documentation. Recently I discovered I can write ebooks (epub, mobi, pdf ) with markdown and more over I can create presentations with markdown and convert them to the HTML with slides, PDF, Microsoft PowerPoint pptx. 

All you need is: markdown or plain text editor, and [pandoc tool](https://pandoc.org/). 

Lets create a markdown document test-pandoc.md: 

```

% Sample Test Document for testing pandoc tool
% User Name
% March 20, 2019

--- 


## Lists

* item1 
* item2 

## Lorem ipsum 

> "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent nec venenatis nunc. Quisque eget nunc a lacus dictum tincidunt. Integer libero ex, aliquam ac hendrerit quis, luctus eu nisl. Pellentesque ultricies vulputate sollicitudin. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Suspendisse potenti. Praesent ac diam ex. Nunc finibus magna nec nisi aliquet, in maximus ligula elementum. Mauris fermentum tellus at malesuada ultrices."

## Tables

| Head 1 | Head 2 |
|--------|--------|
| value 1| value 2|
| value 3| value 4|


```


Secondly lets install all required software: ( FreeBSD way :-) )

```
pkg install hs-pandoc 

#Pandoc by default is using latex to create PDF files. 
pkg install tex-formats texlive-full 


```

Now you can generate your presentation PDF,PPTX, or plain PDF, HTML files: 

```
pandoc test-pandoc.md -s --wrap auto -o test-pandoc-plain.pdf
pandoc test-pandoc.md -f markdown -t html -s -o test-pandoc-plain.html 

pandoc test-pandoc.md -i -t beamer -s --wrap auto --slide-level 2 -o test-pandoc-slides.pdf 
pandoc test-pandoc.md -s --wrap auto -o test-pandoc-slides.pptx 

```


If you want to create HTML presentation you can use reveal.js framework. Download it and unpack to the directory ./reveal.js and run pandoc:

```
pandoc test-pandoc.md -s -i --mathjax -t revealjs -V theme=white --self-contained --slide-level 2 -o test-pandoc-slides.html 

```


