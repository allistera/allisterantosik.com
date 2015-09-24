---
layout:     post
title:      Tip - Running Commands From Anywhere in jQuery Console
date:       2015-11-05
summary:    I recently had javascript tests that required me to execute commands in a jQuery Terminal console which turned out to be more complicated that thought.
---

I recently had javascript tests that required me to execute commands in a jQuery Terminal console which turned out to be more complicated that thought.

[jQuery Terminal](http://terminal.jcubic.pl) is a handy terminal Emulator that allows creating command line interpreters within the web browser.

If a active terminal is present onscreen we can access it from anywhere using the <code>$.terminal.active()</code> function, we can then use the exec function to run a passed in string like so:

{% highlight javascript %}
$.terminal.active().exec('ls -al');
{% endhighlight %}

Various jQuery Terminal functions can be chained to active like exec such as <code>clear</code> or <code>enabled</code>, they are listed here: [API Reference](http://terminal.jcubic.pl/api_reference.php#options)
