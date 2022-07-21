---
title: "Use case vs unit testing"
layout: post
---

Deciding which level to write your tests is always a hard decision. 

On one hand, you may go for fine-grained unit testing, where you exercise one class or even method isolated from the rest of the system. Advantages? 

* This makes your tests much easier to be written, as the unit under test is small. 

* It also makes things much easier to be controlled, as this class probably depends only on a handful of other classes, and mocking is straightforward. 

However, as always, disadvantages exist:

* Exercising a single unit out of the so many that altogether compose the feature may not give you the best feedback in terms of whether the feature works or not as a whole.

* The more fine-grained you go, the more likely you are to write tests that are too coupled with the implementation.

On the other hand, you can test large parts of feature, say, 3, 4, 5 classes altogether, or an entire Service that contains the entire business rule. Advantages? Also a few:

* Your tests now exercise the system in a more realistic way.

* The test cases themselves are closer to the real use case of that feature. 

* The tests are not coupled to the implementation. You can change your production code and your code will not break.

The disadvantages are:

* Use case tests are harder to be written, and in most cases, you will need some infrastructure in place so that developers are productive in writing them. Think of ways of putting data into the database, injecting mocked components in deeper places, etc.

* Exercising every single branch of the implementation of the so many components that compose the feature might be costly. A test that could be written in 30 seconds via unit testing now takes minutes. 

As always, there's no right choice here. My personal decision making process goes as follows:

* If a single unit is business logic heavy, I unit test it. This gives me full control over the unit under test, and I can exercise it from multiple different angles and reach all the branches I want.

* If the unit is not business logic heavy, but does more, e.g., control flow, I consider not unit testing it. Why? The test will end up being just a bunch of mock assertions. 

* Whenever I'm writing unit tests and I feel there's a lot of duplication between the test and the production code, I consider not unit testing it, but go one level higher.

* I always go for use case testing, at least for the main expected and unexpected business flows. The architecture and design of the system should help in making these tests easier to be written. 

* When writing use case testing, I do not focus on covering every single branch of the execution. If I do want to cover every single branch, I consider going more fine-grained and write unit tests.