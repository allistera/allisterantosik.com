---
layout:     post
title:      Installing PHPUnit On OSX Mavericks via Composer
date:       2014-01-08
summary:    Installing PHPUnit globally in OSX can be a bit tedious with many paths that can be gone down whether it be PHAR or PEAR. In this quick guide I will be showing how to easily install PHPUnit using Composer and show how to set up a syslink to run it from anywhere in your system. I will be using a fresh install of Mac OSX Mavericks.
---

Installing PHPUnit globally in OSX can be a bit tedious with many paths that can be gone down whether it be PHAR or PEAR. In this quick guide I will be showing how to easily install PHPUnit using Composer and show how to set up a syslink to run it from anywhere in your system. I will be using a fresh install of Mac OSX Mavericks.

# Install Composer

If you have yet to install composer globally this can be done. First open the Terminal App (In Application > Utilities) and enter the following two commands:

{% highlight bash %}
	curl -sS https://getcomposer.org/installer | php
	sudo mv composer.phar /usr/local/bin/composer
{% endhighlight %}

You will be prompted to enter your administator password when running the second command.

Once done you can now run composer from the Terminal, lets just test that it works, enter the following in the Terminal App:

{% highlight bash %}
	composer --version
{% endhighlight %}

If everything installed corrently you should get back something like the following: <code>Composer version [Version String] [Installation Date]</code>


# Download PHPUnit

Next we need to download PHPUnit, but we need a location on our system to store it, I like to store all mine in ~/libraries, so  lets create this folder and traverse into it, from the Terminal App run the following:

{% highlight bash %}
	mkdir ~/libraries
    cd ~/libraries
{% endhighlight %}

Now it's time to create our <code>composer.json</code> file, once again using the Terminal App that we have open run:

{% highlight bash %}
	touch composer.json
  nano composer.json
{% endhighlight %}

The command line text editor nano will then open, paste the following code in it:

{% highlight json %}
{
    "require-dev": {
        "phpunit/phpunit": "3.7.*"
    }
}
{% endhighlight %}

To save the file and exit nano press ctrl+x, type 'y' and press the enter key.

Finally run the composer install command from the Terminal app to download PHPUnit and it's dependencies like so:

{% highlight bash %}
	composer install
{% endhighlight %}

Note: If you don't have <code>git</code> installed on your system you might get a xcode notiifcation that will allow you to  automatically download and install it it, this is fine allow it to run.

# Install PHPUnit Globally

We now have PHPUnit installed within the libraries folder, lets just  confirm this by run the following:

{% highlight bash %}
	~/libraries/vendor/bin/phpunit --version
{% endhighlight %}

The corrent response should be <code>PHPUnit 3.7.28 by Sebastian Bergmann.</code>

Now lets create a system link to our computers bin folder from PHPUnit Binary, in terminal run:

{% highlight bash %}
	sudo ln -s ~/libraries/vendor/bin/phpunit /usr/bin/phpunit
{% endhighlight %}

Again you will be asked to enter your password.

PHPUnit will now be installed on your system. To confirm this close down the Terminal app, open it again and run the <code>phpunit --version</code> command. The version number should appear as it did before.

The advantage of this approach is that it gives us a central library folder, want to install behat or php_codesniffer? Simply add it to our composer.json file, run composer install and create a system link to the binary.

Happy testing!
