---
layout: post
title:  Intermediate Section
date:   2015-09-21 21:57:00
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

Lets see an example:

[DiffMerge]: https://sourcegear.com/diffmerge/
[TwoBitLabs]: http://twobitlabs.com/2011/08/install-diffmerge-git-mac-os-x/