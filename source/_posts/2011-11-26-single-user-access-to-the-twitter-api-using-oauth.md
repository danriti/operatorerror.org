---
title: Single User Access to the Twitter API using OAuth
author: Dan
layout: post
permalink: /2011/11/single-user-access-to-the-twitter-api-using-oauth/
categories:
  - Article
tags:
  - api
  - oauth
  - programming
  - twitter
---
The Twitter API utilizes a [3-legged OAuth][1] authentication process where an authenticated Twitter user can authorize a Twitter-based application to interact with their account and data. This is useful for applications that desire this ability, however what about a Twitter application that doesn&#8217;t care about other users and just wants to get down and dirty with public Twitter data? Thankfully the Twitter API provides a *relatively* easy way to do this!

**NOTE**: This guide assumes you are already familiar with the <a title="Twitter Developers" href="https://dev.twitter.com/" target="_blank">Twitter Developers</a> page and have already registered an application. If you are unfamiliar with either of these concepts, its time to do some <a title="Twitter Developer Documentation" href="https://dev.twitter.com/docs" target="_blank">reading</a>! If you are unsure what type of authentication process is correct for your application, head on over to the <a title="Obtaining Access Tokens" href="https://dev.twitter.com/docs/auth/obtaining-access-tokens" target="_blank">Obtaining Access Tokens</a> article.

If you haven&#8217;t already generated access tokens for your application, follow <a href="https://dev.twitter.com/docs/auth/tokens-devtwittercom" target="_blank">this guide</a>. Now that you have your access tokens, we can get cooking!

Grab the latest version of the <a title="python-oauth2" href="https://github.com/brosner/python-oauth2" target="_blank">python-oauth2</a> library. If you&#8217;re using another language, there might be an OAuth2 library available <a href="https://dev.twitter.com/docs/auth/oauth/single-user-with-examples" target="_blank">here</a>.

<div class="wp_syntax">
  <table>
    <tr>
      <td class="code">
        <pre class="bash" style="font-family:monospace;"><span style="color: #666666;">$ </span><span style="color: #c20cb9; font-weight: bold;">git clone</span> https:<span style="color: #000000; font-weight: bold;">//</span>github.com<span style="color: #000000; font-weight: bold;">/</span>brosner<span style="color: #000000; font-weight: bold;">/</span>python-oauth2.git</pre>
      </td>
    </tr>
  </table>
</div>

Next, we&#8217;re gonna create a new python script called <a href="https://gist.github.com/1667574" target="_blank">twitter.py</a>.



Replace the following with your Twitter application OAuth values:

*   YOUR\_CONSUMER\_KEY
*   YOUR\_CONSUMER\_SECRET
*   YOUR\_ACCESS\_TOKEN
*   YOUR\_ACCESS\_TOKEN_SECRET

Now run the script and you should get the following output:

<div class="wp_syntax">
  <table>
    <tr>
      <td class="code">
        <pre class="bash" style="font-family:monospace;">$ .<span style="color: #000000; font-weight: bold;">/</span>twitter.py
Hourly =<span style="color: #000000; font-weight: bold;">&gt;</span> <span style="color: #000000;">350</span>
Remaining =<span style="color: #000000; font-weight: bold;">&gt;</span> <span style="color: #000000;">350</span></pre>
      </td>
    </tr>
  </table>
</div>

If you got 350 for your hourly limit, then you&#8217;ve successfully authenticated using OAuth (150 is the hourly limit for unauthenticated API requests)!

Now just replace the **rate\_limit\_url** string with another <a href="https://dev.twitter.com/docs/api" target="_blank">Twitter Resource API URI</a> and have fun!

 [1]: https://dev.twitter.com/docs/auth/3-legged-authorization "3-legged OAuth"