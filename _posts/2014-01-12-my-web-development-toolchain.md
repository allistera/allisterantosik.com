---
layout:     post
title:      My Web Development Toolchain
date:       2014-01-12
summary:    Recently I was asked about some of my favourite Mac OSX apps for web development, I mainly develop in PHP but the all these tools can be used for Python, Ruby etc development with the exception for PHPUnit.
---

Recently I was asked about some of my favourite Mac OSX apps for web development, I mainly develop in PHP but the all these tools can be used for Python, Ruby etc development with the exception for PHPUnit.

####[Vagrant](http://www.vagrantup.com/)

Different projects have different dependences, some use Beanstalkd while others prefer RabbitMQ, rather than installing all these on my machine Vagrant allows me to easily manage them all on a project basis by creating a virtual development environment. Previously I used [MAMP Pro](http://www.mamp.info/en/index.html) to run PHP applications on my development machine until discovering Vagrant and its advantages. [Protobox](http://getprotobox.com/) makes generating Vagrant boxes a breeze.

####[Google Chrome](https://www.google.com/chrome)

Has good support for modern standards and top class developer tools. I also found Safari to be quite slow on occasions especially with dealing with Javascript, don't forget <code>⌘ + [Tab Number]</code> to quicky jump to a specific tab.

**Alternative**: Safari - offers the best integration for OSX although somewhat lacking in terms of developer tools compared with Chrome or Firefox.

####[Sublime Text](http://www.sublimetext.com/)

Using the [Spacegray](https://github.com/kkga/spacegray) theme with Source Code Pro font. I absolutely love how easy it is to customise while retaining its simplicity, not to forget its killer feature: Multiple Selections. In terms of plugins I have the following:

*	[Package Control](https://sublime.wbond.net/)
*	[Emmet](https://sublime.wbond.net/packages/Emmet)
*	[Bracket Highlighter](https://sublime.wbond.net/packages/BracketHighlighter)
*	[NightCycle](https://sublime.wbond.net/packages/NightCycle)
*	[SublimeCodeIntel](https://sublime.wbond.net/packages/SublimeCodeIntel)


**Alternative**: [PHPStorm](http://www.jetbrains.com/phpstorm/)- If you want a full blown PHP IDE this is your best option.  
**Free Alternative**: [Light Table](http://www.lighttable.com/)

####[Things](http://culturedcode.com/things/)

I live by the [GTD](http://en.wikipedia.org/wiki/Getting_Things_Done) approach - Things make managing tasks on a project-to-project basis. Things is very pricey, although I personally think it's worthwhile for my workflow.

**Free Alternative**: [Wunderlist](https://www.wunderlist.com/)


####[iTerm](http://www.iterm2.com/)

I use iTerm for its customizability, it is really easy to theme - my favorite being is Zenburn from [iTerm 2 Color Themes - Github](https://github.com/baskerville/iTerm-2-Color-Themes). I also changed my shell to [fish](http://fishshell.com/) for auto complete!

####[Sequel Pro](http://www.sequelpro.com/)

Such an amazing free MySQL client for the OSX, native Cocoa app so fits beautifully into Mavericks. Works really well remotely over SSH also.

####[Sourcetree](http://www.sourcetreeapp.com/)

While I know a lot of developers prefer to work with VC's through the command line I much prefer a visual element to it, Sourcetree is a free Mercurial and Git Client with built-in support for HG/Git-Flow.

####[Alfred](http://www.alfredapp.com/)

Alfred saves me a lot of time opening apps and searching for files. I have disabled spotlight and changed alfreds key combo to <code>⌘ + space</code>

####[Livereload](http://livereload.com/)

Removes the need to constantly refresh my web browser everytime I make a change to the source code. Livereload constantly monitors a selected folder for changes, also has the ability to compile SASS, LESS, Stylus, CoffeeScript etc. Comes with browser extensions so no need to inject Javascript into your sites.


####[PHPUnit](http://phpunit.de/)

Essential for using the [Test-driven Development](http://net.tutsplus.com/tutorials/php/lets-tdd-a-simple-app-in-php/) process when developing your web applications. I recently wrote a guide on [Installing PHPUnit on OSX Mavericks](http://www.allisterantosik.com/installing-phpunit-on-osx-mavericks/)

####[Capistrano](https://github.com/capistrano/capistrano)

A remote multi-server automation tool primary used for deploying web applications to remote servers. It really helps when deploying to more than one web server, including supporting database migrations.

#### Misc Apps
*   [1Password](https://agilebits.com/onepassword) - essential for proper password storage and generation
*   [Ember](https://realmacsoftware.com/ember) - for storing design inspiration
*   [Evernote](https://evernote.com/) - keeping notes in sync on my iPhone, iPad and Mac
*   [Flux](http://justgetflux.com/) - for reducing eye strain when using your computer at night
*   [Bartender](http://www.macbartender.com/) - let's me tidy my menu bar to the bare minimum
*	[Mailcatcher](http://mailcatcher.me/) - let's me simulate a SMTP server and catches any message sent to it to display in a web interface
