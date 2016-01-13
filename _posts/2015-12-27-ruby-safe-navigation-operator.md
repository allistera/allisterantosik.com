---
layout:     post
title:      Introducing the Safe Navigation Operator in Ruby 2.3.0
date:       2015-12-28
summary:    One of the much anticipated feature in Ruby 2.3.0 is the Safe Navigation Operator (can be found in other modern languages such as C#, Swift, CoffeeScript and Groovy) which gives us a nice syntactic sugar for checking if a property has a nil value. Lets take a look at a use case for it...
---

Ruby version 2.3.0 has recently been released and is now available through [Ruby-Build](https://github.com/rbenv/ruby-build/releases/tag/v20151225).

One of the much anticipated feature in Ruby 2.3.0 is the Safe Navigation Operator (can be found in other modern languages such as C#, Swift, CoffeeScript and Groovy) which gives us a nice syntactic sugar for checking if a property has a nil value.

## How does it work? Lets take a look...

Consider the following example:

{% highlight ruby %}
  user = User.find(1)
  if user.wallet.ballance == 0
    ...
  end
{% endhighlight %}

The problem here is that we will get a Ruby exception if we can't find the user with an ID of 1 or if the user doesn't have a wallet property attached to the user object. If we want to go down the pure ruby way of fixing this we can do something like this:

{% highlight ruby %}
  if user && user.wallet && user.wallet.ballance == 0 
    ..
  end
{% endhighlight %}

This looks long-winded and messey, thankfully ActiveSupport has a way make our syntax a bit nicer that will help us a bit when we are working with Rails objects: the try! method, lets rewrite the previous example using it:

{% highlight ruby %}
  if user.try!(wallet).try!(ballance) == 0 
    ..
  end
{% endhighlight %}
  
But we might be writing code where ActiveSupport isn't available we would have to fall back to the previous pure-ruby syntax, for this lets use the new Safe Navigation Operator in 2.3.0:

{% highlight ruby %}
  if user&.wallet&.ballance == 0
    ..
  end
{% endhighlight %}

It's as easy as that to simplify our code, note that the Safe Navigation Operator behaves as try! of ActiveSupport, which specially handle only nil.

## But...

Beware that **excessive** nil checks are an excellent sign of poor code quality.

