---
layout: post
title: Basic vimrc configuration for Vim
date: 2021-02-25 12:20 +0100
categories: update manuals tools
tags: [vim,vimrc,linux,bsd]
---

Vim is one of the most popular and powerful terminal-based editor. 

Here is some very basic .vimrc configuration example file, that I created: 

```
"   The MIT License (MIT)
"   Copyright (c) 2021-present Jacek Kowalczyk jacekkowalczyk82@gmail.com
"   
"   Permission is hereby granted, free of charge, to any person obtaining a copy
"   of this software and associated documentation files (the "Software"), to deal
"   in the Software without restriction, including without limitation the rights
"   to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
"   copies of the Software, and to permit persons to whom the Software is
"   furnished to do so, subject to the following conditions:
"   
"   The above copyright notice and this permission notice shall be included in
"   all copies or substantial portions of the Software.
"   
"   THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
"   IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
"   FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
"   AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
"   LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
"   OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
"   THE SOFTWARE.
"   
"   This is my very first .vimrc file
"   
" Enable line numbers
set number

" Display the line number, the column number, the virtual column number, and the relative position of the cursor in the file (as a percentage)
set ruler

" Enable syntax highlighting
if has('syntax')
  syntax on
endif

" Select color scheme
color industry



```
