---
layout:     post
title:      Tip Pre Commit Checklist
date:       2013-11-05
summary:    Do you have a checklist that you run through before committing your code? Before I send my code up to BitBucket/GitHub I have a basic bash script that asks me a few questions; if I have kept inline with coding standards, if I have commented on my code, ran unit tests etc. This bash script runs on Unix based OS's forces you to answer these questions before your code is committed.
---

Do you have a checklist that you run through before committing your code? Before I send my code up to BitBucket/GitHub I have a basic bash script that asks me a few questions; if I have kept inline with coding standards, if I have commented on my code, ran unit tests etc. This bash script runs on Unix based OS's forces you to answer these questions before your code is committed.

Here is the current script I have saved in my <code>/usr/bin</code> directory for PHP development. Note it uses mercurial but can of course be updated to use Git by changing line 21 and 26.
{% highlight bash %}
#! /bin/bash

echo "Has all code, classes and methods been commented?"
read ans
[ $ans != "y" ] && exit 0

echo "Is the commit a full feature with everything functioning?"
read ans
[ $ans != "y" ] && exit 0

echo "Has the new feature been tested with expected and non expected data?"
read ans
[ $ans != "y" ] && exit 0

echo "Has the PSR-1 and PSR-2 coding style guides being followed?"
read ans
[ $ans != "y" ] && exit 0

echo "Checklist passed! Commit Message:"
read ans
hg commit -m "$ans"

echo "Commit Successful - Do you wish to push the commit?"
read ans
[ $ans != "y" ] && exit 0
hg push
{% endhighlight %}

This can be installed by running the following code from the command line:
{% highlight bash %}
$ cd /usr/bin
$ sudo nano commit
# Paste the pre-commit script, then save by pressing ^X.
$ sudo chmod +x commit
{% endhighlight %}
Now in the terminal when you run 'commit' the script should kick in like so:

![Check List Script Running](http://i.imgur.com/2vESfOO.png)
