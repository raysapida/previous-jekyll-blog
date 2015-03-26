---
layout: post
title: Easy Wins versus Hard Wins
---
One of the most difficult things for me was keeping up my motivation while learning how
to code. My biggest solution to this was something I learned from [The 7 Habits
of Highly Effective
People](http://www.amazon.com/The-Habits-Highly-Effective-People/dp/1455892823)
and that was a four quadrant chart separated into:

* Important and Urgent
* Important but not Urgent
* Not Important but Urgent
* Not Important and not Urgent

I used to write this chart every day as a way to manage my time but I focus on
the first two now and created two todo lists. The important and urgent category is always the 
priority but I further split the last one into easy wins and hard wins because
those are the challenges you can be flexible with it. 

One of
the things a lot of people have suggested is taking a deep dive into
programming, program 10 hours straight per day to quickly reach the 10,000 hours for mastery
mentioned in
[Outliers](http://www.amazon.com/Outliers-Story-Success-Malcolm-Gladwell/dp/0316017930).
That mindset disregards burnout and that is especially discouraging for a beginner.
It's one of those cases where the process is much more important than the goal
because of how overwhelming programming can be; there are a lot of things to
learn, it's important to be able to decide what abstractions are ok to work with
as is and what topics are uncomfortable enough to stretch your abilities
without breaking your motivations. Easy wins and hard wins is a way I manage
that. I focus on harder problems but I would do something from the easy category when I
knew that I needed a little break but also stay productive. It's very important
though to make sure that everything in that category is still important to
make sure that it's not another form of procrastination. 

## Example grouping for the categories
For me, the important and urgent category was filled with services I'm paying
for which included Treehouse, Codeschool, Upcase, and any other online
subscription or working on an app I can show as a code sample in the future. The important but not urgent category
had two subclasses. The easy wins includes learning a single command, an easy
code kata/exercise, or reading a chapter for a programming book. The hard wins
include reading source code to figure out how a method works, learning a
design pattern, or learning a new tool like a text editor or tmux. 

## Commands I learned recently
* `sudo update-alternatives --config editor`
The default editor for my laptop was nano and I wanted to switch to vim.

* When I was working on Windows 8 and Vagrant, I used a [program](https://windows.github.com/)
that GitHub provided. I knew a handful of commands
but I'm trying to learn enough so that I won't depend on the GUI.

* `git branch -a` 
This list all the branches for a git repo.

* `git branch -d branch_to_delete`
This deletes a branch. 

* `git remote add origin remote repository_URL`
This adds a remote repository I can push and pull to. 

* `git blame directory/to/file.rb`
I learned this from Justin Weiss's [blog
post](http://www.justinweiss.com/blog/2015/03/24/go-beyond-the-easy-fix-with-code-archaeology/)
and it's been useful to track down changes in git's history. 

##Links

* [Postgres management](https://www.digitalocean.com/community/tutorials/how-to-create-remove-manage-tables-in-postgresql-on-a-cloud-server)
A lot of the things in this article is taken care of by rails but I wanted to
learn more commands in psql so that I can poke around the database when I need
to.
 
* [Migrating Rails to Postgres](http://railscasts.com/episodes/342-migrating-to-postgresql?view=asciicast)
I knew how to set up Postgres but this page also added how to migrate data
from sqlite to postgres through the [taps gem](https://github.com/ricardochimal/taps). 

* [Adding blog to a rails app](https://exceptiontrap.com/blog/4-create-a-simple-jekyll-like-blog-in-your-rails-4-app)
I followed this article to add a blog into a rails app that uses markdown syntax.

* [Brakeman gem](https://github.com/presidentbeef/brakeman)
I was seeing this gem a lot in different blog posts and I wanted to try it out.
I still need to learn the [warnings](http://brakemanscanner.org/docs/warning_types/)
and what they mean but I was able to fix unsafe redirects and cross site
scripting with the first pass through. 

* [Setting up email in rails](http://www.gotealeaf.com/blog/handling-emails-in-rails)
This article went through how to set up emails in a rails app through Gmail or
Mailgun. I went through the first part and I want to see how to set up the other
in the future. 
