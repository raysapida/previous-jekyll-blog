---
layout: post
title: Learning specifics about testing
---
I've been working through the testing trails in upcase for test doubles and
testing fundamentals. The most difficult part for me was understanding mocks and spies along with how to
structure them to make sure the right behavior is being tested. I've
written unit tests and a few acceptance tests in the past but I've never used
test doubles before the upcase trail. I had to research the differences between
fakes, dummies, stubs, spies and mocks. Upcase provided an
[aricle](http://www.martinfowler.com/bliki/TestDouble.html) by Martin Fowler as
an introduction to those ideas. From my understanding, the advantages
of using test doubles are clarity and speed. The unit tests should already tests
that the proper answers are being given in the model or controller level which
makes stubs a good way to improve them. Mocks ensure that specific method calls
are being used and spies take that a step further by recording how the method
calls are used. For example, spies could say that a method call was used twice
instead of the expected once.

I've learned the definitions for different kinds of testing; unit,
integration, feature, and functional tests. Unit tests are for a small subset of the
application and I closely associate it with tests for a specific controller or
model. Integration tests go from end to end and I've used it to test that
logging in to an application or using the user interface. Functional tests are
integration tests that actually run the application from end to end similar to
making sure that an email is sent when a person is trying to recover a forgotten
password. Feature tests are for things that change the functionality of the
application like changing a status update from text only to including image
attachments. 

I'm also still getting used to rspec and capybara. The most prevalent comments I would receive from the
exercises were the different shortcuts people use in their tests and other
improvements on readability to make sure that the reader can better understand
the intent behind the tests. Most of my
tests in the past was using Minitest because it was included by default and
it was the framework most of the tutorials I followed use; it's the testing framework included with the exercism
exercises and the Treehouse tutorials for the Treebook application. I've never
really thought of tests outside unit testing but I'm appreciating what testing
adds to the application. I'm starting to see why tests can function as
documentation instead of comments and how bugs can be recreated to better
understand where edge cases are coming from.
