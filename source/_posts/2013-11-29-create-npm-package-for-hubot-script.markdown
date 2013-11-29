---
author: Dan Riti
layout: post
title: "Create a NPM package for your Hubot Script"
date: 2013-11-29 16:11
comments: true
categories:
  - Article
tags:
  - hubot
  - script
  - package
  - npm
  - deploy
  - publish
---

So you just thought of the next killer [Hubot][1] script and you want to share
it with the world? Well if you haven't been paying attention, you should know
that the [hubot-scripts][3] community has changed their [contributing policy][5]:

> It's now preferred that if you are able to, you should release your script as
  part of a npm package built for Hubot.

And it's a good change, because this now allows scripts to be distributed and
versioned as individual NPM packages. This also means that individual scripts
can easily declare dependencies, which is a big improvement.

If you're familiar with the process for [creating a NPM package][6], then
you're off to a good start. We're going to be using [yeoman][7] and the
[generator-hubot-script][8] to generate all the boilerplate necessary for
quickly creating a NPM package for our Hubot script.

**NOTE**: The generated boilerplate is based on the [hubot-example][2] repository.

Now let's ago head and install `yeoman` and the `generator-hubot-script` using
NPM:

```bash
$ npm install -g yo generator-hubot-script
```

Secondly, let's go ahead and create a directory for our script. For the sake of
this example, we're gonna assume we created a script called
`foobar.coffee`, so we want to appropriately namespace our package with
the name `hubot-foobar`:

```bash
$ mkdir hubot-foobar
$ cd hubot-foobar
$ yo hubot-script:foobar
```

Follow the prompts and wait until the NPM install completes. Now let's
initialize the directory as a Git repository and commit our initial files:

```bash
$ git init
$ git add .
$ git commit -m "Initial commit"
[master (root-commit) 5871342] Initial commit
 10 files changed, 175 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 .travis.yml
 create mode 100644 Gruntfile.js
 create mode 100644 README.md
 create mode 100644 index.coffee
 create mode 100644 package.json
 create mode 100755 script/bootstrap
 create mode 100755 script/test
 create mode 100644 src/hello-world.coffee
 create mode 100644 test/hello-world-test.coffee
```

Cool, so now all the boilerplate is in place, it's out with the old and in with
the new:

```bash
$ cp ~/some/location/foobar.coffee src/
$ git add src/foobar.coffee
$ git rm src/hello-world.coffee
$ git commit -m "Add foobar script"
[master 4f4c612] Add foobar script
 1 file changed, 22 deletions(-)
 create mode 100644 src/foobar.coffee
 delete mode 100644 src/hello-world.coffee
```

Unit testing is cool, so let's go ahead and set that up:

```bash
$ git mv test/hello-world-test.coffee test/foobar-test.coffee
$ vim test/foobar-test.coffee # update file to test your script
$ grunt test
```

Once you have some passing test cases, let's go ahead and commit these changes:

```bash
$ git add test/hello-world-test.coffee
$ git commit -m "Update test cases"
[master 35d124a] Update test cases
 1 file changed, 2 insertions(+), 2 deletions(-)
```

Next, you want to go ahead and update the `package.json` file to include
all the relevant information for your script. Make sure the following fields
are all satisfactory:

- `author`
- `description`
- `version`
- `author`
- `license`
- `keywords`
- `repository`
- `bugs`
- `dependencies`

More details on this file can be found [here][9]. Once you're done, go ahead
and commit your changes:

```bash
$ git add package.json
$ git commit -m "Update package.json"
[master 78c3233] Update package.json
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Lastly, go ahead and review the `README.md` file. Feel free to make any
changes, and add any missing documentation you think is necessary. Make sure
to commit any changes you make.

```bash
$ git add README.md
$ git commit -m "Update README"
[master f94cd40] Update README
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Congratulations, you've packaged your Hubot script and are ready to share it
with the world! So go ahead and push this repository to Github or
[publish the package on NPM][10].

[1]: http://hubot.github.com/
[2]: https://github.com/hubot-scripts/hubot-example
[3]: https://github.com/github/hubot-scripts
[5]: https://github.com/github/hubot-scripts/blob/master/CONTRIBUTING.md
[6]: https://npmjs.org/doc/developers.html
[7]: http://yeoman.io/
[8]: https://github.com/desmondmorris/generator-hubot-script
[9]: https://npmjs.org/doc/json.html
[10]: https://npmjs.org/doc/publish.html
