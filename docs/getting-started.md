---
layout: default
title: Getting Started
nav_order: 2
---

# Getting Started
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

If this is the first time you are contributing to an open source project on GitHub,
you might feel overwhelmed by all the details you need to know about Git and GitHub
in general, and the OpenSSL workflow on GitHub in particular.
Don't worry, this page intends to guide you through your first steps. Also rest assured
that the OpenSSL team welcomes every new contributor and we are happy to answer your
questions and help you with any problem you might encounter during your first
pull requests.


## Getting started with GitHub

The GitHub Help site has detailed information about [Getting started with GitHub][github-getting-started],
which we don't want to replicate here. If you never used Git version control system before,
take a look at the excellent [Pro Git][pro-git] book by Scott Chacon (a co-founder of GitHub)
and Ben Straub. It is free and you can read it online or download an offline copy.
The book serves both as a tutorial for beginners and a valuable reference for the experienced user.
It also contains a detailed introduction to GitHub in [Chapter 6][pro-github].


## Setting up the Repositories

The OpenSSL project maintains two source repositories,

 * the **main OpenSSL project repository** at [git.openssl.org][], and
 * the **official GitHub mirror** [openssl/openssl][].

Unless you are an OpenSSL committer (i.e., a team member who has commit access to the project repository),
you can safely ignore the former repository and focus on the GitHub repository.
For the GitHub workflow, you will need two more repositories,

* your **public GitHub fork** yourname/openssl of the openssl/openssl repository, and
* your **local working copy** ~/src/openssl, connected to openssl/openssl and yourname/openssl.

The following setup is only a suggestion and does not claim to be the perfect solution for everybody.
If you are experienced with git and prefer to setup things differently, feel free to do it your way.

![repositories](/assets/images/repositories.svg)


| Repository                 | Name     |  URL/Location                            |
|:---------------------------|:---------|:-----------------------------------------|
| 1: Main OpenSSL repository | upstream |  git://git.openssl.org/openssl.git       |
| 2: Official GitHub mirror  | origin   |  https://github.com/openssl/openssl.git  |
| 3: Your public GitHub fork | yourname |  https://github.com/yourname/openssl.git |
| 4: Your local working copy |          |  ~/src/openssl                           |



### Fork the OpenSSL GitHub Repository

Follow the [GitHub instructions][github-fork-a-repo] to create your fork of the official
GitHub mirror:

```
https://github.com/openssl/openssl.git -> https://github.com/yourname/openssl.git
```

### Create your local working copy

Your local working copy needs to be attached to both the official repository and your
public fork. Use the following steps to clone a local copy from the official repository
and add your own fork as secondary remote repository afterwards.

```
~$ cd ~/src
~/src$ git clone https://github.com/openssl/openssl.git
~/src$ cd openssl
~/src/openssl$ git remote add yourname https://github.com/yourname/openssl.git
```

From now on, we will always assume that the local repository is located at
~/src/openssl and omit the path in the shell prompt.

You can use the `git remote` command to check whether your setup is correct:
```
$ git remote -v

origin https://github.com/openssl/openssl.git (fetch)
origin https://github.com/openssl/openssl.git (push)

yourname https://github.com/yourname/openssl.git (fetch)
yourname https://github.com/yourname/openssl.git (push)
```

### Checkout additional branches

Active development of new features occurs on the `master` branch and
are released on the next version.
Additionally, for all current and previous OpenSSL releases, there is a branch
`OpenSSL_x_y_z-stable` corresponding to version x.y.z, on which bugfixes for
the released version are maintained. Currently, the only supported release is
version 1.1.1.

If you try to checkout the `OpenSSL_1_1_1-stable` stable branch for the first
time using the command
```
git checkout OpenSSL_1_1_1-stable
```
then git will try to checkout the branch from the remote repositories and will
complain because there are two identically named branches in `origin` and in
`yourname`, respectively. It will tell you to use the following more explicit
command instead:
```
git checkout --track origin/OpenSSL_1_1_1-stable
```
This will create a local branch `OpenSSL_1_1_1-stable` tracking the corresponding
branch on `origin`, the official GitHub mirror.


## Pull Requests in a Nutshell

Collaboration on GitHub occurs via [issues and pull requests][github-pull-requests].
The following figure shows the OpenSSL workflow, which essentially follows the
normal GitHub workflow, with one exception: pull requests are not merged on
GitHub directly, but are published on [git.openssl.org], from where they are
mirrored to GitHub. This is shown in the greyed parts of the figure,
which cou can safely ignore for the moment.

![repositories](/assets/images/workflow.svg)

**How you create your pull request**

 * Update your local working copy (a)
 * Implement the changes on a topic branch (b)
 * Push the topic branch to your clone (c)
 * Create a pull request (d)

Your repositories are now set up and you are ready to
[create your first pull request](/creating-a-pull-request).

[pro-git]: https://git-scm.com/book/en/v2
[pro-github]: https://git-scm.com/book/en/v2/GitHub-Account-Setup-and-Configuration

[git.openssl.org]: https://git.openssl.org
[github.com]: https://github.com
[openssl/openssl]: https://github.com/openssl/openssl

[github-getting-started]: https://help.github.com/en/github/getting-started-with-github
[github-fork-a-repo]: https://help.github.com/en/github/getting-started-with-github/fork-a-repo
[github-pull-requests]: https://help.github.com/en/github/collaborating-with-issues-and-pull-requests
