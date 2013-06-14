---
title: Heroku style deployment anywhere
author: Dan
layout: post
permalink: /2013/06/heroku-style-deployment-anywhere/
categories:
  - Article
tags:
  - application
  - bash
  - continuous integration
  - deploy
  - deployment
  - git
  - heroku
  - hook
  - web
---
Heroku is quite the [interesting][1] topic these days. While there are many strong opinions about the platform itself, I feel the one thing they get right is **deployment**.

```bash
$ git push heroku master
```

That&#8217;s it. Dead simple.

Now there really isn&#8217;t any magic behind this, as Heroku harnesses the power of [Git hooks][2]. To mimic this behavior, you can use a [post-receive][3] hook, which is just a *bash script* that runs after the entire process is completed and can be used to update other services or notify users. The beauty is that this functionality can easily be replicated for deploying *any* of your sites.

For this example, let&#8217;s keep it simple and deploy a static blog to a single web server.

First order of business is to make sure you can [easily SSH][4] onto your server. So if you haven&#8217;t already, make sure your SSH public key is copied to your server:

```bash
[dan@local] $ ssh-copy-id username@server.org
```

Now, on your server, we want to create a bare Git repository. This will be the destination repository for when you perform a **git push** for deployment:

```bash
[dan@server] $ cd ~/git
[dan@server] $ mkdir myblog.git
[dan@server] $ cd myblog.git
[dan@server] $ git init --bare
```

Next thing to do is setup our simple **post-receive** script. Let&#8217;s assume for the sake of this example that our blog is served on our web server from the following directory: **/www/myblog.com**. First create the hook in your git repository:

```bash
[dan@server] $ touch ~/git/myblog.git/.git/hooks/post-receieve
```

Then update the **post-receive** hook:

```bash
#!/bin/sh
echo 'Deploying to Production...'
GIT_WORK_TREE=/www/myblog.com git checkout -f
echo 'Success!'
```

Ok, so here is where the magic happens. The **GIT\_WORK\_TREE** environment variable is used as a destination for your checked out source code, with any changes you might have made. Thus, we are performing a force [checkout][5] to the working tree directory (aka deployment)!

**NOTE**: One side benefit of the working tree approach is that you do **not** accidentally serve your [.git directory][6]!

Now that we have a new remote repository, let&#8217;s go ahead and add it to our local git repository:

```bash
[dan@local] $ git remote add production ssh://username@remote-server.org/~/git/myblog.git
```

The last thing left now is to deploy:

```bash
[dan@local] $ git push production master
Counting objects: 9, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 455 bytes, done.
Total 5 (delta 3), reused 0 (delta 0)
remote: Deploying to Production...
remote: Success!
To ssh://username@remote-server.org/~/git/myblog.git
   52056c4..1b5c293  master -&gt; master
```

Now this is a very simple example of a deployment script. Feel free to get as crazy as you want&#8230;send emails, message chat rooms, call [fabric tasks][7], etc! The sky is the limit, so get as creative as you&#8217;d like.

Feel free to [fork my Gist][8] to get yourself started!

 [1]: http://news.rapgenius.com/James-somers-herokus-ugly-secret-lyrics
 [2]: http://git-scm.com/book/en/Customizing-Git-Git-Hooks
 [3]: http://git-scm.com/book/en/Customizing-Git-Git-Hooks#Server-Side-Hooks
 [4]: http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/
 [5]: https://www.kernel.org/pub/software/scm/git/docs/git-checkout.html
 [6]: http://pythonsweetness.tumblr.com/post/52587443706/devs-please-stop-serving-git-to-the-outside-world
 [7]: http://docs.fabfile.org/en/1.6/
 [8]: https://gist.github.com/danriti/4176739
