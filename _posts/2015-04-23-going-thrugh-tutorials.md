---
layout: post
title: Learning from tutorials
---
For the past two weeks, I've been going through as many Ruby tutorial projects
as I could. Many of them were easy to follow but this time around, I've been
trying my best to practice test-driven development as I go through the
exercises. The [contact
manager](http://tutorials.jumpstartlab.com/projects/contact_manager.html)
tutorial by Jumpstart Lab was a great starting point for this because they
follow this workflow.

I've been trying out different
tools including [rspec-rails](https://github.com/rspec/rspec-rails),
[shoulda-matchers](https://github.com/thoughtbot/shoulda-matchers),
[factory_girl_rails](https://github.com/thoughtbot/factory_girl_rails),
[fabrication](https://github.com/paulelliott/fabrication),
[minitest](https://github.com/seattlerb/minitest), and
[fixtures](http://api.rubyonrails.org/classes/ActiveRecord/FixtureSet.html). So
far, I've been using rspec more because of how it
integrates with rails generators like scaffolding. Scaffolding generates
the usual CRUD actions and rspec generates the associated test in the controller 
specs. I felt like I was cheating a little bit by using generators so much but
the speed I was working through tutorials that used to take me multiple days was
difficult to overlook. I found myself setting model fields and
associations through the command line instead of migrations. Rspec's syntax 
feels very natural and as familiar now as
minitest's assertions. At this point, I can appreciate what the generators do
and I don't have to build up Rails controller from the bottom up as long as I
understand what is going on which each action and I'm testing throughout the
whole process.

## Commands I've learned
* `rails g model sports_category --parent category`

* `rails g scaffold Comment content:text user:belongs_to post:belongs_to`

* `heroku git:clone -a myapp`

* [`rails g scaffold Foo foo_string:string foo_text:text foo_integer:integer
  foo_float:float foo_decimal:decimal foo_timestamp:timestamp foo_time:time
foo_date:date foo_binary:binary
foo_boolean:boolean`](https://agilewarrior.wordpress.com/2014/10/12/rails-generators-cheat-sheet/)
