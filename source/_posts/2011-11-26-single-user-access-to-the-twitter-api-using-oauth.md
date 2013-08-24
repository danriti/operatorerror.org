---
title: Single User Access to the Twitter API using OAuth
author: Dan Riti
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

```bash
$ git clone https://github.com/brosner/python-oauth2.git
```

Next, we&#8217;re gonna create a new python script called <a href="https://gist.github.com/1667574" target="_blank">twitter.py</a>.

```python twitter_api.py https://gist.github.com/danriti/1667574#file-twitter_api-py View Gist
#!/usr/bin/python

import simplejson as json

import oauth2 as oauth

# Create your consumer with the proper key/secret.
consumer = oauth.Consumer(key="YOUR_CONSUMER_KEY",
                          secret="YOUR_CONSUMER_SECRET")

# Create your token with the proper key/secret.
token = oauth.Token(key="YOUR_ACCESS_TOKEN",
                    secret="YOUR_ACCESS_TOKEN_SECRET")

# Request token URL for Twitter.
rate_limit_url = "http://api.twitter.com/1/account/rate_limit_status.json"

# Create our client.
client = oauth.Client(consumer, token)

# The OAuth Client request works just like httplib2 for the most part.
resp, content = client.request(rate_limit_url, "GET")

# Parse the JSON into a Python dictionary.
data = json.loads(content)

# Print hourly limits.
print "Hourly    => %3d" % (data['hourly_limit'])
print "Remaining => %3d" % (data['remaining_hits'])
```

Replace the following with your Twitter application OAuth values:

-  YOUR\_CONSUMER\_KEY
-  YOUR\_CONSUMER\_SECRET
-  YOUR\_ACCESS\_TOKEN
-  YOUR\_ACCESS\_TOKEN_SECRET

Now run the script and you should get the following output:

```bash
$ ./twitter.py
Hourly => 350
Remaining => 350
```

If you got 350 for your hourly limit, then you&#8217;ve successfully authenticated using OAuth (150 is the hourly limit for unauthenticated API requests)!

Now just replace the **rate\_limit\_url** string with another <a href="https://dev.twitter.com/docs/api" target="_blank">Twitter Resource API URI</a> and have fun!

 [1]: https://dev.twitter.com/docs/auth/3-legged-authorization "3-legged OAuth"
