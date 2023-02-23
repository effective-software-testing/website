---
title: "Unit or integration tests? It doesn't matter!"
layout: post
---

I remember back in the early 2000s when the different user groups would have long e-mail threads about "what constitutes a unit test?" or "unit or integration test, which one is best?". This made a lot of sense back then. However, in 2023, I think we should be past this discussion.

As long as tests **run fast**, **are easy to be written**, and **give good feedback**, we are fine.

**Tests should run fast.** Tests that take too long to run, or tests that require a lot of computational power, won't be executed as often. Developers won't be able to run them "at every second" as they often do with cheap tests. Infrastructure engineers may also have a hard time configuring the CI, as your company may not have all the infrastructure required to run the expensive test thousands of times a day. _If the test runs fast, you are fine._

**Tests should be easy to be written.** If tests aren't easy to be written, developers won't do them. I [wrote about it](https://www.effective-software-testing.com/it-has-to-be-easy) in a previous edition of this newsletter. Unit tests tend to be easier to be written, but if what you need is a more integrated test, you can achieve the same by providing developers with easy ways to write them. _If the test is easy to be written, you are fine._

**Tests should give good feedback**. A good test breaks as soon as the feature stops working. Sometimes we can get good feedback when we test a class in isolation from the rest. Sometimes, we get even better feedback if we test "two classes" together. _As long as you are confident that the test is giving you a sound signal about your system, you are fine._

I am a big fan of testing individual units. Whenever I see a way to test a class in isolation from the rest, I do it. I find it to be the most straightforward way to exercise my code. However, in practice, I get myself writing tests that involve a bunch of classes together almost all the time. 

In most of the code I write, the only real barrier that prevents me from writing tests that are fast and easy to be written is access to external resources, such as an external web service. These I mock without even blinking. Putting 3, 4, or 5 domain classes altogether and calling the behavior under test tends to be simple if your classes are well-designed. Mocking them is even more work than not mocking them. 

What about databases? I rarely mock them as well. In the stack I use the most, Spring, it's so easy to spin up an in-memory database that I go for it. Maybe even easier than mocking up everything. The biggest challenge, mocking or not, is creating the right data so that the class under test can do its magic. To that, I invest in test data builders so that I can create complex entities with few lines of code. Persisting these entities in the database or configuring my stubs to return takes me the same amount of work.

How do I call these tests, that may exercise more than one class, that goes to the database, but mocks other external things? _Does it matter?_ As long as you are focusing on fast, easy-to-be-written, with good feedback tests, you are fine.

