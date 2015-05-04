---
layout: post
title: Vim Cheat Sheet
---
Lately, I've been envious of graphic text editors and the way they navigate
through project files. I've been doing a lot of tutorial projects in Ruby and 
Javascript along with cloning documentation from github as a reference offline.
I downloaded [atom](https://atom.io/) to accomplish this but I'm sacrificing the
speed of working with a vim/tmux setup. After watching Upcase's latest Weekly
Iteration on Vim, I decided to try achieving a deeper understanding of Vim's
capabilities.

## [Rails Vim commands](http://www.sitepoint.com/effective-rails-development-vim/)

* `:PluginInstall` - Install Vundle plugins

* `gf` - Go to File

* `CTRL + o` - Go back to the previous file

* `CTRL + i` - Go forward in visited files

* `:jumps` - List visited files

* `RcontrollerJump` - to relevant controller, as if you are in a model file, and you want to jump to its controller.

* `RmodelJump` - to the model

* `RviewJust` - add the name of the view like (index, show, edit) to jump to the relevant view.

* `RunittestJump` - to the relevant unit test.

* `RfunctionaltestJump` - to the relevant test.

* `RintegrationtestJump` - to the integration test, integration spec, or cucumber feature specified.

* `RspecJump` - to the given spec.

* `RmigrationUse` - tab completion to choose from the available migrations and jump to one of them.

* `RschemaJump` - to the project schema.

* `RmailerJump` - to the given mailer.

* `RhelperJump` - to the given helper.

* `RjavascriptJump` - to given JavaScript or CoffeScript file.

* `RstylesheetJump` - to given stylesheet.

* `RtaskJump` - to given task.

* `RlibJump` - to given lib, if no arguments specified it jumps to the Gemfile.

* `RlayoutJump` - to the layout of the current controller.

* `:RV` - Open files in vertical split windows

* `:RS` - Open files in horizontal splits

* `:RT` - Open files in new tabs

* `:RD` - Open files in current buffer

* `:Rgenerate migration add_something_to_tablename`

* `:Rserver`, `:Rserver!` and `:Rserver!-` - Running, Restarting, and Killing the Serve

* `:Rpreview` - Open the correct URL for the current file

## [Vim-rspec](https://github.com/thoughtbot/vim-rspec)
* `map <Leader>t :call RunCurrentSpecFile()<CR>`

* `map <Leader>s :call RunNearestSpec()<CR>`

* `map <Leader>l :call RunLastSpec()<CR>`

* `map <Leader>a :call RunAllSpecs()<CR>`

## Vim plugins to checkout
* [vim-snipmate](https://github.com/garbas/vim-snipmate) - Creates code
  templates

* [ag.vim](https://github.com/rking/ag.vim) - Searching similar to grep and ack

* [tcomment_vim](https://github.com/tomtom/tcomment_vim) - A plugin to comment
  out blocks of code

* [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) -
  Shortcuts for common ruby refactoring techniques

* [vim-bundler](https://github.com/tpope/vim-bundler) - Ability to run bundler
  from vim

## Commands I've learned
* `gem pristine --all --only-executables`

* `rails _4.1.0_ new respond_to_4.`

* `gem install rails -v "~>4.0.0"`

* `rake paperclip:refresh:missing_styles`

