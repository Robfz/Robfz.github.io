---
layout: post
title:  Intermediate Section
date:   2015-09-22 12:16:00
categories: noob level
---

Now we are going to talk about some intermediate topics.

<h2>DiffMerge</h2>

Sometimes there will be occasions when we want to compare the differences between file versions. Git comes bundled with a `difftool` to compare files, but there are better tools. Here, we are going to set [DiffMerge][DiffMerge] as our default `difftool`.

First download [DiffMerge][DiffMerge]. Then use the following commands to configure Git to use it (these instructions are for Linux):

{% highlight ruby %}
git config --global diff.tool diffmerge
git config --global difftool.diffmerge.cmd 'diffmerge "$LOCAL" "$REMOTE"'
git config --global merge.tool diffmerge
git config --global mergetool.diffmerge.cmd 'diffmerge --merge --result="$MERGED" "$LOCAL" "$(if test -f "$BASE"; then echo "$BASE"; else echo "$LOCAL"; fi)" "$REMOTE"'
git config --global mergetool.diffmerge.trustExitCode true
{% endhighlight %}

And a brief usage guide:

{% highlight ruby %}
# diff the local file.m against the checked-in version
git difftool file.m

# diff the local file.m against the version in some-feature-branch
git difftool some-feature-branch file.m

# diff the file.m from the Build-54 tag to the Build-55 tag
git difftool Build-54..Build-55 file.m
{% endhighlight %}

(Info taken from [Two Bit Labs][TwoBitLabs])

Lets see an example. I am going to modify the file `index.html` in my repository and run the command:

{% highlight ruby %}
git difftool index.html
{% endhighlight %}

![Diff1](/assets/intermediate/Diff1.png)

A prompt will ask us if we want to start `DiffMerge`:

![Diff2](/assets/intermediate/Diff2.png)

Then we can use `git mergetool` to merge the files.

<h2>Branching</h2>

<h1>Forking</h1>

The term `fork` refers to creating a copy of someone's else repository and work on it. To fork a repository:

Navigate to the GitHub page of the project you want to fork and click on the `fork` button:

![Fork1](/assets/intermediate/Fork1.png)

And the magic kicks in:

![Fork2](/assets/intermediate/Fork2.png)

Lets clone our fork, make a modification to a file, commit the change and push them to the server:

![Fork3](/assets/intermediate/Fork3.png)

![Fork4](/assets/intermediate/Fork4.png)

![Fork5](/assets/intermediate/Fork5.png)

<h1>Pull requests</h1>

Now that we have done some modifications on our fork, lets request the original author to merge our changes to her repository. This is called a `pull request`.

To create a pull request, go to your forked repository and click on the little green button next to the branch button:

![PullReq1](/assets/intermediate/PullReq1.png)

You can see the changes done. Then click on 'Create pull request':

![PullReq2](/assets/intermediate/PullReq2.png)

Write a title for your `pull request` and a description:

![PullReq3](/assets/intermediate/PullReq3.png)

Then, you just have to wait for the author to accept or reject your request. In our case, our request was accepted!

![PullReq4](/assets/intermediate/PullReq4.png)

<h1>Accepting pull requests</h1>

If someone forks a repository from us and makes a `pull request`, GitHub will notify us:

![AccPull1](/assets/intermediate/AccPull1.png)

We can review the changes and decide if we want to merge the changes in our repository:

![AccPull2](/assets/intermediate/AccPull2.png)

![AccPull3](/assets/intermediate/AccPull3.png)

Then we can see the commit history; collaboration is cool!

![AccPull4](/assets/intermediate/AccPull4.png)

[DiffMerge]: https://sourcegear.com/diffmerge/
[TwoBitLabs]: http://twobitlabs.com/2011/08/install-diffmerge-git-mac-os-x/