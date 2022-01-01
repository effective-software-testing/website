---
title: "Do unit tests make refactoring harder?"
layout: post
---

A point often raised by those that prefer integration tests over unit tests is that _unit tests make refactoring harder_. By harder, they mean that a small change in the production code may require you to make lots of updates in your test code.

This is a super valid point. If you change the signature of a method, you will have to update all the calls to it from your unit test code; if you change the entire implementation of a functionality, you probably won't need to change a single line of your system tests. **The closer your tests are to the implementation the more sensitive they are to changes.** 

Should I then stop writing unit tests? Well, each test level has its pros and cons. Unit tests are more prone to changes, but they are also much cheaper, faster, and easier to write than integration or system tests. I discuss these trade-offs and when I prefer to go for one or the other with more depth in Chapter 1 of my book, and so I'll skip them here.

In a nutshell, I am still a big proponent of unit testing. If you can unit test something, you should. The question is: _how can we make unit tests a bit more refactoring-friendly?_

* Make your units really small. If they are small, propagating changes won't be such a burden.
* Make your test code to depend only on what it really needs.
* If you know a class will be used in many different test suites, apply  design patterns and best practices to reduce coupling. Entities, for example, are commonly spread among different test suites, and the Test Data Builders help you in reduce the coupling.
* Unit testing doesn't necessarily mean testing one class only. If you have a set of small cohesive classes that work together to deliver one feature, you may want to exercise them together. (Note that I consider integration test a test that goes beyond the borders of our system, e.g., they consume a web service or a database; I consider testing two or three classes together still unit testing).

A final note: breaking tests are not always bad. Tests that break when something changes can help you revisiting the pieces of code where this change will be propagated to. Think of a method that just had its signature changed. A bunch of tests will not even compile anymore. However, revisiting the tests in which this happened helps me in revisiting what impact this new method signature will have in the relevant classes of my system. In a way, the breaking tests are calling my attention to specific parts of the code and saying: _"hey, please, revisit this!"_. Clearly, you do not want hundreds of tests doing that, but just the right amount.

Happy refactoring!

