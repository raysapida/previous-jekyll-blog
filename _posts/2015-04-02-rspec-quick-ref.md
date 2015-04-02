---
layout: post
title: Rspec Quick Reference
---
I've been working to rewrite the test suite for one of the apps I've made from
Minitest/Fixtures to Rspec/Factory Girl. My favorite thing about Minitest is
that it's simple to understand since it's just Ruby, but I wanted to explore what
Rspec has to offer. I've seen alot of
Rspec in the open source projects I've looked into and in many of the tutorials
I follow. Even though the syntax is easy to understand, using it to code was
harder than I thought. I started a quick reference sheet from cheat sheats I
found on the internet and the documentation for the gems. They don't give a full
explanation on what they do, but I found that the syntax is expressive enough
that being able to see an example is enough to use it.

##Structure

    describe <class> do
      it "description of what happens" do 
        <setup code>
        <exercise code>
        <expectation code>
        <cleanup code>
      end
    end

## Setup code

    before { <setup code> }
    let( <variable> ) { <object instantiate> }

    ## Test doubles
    book = double("book")
    book = instance_double("book")
    allow(book).to receive(:title).and_return("The Rspec Book")
    allow_any_instance_of(Widget).to receive(:name).and_return("Wibble")
    spy("invitation")
    instance_spy("invitation")
    class_spy("invitation")
    object_spy("invitation")

## Exercise code

    ## Model Tests from shoulda-matchers gem documentation

    it { should <should-matchers code> }

    allow_value('http://foo.com', 'http://bar.com/baz').for(:website_url)
    validate_confirmation_of(:email)
    validate_length_of(:password).is_at_least(10).on(:create)
    validate_numericality_of(:age).only_integer
    validate_presence_of(:password)
    belong_to(:organization)
    accept_nested_attributes_for(:mirrors).allow_destroy(true)
    have_many(:friends)
    have_one(:partner)
    have_and_belong_to_many(:awards)

    ## Controller Tests

    get :new

    Article.should_receive(:new).with(title: 'The New Article Title').and_return(article)
    post :create, message: { title: 'The New Article Title' }

    article.should_receive(:save)
    post :create

    article.stub(:save)
    post :create
    response.should redirect_to(action: 'index')
    flash[:notice].should eq('The article was saved successfully.')

    ## Feature Tests with Capybara

    visit book_path
    fill_in 'Email', :with => 'user@example.com'
    click_on "Submit"
    click_link('Link Text')
    choose('A Radio Button')
    check('A Checkbox')
    uncheck('A Checkbox')
    find_field('First Name').value
    find_link('Hello').visible?
    find_button('Send').click

## Expectation code

    expect(<expectation code>).to      eq(<value>)
    expect(<expectation code>).not_to  eq(<value>)

    ## Paired with spy

    expect(invitation).to have_received(:accept).with(mailer)

    # Values that can be used 

    be_true
    be_false
    be_nil
    match /regex/
    start_with 
    end_with
    match_array [array]
    be_a_kind_of <class name>
    be_an_instance_of <class name>
    have(<number>).things
    have_at_least(<number>).things
    have_at_most(<number>).things
    raise_error <optional error>

    ## Controller specific

    assigns[:article].should be_a_new Article
    response.should render_template :new

## Thoughtbot articles on testing
I've been reading about testing philosophies and watching tutorials on
TDD. I've been going through a lot of the blog posts on the thoughtbot because I
started learning about Rspec in general from their Upcase trails and using many
of their tools. These are a few of the articles I've read that helped me get a
grip on the way people test and the terms they use.

* [Unit
  Tests](https://robots.thoughtbot.com/back-to-basics-writing-unit-tests-first)
* [How to test Rails apps](https://robots.thoughtbot.com/how-we-test-rails-applications)
* [Mystery Guest](https://robots.thoughtbot.com/mystery-guest)
* [Stub External
  Services](https://robots.thoughtbot.com/how-to-stub-external-services-in-tests)
* [Fake Objects](https://robots.thoughtbot.com/fake-it)
* [Test Spies](https://robots.thoughtbot.com/a-closer-look-at-test-spies)
* [Acceptance
  Tests](https://robots.thoughtbot.com/acceptance-tests-at-a-single-level-of-abstraction)
* [Testing Environment
  Variables](https://robots.thoughtbot.com/testing-and-environment-variables)
* [Test Outside-In](https://robots.thoughtbot.com/testing-from-the-outsidein)
* [Selectively Avoid Factory
  Girl](https://robots.thoughtbot.com/speed-up-tests-by-selectively-avoiding-factory-girl)


## Commands I've learned
* `git log --grep` searches the commit messages
* `git log -S` searches the code in the repo and can take Regex
* `tar xvf archive_name.tar` extracting from a tar file
* `unzip test.zip` extracting from a zip file

## Links 
* [Functional Programming and Ruby](https://www.youtube.com/watch?v=5ZjwEPupybw)
This video was showing functional programming principles that I've been seeing
more and more when I looked into open source projects. This mindset for
programming has been difficult to wrap my head around but I can see a lot of
uses for it.

* [Using Ruby
  Forwardable](http://vaidehijoshi.github.io/blog/2015/03/31/delegating-all-of-the-things-with-ruby-forwardable/)
 contains ways to use the delegation pattern with the Forwardable
module. 

* [7 Unusual
  Datastores](https://blog.engineyard.com/2015/seven-unusual-ruby-datastores)
 shows datastores I'm not too familiar with like Marshal and ObjectSpace. I have
read that the latter is used for finding things like memory leaks or
benchmarking to figure out a good garbage collector setting. 

* [Keyword
  Arguments](http://www.justinweiss.com/blog/2015/03/30/fun-with-keyword-arguments/)
 introduced a way to use keyword arguments in Ruby 2.0+. I've been using the
older syntax all this time so finding out about this one has been great. It
also goes into different ways you could use it. 

* [Rails enums](http://6ftdan.com/allyourdev/2015/03/31/rails-4s-awesome-enums/)
 talks about the enum method in Rails 4 which I've seen a few times but never
really looked into completely.
