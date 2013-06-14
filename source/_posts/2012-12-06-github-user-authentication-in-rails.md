---
title: Github user authentication in Rails
author: Dan Riti
layout: post
permalink: /2012/12/github-user-authentication-in-rails/
categories:
  - Article
tags:
  - api
  - authentication
  - github
  - omniauth
  - programming
  - rails
  - ruby
  - user
---
So you want to authenticate users using the Github API on your next Ruby and Rails project? Using Omniauth this is very easy to accomplish, however I set out to make it even *easier* by building a [Rails skeleton][1] for just this task!

First thing you want to do is [create a new application][2] on Github!

![][3]

Set your **Main** and **Callback** URL accordingly! If you&#8217;re only doing local development for now, then you should be all set using both example URLs.

![][4]

Now that your Github application is created, we need set some environment variables for the **Client ID** and **Client Secret**. You can do this on the command line or place both these values in your ~/.bashrc file.

```bash
$ export GITHUB_KEY="c6e53fab550fd8aa1523"
$ export GITHUB_SECRET="a651c99cb4de311795f924a3209984f1d27628e0"
```

Now we need to clone the project from Github and get it up and running!

```bash
$ git clone git@github.com:notfunk/rails-github-skeleton.git
$ cd rails-github-skeleton
$ bundle install
$ rake db:migrate
$ rails s
```

Now just visit <http://127.0.0.1:3000> in your browser and sign in! Happy hacking.

![][5]

 [1]: https://github.com/notfunk/rails-github-skeleton
 [2]: https://github.com/settings/applications/new
 [3]: http://i.imgur.com/zVBQN.png
 [4]: http://i.imgur.com/aKLZD.png "Hosted by imgur.com"
 [5]: http://i.imgur.com/5GJoO.jpg?1 "Hosted by imgur.com"
