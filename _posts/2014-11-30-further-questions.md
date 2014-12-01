---
layout: post
title: Further Questions
---
I'm finally sitting down and trying to look into the questions that built up from the past week  

* ### Why adding the ruby gem foreman into the Gemfile is not recommended?
This ruby gem is used for organizing apps with multiple components and uses a Procfile. The Procfile lists which processes foreman is suppose to manage. Heroku has an [article](https://devcenter.heroku.com/articles/procfile#process-types-as-templates) that provides further details on Procfiles and the github page for foreman also has an extensive [manual](http://ddollar.github.io/foreman/). What jumped out the most from the foreman manual were the flags for port and concurrency which managed how many workers would be used for each process. From the heroku article , the most basic command in the Procfile was `bundle exec rails server -p $PORT` but more processes can be added. From what I can find, Heroku didn't suggest adding foreman into the Gemfile because its already added by default. 

* ### How does Unicorn interact with Rack Applications ? 
I found an [article](https://blog.engineyard.com/2010/everything-you-need-to-know-about-unicorn) that clarified the features that Unicorn has. There was also another article on how they can be configured at [Digitial Ocean](https://www.digitalocean.com/community/tutorials/how-to-optimize-unicorn-workers-in-a-ruby-on-rails-app). Both articles wrote about the advantages of using Unicorn but I didn't start seeing how it could be implemented until I looked at the [guide](http://guides.rubyonrails.org/initialization.html#loading-rails-rack-lib-rack-server-rb) for the Rails Initialization Process. At the end of the guide, it mentioned that the process would be handed off to the specific server implementaion and that led me to the [Unicorn::HttpServer](http://bogomips.org/unicorn.git/tree/lib/unicorn/http_server.rb) class. I'm not sure how the process goes after it reaches this point, but I'll read the source code more in detail to find out. I do know from the comments that a server could be run using `HttpServer::run`. In the future, I want to write a blog post that extends the guide to how Unicorn would handle the last line `server.run wrapped_app, options, &blk`. 

* ### What are the major differences between Unicorn, Thin , Puma and other Rack web servers ?
This [article](https://www.digitalocean.com/community/tutorials/a-comparison-of-rack-web-servers-for-ruby-web-applications) was a great start on figuring out the differences between the servers. The answer produced even more questions though. Specifically on what is NGINX, Mongrel's parser, Event Machine network I/O library, and the specifics of Rack middleware for HTTP requests. 

* ### How does concurrency and thread-safe work in a Rails?
I started looking at stackoverflow to find out what [concurrency](http://stackoverflow.com/questions/1050222/concurrency-vs-parallelism-what-is-the-difference) and [thread-safe](http://stackoverflow.com/questions/261683/what-is-meant-by-thread-safe-code) means. There was also another [post](http://stackoverflow.com/questions/15184338/how-to-know-what-is-not-thread-safe-in-ruby) on what isn't thread safe in Ruby. Rails has a specific [configuration](http://www.sitepoint.com/config-threadsafe/) that is turned on by default and this [post](http://tenderlovemaking.com/2012/06/18/removing-config-threadsafe.html) went into through an indepth discussion about what that configuration did. The most interesting parts was when he said that "We know that loading the framework isn’t threadsafe, so the strategy is to load it all up before any threads are ready to handle requests" and that the `@allow_concurrency` option turns off a Rack Middleware called `Rack::Lock`. Again, this opened up more questions about the difference between multi-threaded servers and multi-process servers along with the difference between eager loading and lazy loading. 

		def threadsafe!
			@preload_frameworks = true
			@cache_classes      = true
			@dependency_loading = false
			@allow_concurrency  = true
			self
		end
			
* ### How to configure a deployment through environment variables?
After finding two articles about it from [railsapps](http://railsapps.github.io/rails-environment-variables.html) and [tealeaf](http://www.gotealeaf.com/blog/managing-environment-configuration-variables-in-rails), the best ways I read to manage environment variables centers around two gems; [figaro](https://github.com/laserlemon/figaro) and [dotenv-development](https://github.com/bkeepers/dotenv-deployment). Both use a separate file, `.env` and `application.yml` respectively, that can be used to set environment variables and should not added to the public repository. 

* ### What are the best practices for deploying a Rails application?
There were many articles about this and I found that the best practices revolve around where you're deploying to and the specific requirements for your app. A common thread I found was using a tool to standardize the process like [capistrano](http://capistranorb.com/documentation/overview/what-is-capistrano/), [chef](https://www.getchef.com/chef/), or [puppet](http://puppetlabs.com/).  

## Even more questions
* What is NGINX?
* What is Mongrel's parser?
* What is Event Machine network I/O library and how does it work? 
* How does Rack middleware and Rack in general work with Ruby web applications?
* What is the difference between multi-threaded servers and multi-process servers?
* What is the difference between eager loading and lazy loading?
* How could I use capistrano, chef or puppet ?