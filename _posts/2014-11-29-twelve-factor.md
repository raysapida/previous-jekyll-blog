---
layout: post
title: 12 Factor apps
---
I was researching the ideas behind the 12 factor app and I learned a lot about deploying an application. 

1. ### Codebase
The main idea behind this factor is using a version control system and that one app corresponds to one codebase. Codebases should not share code and if it does, they should be refactored into a shared library that can be included with dependencies.   

2. ### Dependencies
Manage dependencies within an app and for a Rails application, this can be done through the Gemfile with locked versions. 

3. ### Config
The configuration should be separate from the code and preferrably set in the environment's variables. For a Rails app, there's an explicit directory where configurations can be defined but this definition does not include routes or other internal configurations. Does this mean that the configurations in the yaml files should not be stated? This [article](http://blog.doismellburning.co.uk/2014/10/06/twelve-factor-config-misunderstandings-and-advice/) cleared up some of those things for me. Things like the secret key and database configuration can be managed from the command line or with a `config/secrets.yml` that's not added to a repository. I still had more questions about managing secret keys outside of Rails with engines like Devise. I searched more and found answers in [one](https://github.com/plataformatec/devise/issues/2554) of Devise's issues page. I still need to do more research into this because it sounds specific to what an app is using. 

4. ### Backing Services
These services include the database, messaging and cache systems. The main idea behind this is that each service should be loosely coupled with the app and that would enable a deployment to easily swap them. My only experience with this so far is through database configurations.

5. ### Build, Release, Run
This factor encourages the separation betweem the build, release, and run stages. The build stage occurs during deployment, the release stage combines the build stage with configurations, and the run stage occurs while the environment is proccessing requests. I'm still figuring out the best way to do this for a Rails app. Most of the articles I've read used scripts to simplify these stages. 

6. ### Processes
Each process should be stateless, share nothing with each other, and persistent data should be stored in a database. Specifically, the state is transfered in requests and not stored in the web server. From my understanding, these states don't apply to sessions which are stored in clients as cookies. This concept seems to go in line with a REST applications and helps with scaling the application. 

7. ### Port Binding
The app should be self-contained and should not depend on runtime execution. It listens to requests and sends data through the port bindings. Along with processes, this one seems to be similar to a REST application and Rails can usually do this for free. 

8. ### Concurrency
The application should be thread-safe or support concurrency meaning multiple processes could be added. I'm still struggling with the idea of what kind of code is thread-safe in Rails and how Rails implements concurrency. I've read that Rails uses concurrency by making sure that threads don't share the same data when they're run or lock them when they do to reduce interference but I don't know where this happens in the framework. 

9. ### Disposability
Apps should have a fast startup and graceful shutdown. The former implies that less data or processes would be needed for the application to start and the latter implies that the app won't need a specific process every time it shuts down. Both parts make concurrent requests more effective and durable from errors. Specific implementations of this would include blocking a new request if the older one is still going or reconnecting  when the connection is lost. 

10. ### Dev/prod parity
This involves keeping development and production as similar as possible. This helps with continuous deployment by keeping changes small so they can be pushed to development quickly, having developers work on both stages, and keeping the tools/dependencies as similar as possible. For example, the development side should use the same type of database and the environment could be handled by a virtual machine through vagrant to make sure that everything works on the same machine.

11. ### Logs
Treating logs as an event stream enables them to be stored in a third party service instead of a specific log file. This is useful when the app is deployed to multiple places and all the logs would be handle by one service. 

12. ### Admin Processes
Administration processes like migrations should be handled as a one off process and in an identical environment as production. This is usually done through deployment scripts. I'm still learning how to deploy an app effectively so this one is still a work in progress. 

##Further questions 
* Why adding the ruby gem foreman into the Gemfile is not recommended?
* How does Unicorn interact with Rack Applications ? 
* What are the major differences between Unicorn, Thin , Puma and other Rack web servers ?
* How does concurrency and thread-safe work in a Rails?
* How to configure a deployment through environment variables?
* What are the best practices for deploying a Rails application?