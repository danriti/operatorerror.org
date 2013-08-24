---
title: Get a Facebook API Access Token that Never Expires
author: Dan
layout: post
permalink: /2011/07/get-a-facebook-api-access-token-that-never-expires/
comments: true
categories:
  - Article
tags:
  - api
  - facebook
  - oauth
  - programming
---
<p><strong>UPDATE</strong> (02/08/2013): Facebook has <a href="https://developers.facebook.com/roadmap/offline-access-removal/" target="_blank">deprecated</a> the <strong>offline_access</strong> token, so this method no longer works! See this post on <a href="http://stackoverflow.com/questions/10467272/get-long-live-access-token-from-facebook" target="_blank">Stack Overflow</a> to learn how to extend an access token to 60 days.</p>
<p>I&#8217;ve been working on a few scripts that performed some minor data collection using the Facebook Graph API as a data source. Ideally, I wanted this script to be able to run several times a day automatically, however Facebook grants access tokens that expire after 1-2 hours. Since I&#8217;m the only one that is going to run this script, I only needed access to <em>my</em> Facebook data and I didn&#8217;t want to have to re-authenticate every few hours. Luckily, Facebook provides a permission parameter to get a &#8220;long-lived&#8221; access token from Oauth called <strong>offline_access</strong>!</p>
<p><strong>NOTE:</strong> If you&#8217;re unfamiliar with the <a href="https://developers.facebook.com/docs/authentication/">Facebook API authentication process</a>, I suggest you brush up before continuing!</p>
<p>Below is an example of the permission parameter you would pass to the Oauth dialog to let Facebook know you don&#8217;t want some wimpy access token, but one that will last much longer!</p>
<blockquote><p>https://www.facebook.com/dialog/oauth?<br />
client_id=YOUR_APP_ID&amp;redirect_uri=YOUR_URL&amp;<strong>scope=offline_access</strong></p></blockquote>
<p>Then just follow the rest of the Facebook authentication process normally and you should be set!</p>
<p>From the <a href="https://developers.facebook.com/docs/reference/api/permissions/">Facebook Permissions Reference</a>:</p>
<blockquote><p><strong>offline_access</strong> &#8211; Enables your app to perform authorized requests on behalf of the user at any time. By default, most access tokens expire after a short time period to ensure applications only make requests on behalf of the user when the are actively using the application. This permission makes the access token returned by our OAuth endpoint long-lived.</p></blockquote>
<p>However, if you&#8217;re feeling <em>extra</em> lazy, you could always generate an <strong>offline_access</strong> access token using the <a href="https://developers.facebook.com/tools/explorer">Graph API Explorer</a>!</p>
<ul>
<li>Head on over to the <a href="https://developers.facebook.com/tools/explorer">Graph API Explorer</a></li>
<li>Click the <strong>Get Access Token</strong> button</li>
<li>Select the <strong>Extended Permissions</strong> tab</li>
<li>Check the <strong>offline_access</strong> box</li>
<li>Click the <strong>Get Access Token</strong> button!</li>
</ul>
<p><a href="http://i.imgur.com/kHObm.png"><img src="http://i.imgur.com/kHObm.png" alt="Facebook Graph API Explorer permissions" /></a></p>
<p>Now just grab your newly generated access token and get to work!</p>
