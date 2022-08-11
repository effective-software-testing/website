---
title: "'I would have found this bug with E2E tests' is a fallacy!"
layout: post
---


No, you would not! 

This statement is a common response I get back from engineers whenever I advocate for more unit (or at least “a bit less E2E") tests.

The proponents of “more E2E tests” are right in the sense that you may be able to reproduce bugs that can't really happen in more isolated tests. However, in practice, focusing your test suites more on E2E tests will not help you in find more bugs. In fact, I would argue that focusing solely on E2E tests can actually have the opposite effect, meaning, you will find less bugs. Let me tell you why. (Warning: this is purely based on opinion and experience, no real scientific evidence here).

Imagine two teams, both developing the same system. One team, however, focuses on unit testing, and the other team focuses on E2E testing.

Let's start with team one, which prefers unit testing. This team also writes of integration tests whenever it makes sense (say, to test a use case that interacts with a database), but doesn't really write lots of e2e tests (say, they never make network requests to other services, they always mock them). 

Because writing these tests tends to be cheap and fast, the engineers produce lots of unit (or more isolated) tests per day. Pull requests with use cases are full of tests. These tests exercise lots of different boundaries and corner cases (if you don't know how to systematically look for boundaries, take a look at my book). These tests also run super fast, which means developers can run the entire suite in their machines, and their CI pipeline gives feedback in just a few minutes. 

This team eventually observed a bug in production that they couldn't predict during testing. This bug happened because of a complex interaction between two of the services, say, for a rare input, service 1 returned something that service 2 wasn't really expecting. The team understands the problem (they have good monitoring in place!), then go back to their test suite and improve the tests by, say, better specifying the mocked behaviour of the dependency. Writing this test is again cheap and it takes only a few minutes. This bug never comes back again. 

Now, to the second team that prefers to exercise their use cases via E2E tests. They have very little unit tests. Because this is their focus, this team have spent good energy in creating some decent infrastructure so that writing these tests isn't that hard. 

But still, writing tests take more time from developers. After all, given that the test touches many different parts of the system, setting up the test means making sure all the systems are in the right state when the test starts. If the use case requires the interaction of three different services, engineers have to put these three apps up, populate their databases with different data, and observe that the three systems operated as expected. 

Because of this, exercise every little branch, boundary, or corner case of the system is much harder. After all, exercising every single if statement via E2E tests is too hard and costly. These tests are also quite slow to run and require a lot of configuration in the engineer's machine. Because of that, they often only run a subset of tests in their local environment, and let the CI run everything. The CI takes a few hours to run the entire suite, and so, feedback comes only a bit late.

Now, surprise surprise. This team also observed the same bug as team 1. Why? Well, because thinking of test cases that exercise rare behaviour is tricky, regardless of the test level you pick. If the engineer could have predicted this bug, they would have not written the bug (or would have written a unit or E2E test) in first place. 

Sure, maybe team 2 had a better shot at finding it due to their strong E2E testing mindset. However, again, it is more up to the engineer to identify places where bugs can happen rather than some super magic that E2E tests do.

Maybe, and that's just a pure opinionated guess, team 1 would even have higher odds of finding it in practice. After all, it's so cheap to exercise different extreme cases in their unit tests, that engineers there have more time to invest on boundary and exceptional testing. Meanwhile, engineers in team 2 might still be too busy trying to write test cases even for the happy paths of the use case.

Don't get me wrong. E2E tests are awesome. And we need them to make sure things actually work in production. But you don't want to exercise every little boundary of your system via E2E tests. They are too expensive for that. Rather, you need an extensive test suite that gives developers a feeling of productivity and safety whenever they make changes, and that's more likely to happen in unit (or at least more isolated) tests. 