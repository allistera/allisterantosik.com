---
layout:     post
title:      Introducing mileager.io
date:       2015-08-30
summary:    Mileager.io - the new, easy way to monitor of your cars mileage
---

Around this time last year I was on the search for a new car, after many hours on the forecourt looking at various options I finally decided to go down the leasing route and choose a new Audi A3 which I have falling in love with! The only thing that concerned me was my mileage, may cars these days comes with mileage restrictions and I wanted a easy and simple way to track my usage to keep in inline.

Shortly after this I spent a few months creating a web application I named 'Car Mileager', fully written in Ruby on Rails along with the awesome looking [Materialize CSS](http://materializecss.com) framework that borrows inspiration from Google's Material Design, the most important thing was to try out new things, importance was placed on TDD, mobile-first and code that follows good style guides.

Since then I have seen various Javascript frameworks gaining in popularity, from Backbone, to Ember and Angular to the up and coming framework React+Flux. After comparing these I decided I wanted to move over to using Ember for Car Mileager, I would also choose to rebrand it into Mileager.io (Got to give it a more startup-y feel!). This will be based on Rails for its backend API, and Ember as the front end framework giving it a client-server architecture. This also gives me the choice of creating mobile apps in future, swift/iOS development is next on my todo list for learning.

To give a general overview of the features from a developer point of view, if you want to look at the client features feel free to visit [mileager.io](https://mileager.io).

# Continuous Integration and Deployments

Both the front and back end have a full test suite, from unit tests, to integration tests. I made use of [Travis-CI](https://travis-ci.org/) for running these on a CI server. For validating the code against Ruby, Javascript and SCSS style guides [Hound-CI](https://houndci.com/) is also used - couldn't recommend it more, an awesome service from the geniuses over at thoughbot.

Once the integration tests have been ran and the pull request have been accepted [Heroku](https://www.heroku.com/) has an new(ish) [feature](https://devcenter.heroku.com/articles/github-integration) for automatically deploying code from Github when a selected branch (In my case master) has been changed, providing a truly continuous deployment scenario.

# Token Authentication

I spend a lot of time investigating methods of authenticating users against an API, I didn't want to introduce a full blown oAuth2 provider, and didn't fancy utilising existing providers such as Facebook or GitHub. I choose to implement a simple Token authentication solution, one of the main issues encountered was that [devise](https://github.com/plataformatec/devise), the ruby gem that I use for user and session management removed token authentication, lucky it was trivial to implement a custom method.

[ember-simple-auth](https://github.com/simplabs/ember-simple-auth) along with [ember-simple-auth-devise](https://github.com/simplabs/ember-cli-simple-auth-devise) provided a easy way on glueing Ember and devise together.

# Ember Integration Tests

Wow, I was amazed at how easy writing integration tests in ember was!

Ember has some awesome documentation on testing, I wrote them using qUnit and ran using the testem runner under CI mode. For mocking the API responses on the client side [ember-cli-mirage](https://github.com/samselikoff/ember-cli-mirage) was used. Over all when developing in Ember everything 'just worked' as expected, although finding what the right way of doing things could be challenging on occasions, this is where the documentation helped a great deal.

# Looking to the future

For an idea on what I have planned for Mileager.io - both big and small, here is some tasks on my Kanban board:

* iOS/Apple Watch Application written in swift
* Rewrite in Rails API when Rails 5 gets released
* Full user management functionality - delete profile, change password etc
* Export data to CSV
* API documentation in [Slate](https://github.com/tripit/slate)

Both projects can be found on GitHub:

* [allistera/mileager.io-back](https://github.com/allistera/mileager.io-back) - Rails API
* [allistera/mileager.io-front](https://github.com/allistera/mileager.io-front) - Ember.cli
