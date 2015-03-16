---
layout: post
title: Commands I needed to start using the Command Line
---
## Basic Commands

The [ls](http://ss64.com/bash/ls.html) command list the contents of the current directory. A more detailed
  form would be `ls -la` which lists the contents along with their file permissions.

The [cd](http://ss64.com/bash/cd.html) command lets you move back and forth from folders by adding the
  folder name afterwards. `cd ..` lets you move back by one folder and `cd -`
lets you jump back and forth between the last changed spots. 

The [mkdir](http://ss64.com/bash/mkdir.html) command makes a folder while [rmdir](http://ss64.com/bash/rmdir.html) removes an empty folder. 

[cp](http://ss64.com/bash/cp.html) can copy files where the the first group is the target and the second
  group is the destination.

[mv](http://ss64.com/bash/mv.html) moves files and works similarly to `cp` except the first group is
  deleted afterwards. 

The [rm](http://ss64.com/bash/rm.html) command deletes a file and passing in additional flags like `rm
  -rf` would delete a whole folder along with its contents. 

## Useful Commands

[man](http://ss64.com/bash/man.html) followed by another command would show the complete help
  section on how to use that command. Whenever I'm lost or forgot how to use a
particular command, I would use this to figure out how it works. 

[sudo](http://ss64.com/bash/sudo.html) can be prepended to other commands that need super user
  permission to execute. 

[chmod](http://ss64.com/bash/chmod.html) can change the file permissions of a file enabling you to edit or use
  thE FIle. 

[grep](http://ss64.com/bash/grep.html) lets you search through the file's or output's contents using a regular
  expression. There are other commands that other people use to perform the same
function but this is the most common one. 

[head](http://ss64.com/bash/head.html) and [tail](http://ss64.com/bash/tail.html) - Shows the first of last ten lines for a file or output.
  They're useful for logs and when piping a string of commands. 

[rails](http://guides.rubyonrails.org/command_line.html) has their own set of
  commands along with
[rake](http://edgeguides.rubyonrails.org/active_record_migrations.html#running-migrations) commands for migrations. I end up using [rails
console](http://guides.rubyonrails.org/command_line.html#rails-console) the most
when debugging a problem or exploring an application.

## Optional Commands 

[vagrant up](http://docs.vagrantup.com/v2/cli/up.html) and [vagrant ssh](http://docs.vagrantup.com/v2/cli/ssh.html) - I had a lot of trouble with setting up a development environment since I had a Windows 8 laptop. I
learned that [Vagrant](https://www.vagrantup.com/) was the easiest way to start
using a virtual machine at the time and I started with the [rails dev box](https://github.com/rails/rails-dev-box).

[rvm](https://rvm.io/rvm/cli) was how I managed my environments and it helped
  me separate incompatible gems. A Gemfile should manage most of
these but I had trouble figuring out where errors were coming from when
installing gems and this was an easier solution at the time. 

[vim](http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html) - I started with vim because I couldn't figure out how to share
  folders between the virtual machine and the local machine but I ended up
enjoying being able to quickly switch between the editor and shell so much that I stuck
with it. 

[tmux](https://robots.thoughtbot.com/a-tmux-crash-course) - I began learning this on an Upcase trail and using it finally
  convinced me to install a Linux distribution. It became more evident that developing in a virtual
machine was the bottleneck for me when I became comfortable
enough in a tmux session, especially when running tests. 
