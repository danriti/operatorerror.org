---
title: Find is Your Friend
author: Dan
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

<div class="wp_syntax">
  <table>
    <tr>
      <td class="code">
        <pre class="bash" style="font-family:monospace;"><span style="color: #666666;">$ </span><span style="color: #c20cb9; font-weight: bold;">find</span> . <span style="color: #000000; font-weight: bold;">|</span> <span style="color: #c20cb9; font-weight: bold;">xargs</span> <span style="color: #c20cb9; font-weight: bold;">grep</span> <span style="color: #ff0000;">'searchString'</span></pre>
      </td>
    </tr>
  </table>
</div>

Find a string in all files but only list the file names (note the &#8216;-sl&#8217; flag):

<div class="wp_syntax">
  <table>
    <tr>
      <td class="code">
        <pre class="bash" style="font-family:monospace;"><span style="color: #666666;">$ </span><span style="color: #c20cb9; font-weight: bold;">find</span> . <span style="color: #000000; font-weight: bold;">|</span> <span style="color: #c20cb9; font-weight: bold;">xargs</span> <span style="color: #c20cb9; font-weight: bold;">grep</span> <span style="color: #ff0000;">'searchString'</span> <span style="color: #660033;">-sl</span></pre>
      </td>
    </tr>
  </table>
</div>

Find a string in only C headers:

<div class="wp_syntax">
  <table>
    <tr>
      <td class="code">
        <pre class="bash" style="font-family:monospace;"><span style="color: #666666;">$ </span><span style="color: #c20cb9; font-weight: bold;">find</span> . <span style="color: #660033;">-name</span> <span style="color: #ff0000;">"*.h"</span> <span style="color: #000000; font-weight: bold;">|</span> <span style="color: #c20cb9; font-weight: bold;">xargs</span> <span style="color: #c20cb9; font-weight: bold;">grep</span> <span style="color: #ff0000;">'searchString'</span></pre>
      </td>
    </tr>
  </table>
</div>

Enjoy!