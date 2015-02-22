---
layout: post
title: Reading The Rails 4 Way - part 1
---
When I was getting deeper into reading [The Rspec
Book](https://pragprog.com/book/achbd/the-rspec-book) a few weeks ago, I found
that I had difficulties when it came to information that wasn't included in the 
[rails guides](http://guides.rubyonrails.org/). I picked up [The Rails 4
Way](https://leanpub.com/tr4w) to rectify that. The book felt more like
documentation while I was reading it and that's very intentional. The breadth and
depth was impressive and I wanted to get a book that I could carry with me as a
physical documentation of the framework. I knew before reading it that I
couldn't memorize everything the book had to offer so I read it like I would
when I read Google Map directions, finding the general routes I needed and
making a mental note for things that I didn't need to know now but would
definitely look into once I reached that landmark. 

The first chapter dealt with a rails environment and configuration. Most of it
dealt with things I learned from other sources but I was introduced into the
specifics of bundler and other configuration details. This is the section I
learned to add gems into the vendor directory which I wanted to do because I
recently learned about ctags from Upcase's vim trail. This enabled me to jump
around my app figuring out how methods are called throughout the application. 
The next three chapters after that were also refreshers on routes, REST in
Rails, and controllers. 

There were five full chapters that dealt with active record split into general
active record uses, migrations, associations, validations and advance active
record uses. Active record deals with so many parts of Rails that I remember looking at the 
source code before and not getting where to begin. The book delved into the
database adapters for the most common relational databases and how Rails
interprets the types of data they use. During the rest of the chapters, what
stood out to me the most where how callback were used in the model, how
associations are made particularly polymorphic associations, and using indexes. 

The tenth chapter dealt with the action view part of Rails and introduced the
decent exposure gem. Most of it was a refresher dealing with methods available
in the view diretory, using partials, and rendering objects or collections. The
most useful part I learned was the `assigns` instance variable which shows what
is being communicated between the controller and view. 

