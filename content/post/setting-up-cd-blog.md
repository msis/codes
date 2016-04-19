+++
date = "2016-04-19T10:15:15-04:00"
title = "Setting up Continuous Deployment for a blog"
draft = true

+++

Like most people I love free things that work well.
Open source projects [hugo](http://gohugo.io/), free hosting [github](https://github.com/), and free Continuous Integration and Deployment [Travis CI](https://travis-ci.org/) are therefore something I love to play with.

However the challenge with *open-source* and *free* is that it's hard to go from nothing to something reliable quickly and easily.
For example, to set up this blog, it took me almost around 20 iterations before being able to finally write this very first article.

This is mainly due to one of the biggest flaws of open-source in general: **documentation**.
Most people value contribution through the change that is made.
I fall under this category too and this my first try documenting the process of using 3 open-source/free resources to set-up a $0 blog (or a static web pages in general).

## Pre-requisites
Make sure that you have a text-editor, [`git`](https://git-scm.com/), and account on [*gihtub*](https://github.com/join), one on [*Travid CI*](https://travis-ci.org/) and above all, Internet access.

The tools I'll be using are cross-platform. I'll be showing you the steps for *Debian/Ubuntu*. For *Windows* and *OS X* users, it can only be easier.

# Install hugo
First you need to get the binaries for Hugo for your operating system [here](https://github.com/spf13/hugo/releases).
As of now, the latest version of hugo is *v0.15*.

Once the download is complete, proceed to the install.
Here's how to do it for *Linux* users:
```console
$ cd Downloads
$ sudo dpkg -i hugo_0.15_amd64.deb
```

And you're done!
### Read more
- [Quickstart with `hugo`](http://gohugo.io/overview/quickstart/)


# Github pages
Github are kind enough to serve static web pages right from the *git* repos.

Suppose that your username is `msis` and you want to serve static pages from a repo named `codes`. As soon as a git *branch* is called `gh-pages` exists, Github will generate the webpages available under http://msis.github.io/codes/ .

To do so, first create an new repository on Github.
Then clone it locally, on a console:
```console
$ git clone https://github.com/msis/codes
```

The latter command will create a local folder containing repository.
We now need to initiate a *hugo* website :
```console
$ hugo new site --force codes
$ cd codes
```
//TODO:
Note that the `--force` is necessary as the directory `codes` already exists.

### Read more
- [Github Pages](https://pages.github.com/)

# Generate Github token
As *Travis CI* will be publishing the webpages on your behalf. You better have a Github token to use instead of your password.
A token can be disabled and/or reset in case it's compromised and will limit the collateral harm that a leaked password may cause.

To get a Github token, go to: https://github.com/settings/tokens .
We will be encrypting the token in the next step to prevent compromising the github account.

Create a new token, name it *travis-ci* and give it access to :

```
[x] repo
  [x] repo:status
  [x] repo_deployment
  [x] public_repo
```

Once generated save the token in a secure place. (Do not commit your tokens unencrypted!)

# Travis CI

*Travis CI* is very useful to run continuous integration of your code in general and a very handy tool if you master it enough.

In our case, we will be using for two things: first we would like *Travis* to check that our **hugo** site builds correctly. And when it does, to automatically publish it for us to *Github* to serve it.

# Adding the deployment script

# Read More
