---
title: Find is Your Friend
author: Dan Riti
layout: post
permalink: /2010/09/find-is-your-friend/
categories:
  - Article
tags:
  - command line
  - programming
---
Searching for files using *find* on the command line is a powerful tool that most developers should be familiar with. Searching for strings inside files using *grep* can be even more useful for developers, especially if you are working in a unfamiliar code base.

While both these commands are great to use individually, they really start to shine when you combine the two. This union of forces will enable one to search recursively through folders checking for substrings in all files. Behold, the power of *find* and *grep*!

Find a string in all files and list the results:

```bash
$ find . | xargs grep 'searchString'
```

Find a string in all files but only list the file names (note the &#8216;-sl&#8217; flag):

```bash
$ find . | xargs grep 'searchString'
```

Find a string in only C headers:

```bash
$ find . -name "*.h" | xargs grep 'searchString'
```

Enjoy!
