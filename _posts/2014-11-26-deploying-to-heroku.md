---
layout: post
title: Deploying to Heroku
---
I've recently deployed an [app](https://github.com/raysapida/mustached-octo-robot) I was working on to Heroku and the process of matching the development environment to the production environment was very interesting. Heroku itself provided an [article](https://devcenter.heroku.com/articles/getting-started-with-rails4) to set up a Rails app and an additonal [article](https://devcenter.heroku.com/articles/rails-unicorn) to set up a unicorn server. 

### The two specific gems I added to the Gemfile
* [unicorn](https://rubygems.org/gems/unicorn)
* [rails_12factor](https://github.com/heroku/rails_12factor) which includes the gems [rails_stdout_logging](https://github.com/heroku/rails_stdout_logging) and [rails_serve_static_assets](https://github.com/heroku/rails_serve_static_assets)

The rails_12factor gem enables the app to improve on two factors in the [12 factor app](http://12factor.net/); treating logs as an event stream instead of writing them to a single file and serving static assets through Rails instead of a proxy server. This was my first experience with the term twelve factor app and I'm taking the time to learn as much as I can about it before writing any more on the topic. 

To use the unicorn gem, I added a file to `config/unicorn.rb` and I used the basic configuration that heroku provided. The default web server in rails, Webrick, can only handle one request at a time so a different server is needed in production. From my understanding, Unicorn emulates a thread safe app by prioritizing fast requests over slower ones. 

The biggest problem I came across was applying the database migrations to the Heroku database. Running `heroku run rake db:migrate` produced an error and it might have been because I started the app from an older version of Rails. The older migrations could have started conflicting. As a workaround, I switched my development database to Posgresql, ran the migrations on my computer, and pushed the schema through the command  `heroku pg:push <LOCAL DB> <HEROKU DB>`. 

### Further questions I had ###
* What are the practical ramifications of the 12 factors to a web developer ?
* Why shouldn't I add the ruby gem foreman into the Gemfile ?
* How does Unicorn interact with Rack Applications ?
* What are the major differences between Unicorn, Thin , Puma and other Rack web servers ?