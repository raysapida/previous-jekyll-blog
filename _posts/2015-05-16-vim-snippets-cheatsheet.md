---
layout: post
title: Snippets Cheat Sheet
---
I'm currently trying to use more of snippets in vim and this is a group of
commands that I think would help me out. These snippets are provided by two
different repositories and I installed
[vim-pathogern](https://github.com/tpope/vim-pathogen) to add more of my own in
the future.

## [honza vim-snippets](https://github.com/honza/vim-snippets)

### Rails
* `snippet resources` - Create resources controller class
* `snippet befc` - before create
* `snippet befd` - before destroy
* `snippet befu` - before update
* `snippet befv` - before validation
* `snippet defcreate` - def create - resource
* `snippet fina` - find(:all)
* `snippet defi` - def initialize
* `snippet class` - class <class_name> def initialize ... end end

### Markdown
* `snippet link` - Link to something
* `snippet img` - Image
* `snippet ilc` - Inline Code
* `snippet cbl` - Codeblock

### Html
* `snippet body` - body tags
* `snippet div` - div tags
* `snippet div.` - div tags with class
* `snippet div#` - div tags with class and id
* `snippet p` - paragraph tags
* `snippet ul` - unordered list tags
* `snippet li` - list item tags

## [r00k dotfiles](https://github.com/r00k/dotfiles)

### Ruby
* `snippet =b` - comment code block
* `snippet req` - reuire statement
* `snippet case` - case when statements
* `snippet def` - def method with end
* `snippet if` - if statement
* `snippet ife` - if else statement
* `snippet elsif` - elsif statement
* `snippet Enum` - include Enumerable and create each method
* `snippet Comp` - include Comparable and create spaceship method
* `snippet defs` - def self. statement
* `snippet ea` - each method
* `snippet eai` - each with index method
* `snippet inj` - inject method
* `snippet map` - map method

### ERB
* `snippet p`
* `snippet pe`
* `snippet end`

### Rspec
* `snippet new` - test double with allow
* `snippet desc` - describe block
* `snippet it` - it block
* `snippet con` - context block
* `snippet bed` - before block
* `snippet hc` - expect page have content
* `snippet let` - let block
* `snippet ex` - expect to
* `snippet scen` - scenario block
* `snippet rrh` - require rails helper

## Commands I've learned
* `rails new api -T -d postgresql` - The -T is the same as  --skip-test-unit
* `rails new bostonember -B -S` - Skips bundle install and sprockets
* `FactoryGirl.create_list(:contact, 10)`
* `rails g model Account name:string subdomain:string --skip`
