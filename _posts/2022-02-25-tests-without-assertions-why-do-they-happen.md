---
title: "Tests without assertions: why do they happen?"
layout: post
---

Have you even seen a test without assertions? If you work on large complex systems, then I'm sure your answer is a _yes_.

We all know that **tests without assertions aren't testing much**. After all, they may pass even if the behavior isn't as expected. The question then is: if we all know tests should have assertions, why do we see tests without them?

Maybe the simplest reason is that the developer wanted the test to break in case the production code throws an exception. Sure, this works. If no exceptions are thrown, the test will pass. If an exception happens, JUnit will make sure to fail the test. 

In such cases, I always ask myself: isn't there something to be asserted in case the behavior is as expected? Think of some batch job that summarizes the billing of customers with due date of today. Can't the test assert that the invoices were generated correctly?

Tests that just expect the production code not to break are often weak. We want the opposite: tests with strong assertions that would capture any small deviation from the expected behavior.

Now, I fear the **most common reason for tests without assertions is lack of observability**. It is so hard to observe the output of the program under test, that developers simply can't write assertions, even if they want to.

Think of the batch job example again. To ensure that the invoices were generated correctly, the developer needs to make two or three HTTP calls to different services. Or maybe the batch job simply writes files on the server, and there's no easy way to read them.

Bad observability tends to happen more often in integration and system tests where you have multiple components and external parties working together. I'll repeat the advice I give in the _Larger Tests_ chapter of my book: **you should invest heavily in test infrastructure**. 

For this particular batch job example, you may create an API that hides all the complexity of interacting with the many web services. From the test code, all the developer would then need to do is to call a method, say, `getGeneratedInvoices()`, and the generated invoices are collected from the many services.

You may spend some time building it, but once such an infrastructure is in place, writing such tests will be much easier. And more importantly, your tests will have proper strong assertions.

To sum up: the lack of observability may cause developers to write tests without assertions. A good test infrastructure is key to solve the issue. 


