---
layout: default
title: Submitting a Pull Request
nav_order: 3
---


# Submitting a Pull Request
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


Collaboration on GitHub occurs via issues and pull requests. If you never created a
pull request before you might want to read the GitHub introduction about
[collaborating with issues pull requests][github-pull-requests] first.

The following figure shows the OpenSSL pull request workflow. It essentially follows
the normal [GitHub workflow][github-flow] for pull requests, with one exception:
Pull requests are not merged on GitHub directly.
Instead, a committer merges the changes locally and pushes them to [git.openssl.org][],
from where they are immediately pushed to the GitHub mirror [openssl/openssl][] by a script.
This difference is only important for team members. As a normal contributor,
you can ignore the greyed parts of the figure.

![repositories](/assets/images/workflow.svg)

**How you create your pull request**

 * Update your local working copy (a)
 * Implement the changes on a topic branch (b)
 * Push the topic branch to your clone (c)
 * Create a pull request (d)

**How your pull request get's reviewed and accepted**

 * Fetch the pull request (e)
 * Review and merge the commits (f)
 * Push the merged commits upstream (g)
 * Push new commits to the GitHub mirror automatically (h)

In practice, the workflow is not as simple, because the reviewers will have
change requests, which you respond to by adding fixups to your pull request.
While improving your pull request, you might happen that have to update your
working copy first in order to obtain changes from other contributors or
to fix conflicts. So in general you will have to repeat some of the steps
from above more often.

But let's start at the beginning and not in the middle.


### Update your local working copy

If you cloned your working copy from the official GitHub clone, then your
`master` branch is already tracking the `origin/master` branch, which makes
it easy to update your local copy.

```
$ git fetch --all
$ git checkout master
$ git pull
```

### Implement the changes on a topic branch

We heavily recommend that you create a dedicated topic branch for every
pull request you intend to submit. Don't make you changes on the `master`
branch, this will just add unnecessary complications to your own pull
request workflow.

In general, we ask you to base your work an a current version of the
`master` branch.

```
$ git checkout -b branch-name master
```

If it is a bugfix for a released version of OpenSSL, then we alternatively
accept pull requests agains the corresponding stable branch.
Currently, the only supported release is version 1.1.1., which is maintained
on the `OpenSSL_1_1_1-stable` branch.


### Push the topic branch to your clone

When finished implementing your changes, you can push your local branch
to your public GitHub fork.

```
$ git push yourname branch-name

Enumerating objects: 605, done.
Counting objects: 100% (605/605), done.
Delta compression using up to 4 threads
Compressing objects: 100% (132/132), done.
Writing objects: 100% (421/421), 85.79 KiB | 2.00 MiB/s, done.
Total 421 (delta 365), reused 343 (delta 289)
remote: Resolving deltas: 100% (365/365), completed with 172 local objects.
remote:
remote: Create a pull request for 'topic-branch' on GitHub by visiting:
remote:      https://github.com/yourname/openssl/pull/new/topic-branch
remote:
To github.com:yourname/openssl.git
 * [new branch]            topic-branch -> topic-branch
```
Note in the output above that GitHub noticed that you pushed a new branch
to you clone and suggested your next step in its response:
```
remote: Create a pull request for 'topic-branch' on GitHub by visiting:
remote:      https://github.com/yourname/openssl/pull/new/topic-branch
```

On some Linux terminals, you can open the simply left-click the link while
holding down the CTRL key. On your computer, the command migth work differently.
Alternatively, you can just copy the link and manually open it in your browser.


### Create a pull request

Follow the above link will to the GitHub web interface where you can
compare your changes and [create a pull request][github-create-pull-request].


[pro-git]: https://git-scm.com/book/en/v2
[pro-github]: https://git-scm.com/book/en/v2/GitHub-Account-Setup-and-Configuration

[git.openssl.org]: https://git.openssl.org
[github.com]: https://github.com
[openssl/openssl]: https://github.com/openssl/openssl

[github-pull-requests]: https://help.github.com/en/github/collaborating-with-issues-and-pull-requests
[github-create-pull-request]: https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request
[github-flow]: https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/github-flow