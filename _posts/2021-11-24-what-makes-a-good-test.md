---
title: "What makes a good test?"
layout: post
---

Writing good test code might be as challenging as writing good production code. In my book, I describe what the attributes that I like to see in them. 

In a nutshell:

* **Tests should be fast**. You want your tests to be fast. Slow tests make you feel unproductive. You tend not to run slow tests as often as fast tests, and that means less feedback.

* **Tests should be cohesive, independent, and isolated**. You want your tests to focus on one thing and one thing only. This may change if you are doing larger integration or system tests, but at unit level, you for sure want small cohesive tests. You also want them to not depend on other tests. Meaning, the test should be responsible for setting up everything it needs and clean up its mess.

* **Tests should have a reason to exist**. You only want tests that add something to your test suite. You know that test method you wrote for that _getter_ only because you wanted a higher coverage score? This is a good example of a useless test.

* **Tests should be repeatable and not flaky**. Flaky tests hinder the confidence of development teams. Is this test really breaking or is the test just being flaky? Can we deploy to production or not? I know that, in practice, it is hard to fully avoid them, but that should be our goal.

* **Tests should have strong assertions**. Tests are only as good as their assertions. We want our tests to be as strong as possible. If the code under test changes two things, you want to assert that these two things are as expected. You want your tests to ensure that any small breaking change in production is captured by the tests and that's only possible with good strong assertions.


* **Tests should break in case the behavior changes**. Tests are our best friend when it comes to letting us know if something changed. If the behavior of the system changed, you want to see a breaking test. Breaking tests are not always that bad, especially when they give us useful information.


* **Tests should have a single and clear reason to fail**. This is somewhat related to tests being cohesive. We want our tests to scream why they are failing. We do not want developers to have to re-execute or add debugging lines to understand what's going on. 

* **Tests should be easy to write**. You write tests every day. Every hour. Every minute maybe. You are going to write hundreds of tests. You do not want writing tests to be a pain. You want it to be easy. If it's not easy, maybe your code isn't as testable as you thought it was.


* **Tests should be easy to read**. You write the test just once but you (and your colleagues) read it multiple times. You want a developer, in a split second, to be able to understand what's being tested. 

* **Tests should be easy to change and evolve**. Your production code changes and evolves super fast, which means your tests should also follow the pace. If a single change in production code means hours of changes in test code, you are doing it wrong.


In my book, I dive more into each one of these principles, and I give suggestions on how to achieve them. 

Can we _really_ achieve all of this? Well, it's super hard, and in practice, you will have tests that adhere more to these principles, and others a bit less. It is good to know, though, what the impact of not following a principle will be. You wrote a test that is not easy to read? You may pay more to comprehend it the next time you have to maintain it. So on and so forth.

There are lots of other guidelines and best practices about test code. The works that inspired me the most throughout my career came from Gerard Meszaros and Kent Beck. I suggest you read their principles as well!

**References**


* Meszaros, Gerard. 2007. _XUnit Test Patterns: Refactoring Test Code_. Pearson Education.

* Beck, Kent. 2019. "Test Desiderata." https://medium.com/@kentbeck_7670/test-desiderata-94150638a4b3.



