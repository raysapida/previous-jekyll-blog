---
layout: post
title: My favorite ruby gem
---
If I could tell myself one thing when I first started learning about Ruby and Rails, I would say use [pry](https://github.com/pry/pry). There are so many tutorials that I stopped halfway through because I couldn't debug it properly and Pry ended up helping me with most of them. In Rails, I've used `binding.pry` so much that I sometimes leave it as a comment in case I have to go through it again. The only misstep I've had while using it is including `binding.pry` directly into a `for` or `while` loop. In that case, each `step` usually goes through one iteration of the loop and using the `finish` command does the same thing. 

Also, since I've started doing coding challenges like [exercism](http://exercism.io/) and [codewars](codewars.com), I've used Pry to explore what I can do when solving problems. What I love the most about using it is that I can create a variable with the methods I'm using, `cd` into it, and use the `ls` command to view all the methods available. I could then use the `?` or `show-doc` commands to explore what each method can do. While learning how to use methods, I have a hard time figuring out how the object I pass changes and which methods could then be called on it. In my first iteration, I usually group methods by the type of object they become since the most common type of errors I've had are `ArgumentError` and `TypeError`.  As an added benefit, I could try out any code I want to write in the Pry before adding it to my project. That way, I could be sure that a problem exists somewhere other than the code I'm working on. 

I was introduced to both of these approaches in Rails Conference videos I've seen from YouTube and if either interest you, you can follow the following links below to learn more about it.  

[Ruby Conf 2013 - REPL driven development with Pry by Conrad Irwin](https://www.youtube.com/watch?v=D9j_Mf91M0I)

[RailsConf 2014 - Debugger Driven Developement with Pry by Joel Turnbull](https://www.youtube.com/watch?v=4hfMUP5iTq8)