---
layout: post
title: More debugging with deployment
---
While I was experimenting with the
[dotenv-heroku](https://github.com/sideshowcoder/dotenv-heroku) gem, the app I
was deploying started showing the app crashed error message. I ran all my tests
before pushing the code to heroku so I was sure that the problem had something
to do with the configuration.

## First suspect: Devise secret key
Since I had just extracted the secret key for Devise into an environment
variable, I thought that the problem was because the Rails app was throwing an
error since Devise couldn't read the environment variable. I undid my commit
but the app still wouldn't start. I added
[heroku-repo](https://github.com/heroku/heroku-repo) to see if the problem could
be fixed by rebuilding the repository with different keys for the environment variable. 

## Second suspect: database.yml
I tried to see if I could access the app from the command line. I ran `heroku run rails console`
and received the error:

* active_record/connection_adapters/connection_specification.rb:37:in \`initialize': undefined method \`tr' for nil:NilClass (NoMethodError)

That led me to question if my configuration in the `database.yml` was wrong or that
the yaml file wasn't properly formatted. I played around with different settings
with no luck. After searching through articles and Heroku's
[devcenter](https://devcenter.heroku.com/articles/heroku-postgresql#connecting-in-ruby), I
found out that Heroku bypasses that file and only needs the url for the
database. 

## Third suspect: DATABASE_URL
The corresponding method was: 

    def initialize(url)
      raise "Database URL cannot be empty" if url.blank?
      @uri     = uri_parser.parse(url)
      @adapter = @uri.scheme.tr('-', '_')
      @adapter = "postgresql" if @adapter == "postgres"
      if @uri.opaque
        @uri.opaque, @query = @uri.opaque.split('?', 2)
      else
        @query = @uri.query
      end
    end

Since the first line wasn't raised, the url was not blank. The method was
reading the `DATABASE_URL` variable but was having problems afterwards. Something
was happening in the next two lines. The instance variable `@uri` was calling a
method: 

    def uri_parser
        @uri_parser ||= URI::Parser.new
    end

`URI::Parser` is part of a Ruby standard library that deals with a string of
characters representing a [uniform resource
identifier](http://en.wikipedia.org/wiki/Uniform_resource_identifier). The
`uri_parser` method instantiates a new URI object and the `parse` method then
tries to create a uri object from the `url` passed in. The `@adapter` tries to read
the resulting variable with the `scheme` method and that was when the `tr` method
throws an error because scheme can't read the object. After reading the
documention for the [parse
method](http://ruby-doc.org/stdlib-2.2.1/libdoc/uri/rdoc/URI/RFC2396_Parser.html#method-i-parse), 
I realized that the `DATABASE_URL` variable that was set in the environment was
not properly formatted. 

## Solution
At some point when I first tried to push the `.env` file to Heroku, the url
changed and the colon characters turned into equal characters. I'm not sure
if the dotenv-heroku gem did this but I exchanged the gem for
[heroku-config](https://github.com/ddollar/heroku-config)
instead and set the variables that way. 

## Easier way to debug
I realized later that above the initialize method was an example comment: 

        # == Example
        #
        #   url = "postgresql://foo:bar@localhost:9000/foo_test?pool=5&timeout=3000"
        #   ConnectionUrlResolver.new(url).to_hash
        #   # => {
        #     "adapter"  => "postgresql",
        #     "host"     => "localhost",
        #     "port"     => 9000,
        #     "database" => "foo_test",
        #     "username" => "foo",
        #     "password" => "bar",
        #     "pool"     => "5",
        #     "timeout"  => "3000"
        #   }

If I read the example for the url I would have seen that the `DATABASE_URL` was
not properly formatted. I appreciate that I'm now able to dig into Rails to figure out
what's wrong, but reading the error message and corresponding comments carefully could have
saved me hours of time. A lesson learned for the next time I have problems
pushing environment variables.

## Links
* [Summary of Ruby
Collections](http://6ftdan.com/allyourdev/2015/03/26/different-collection-types-in-ruby/)
This was an interesting article on Ruby collections, which I feel is the type
of object that I use the most. Most of it is a refresher but I did learn that
Ruby has tuples in one of its libraries and how it could be used. 

* [Intro to Devise](http://www.sitepoint.com/devise-authentication-in-depth/)
This link was also a little bit of a refresher but it's very thorough and it did
go through how to configure the mailer with [delayed
job](https://github.com/collectiveidea/delayed_job). Also, the
[author](http://www.sitepoint.com/author/ibodrov/) is
doing a whole series on authentication with Rails and I'm looking forward to the
next one. 

* [Rails API
tips](https://blog.jalada.co.uk/tips-when-writing-an-api-in-ruby-on-rails/)
I've been trying to learn more about creating a Rails API that could go with a
Javascript frontend and this artcle gave really good tips about problems I
didn't consider. I'm particularly interested in learning about the two
Rack middlewares he suggested; [rack-cors](https://github.com/cyu/rack-cors) and
[heroku-deflator](https://github.com/romanbsd/heroku-deflater). 

* [Regex](http://tom-lord.weebly.com/blog/reverse-engineering-regular-expressions)
This post goes deep into how a regular expression is parsed. The author was
explaining how he structured his
[gem](https://github.com/tom-lord/regexp-examples) to create regex examples. 
