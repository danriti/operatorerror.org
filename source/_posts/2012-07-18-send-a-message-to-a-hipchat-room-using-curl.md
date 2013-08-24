---
title: Send a message to a HipChat Room using cURL
author: Dan Riti
layout: post
permalink: /2012/07/send-a-message-to-a-hipchat-room-using-curl/
categories:
  - Article
tags:
  - bash
  - collaboration
  - command line
  - curl
  - hipchat
  - programming
---
If you are unfamiliar with [HipChat][1], its a persistent chat room used for team collaboration. With its abundance of features, one that stands out is the ability to utilize the [HipChat API][2] to send notifications messages to your team rooms. Notifications are great for letting everyone on your team know an event of significance has occurred. Examples include commits to your source code repository, continuous integration results, or when an extremely angry user adds a new issue to the bug tracker.

![Build passes!][3]

While many web based services offer hooks to make sending notification message to HipChat easy (such as [Github][4]), what if you want to send a notification from an existing Bash script that you use everyday? Well you&#8217;re in luck, because the HipChat API makes this extremely easy to do using [cURL][5]!

**NOTE:** If you haven&#8217;t generated a HipChat API Token yet, learn to do so [here][6].

```bash hipchat.sh https://gist.github.com/danriti/3095606#file-hipchat-sh View Gist
# Build Passes
curl -d "room_id=ourRoom&from=BuildBot&message=Build+Status:+Passing&color=green" https://api.hipchat.com/v1/rooms/message?auth_token=AUTH_TOKEN_HERE&format=json

# Build Fails
curl -d "room_id=ourRoom&from=BuildBot&message=Build+Status:+Failing&color=red&notify=1" https://api.hipchat.com/v1/rooms/message?auth_token=AUTH_TOKEN_HERE&format=json
```

**NOTE:** Make sure to change the parameters to fit your application and insert your authentication token!

HipChat API notification messages have some neat features, such as *colors* and *notify*. This makes it easy making it easy to instantly indicate to your team via HipChat if something erroneous has occurred (such as failed unit tests).

Be sure to check out the full HipChat API documentation for [sending messages to rooms][7].

 [1]: https://www.hipchat.com/
 [2]: https://www.hipchat.com/docs/api/
 [3]: http://i.imgur.com/oypCa.png
 [4]: https://github.com/
 [5]: http://curl.haxx.se/
 [6]: https://www.hipchat.com/docs/api/auth
 [7]: https://www.hipchat.com/docs/api/method/rooms/message
