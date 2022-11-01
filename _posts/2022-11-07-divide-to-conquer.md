---
title: "Divide to conquer"
layout: post
---

In enterprise systems, especially those that are a little distributed, a common argument against unit testing is that "in real life, most bugs occur when apps communicate with each other". This might be true, although I like to see the problem a bit differently. After all, integration tests in distributed apps are always expensive.

Let's break this discussion down in two parts. First, to ensure the functional correctness of the application. Imagine a simple distributed app, where your Checkout system does something and then makes a call to the Inventory system that does something else.

We can ensure the correctness of both the Checkout and Inventory systems through cheap and easy-to-write unit tests. How to achieve that? We simply mock the external systems. Both systems probably have business rules, which we strongly exercise. Both systems also have interactions with other systems, which we test by ensuring that the expected interaction is correct (e.g., by verifying the correct interaction with the mock).

If you feel unit testing like this is not enough to ensure the correctness of the functionality, it might be because the contracts between the applications isn't clear. After all, if they were clear, testing that the right information is passed to the other app, or that the other app returns a specific type of data structure given a certain input should be more than enough.

This is key when trying to focus on unit testing. Unit testing in these type of systems works because we _trust_ on the contract we defined between the two parties.

Second, of course, when you distribute your application, you introduce new types of challenges. Say, the app may be unavailable or too slow or flaky. You can sure test for these things as well, but note that you are not testing the functional requirements anymore. This is just a different type of testing. 

The beauty of separating these two things is that you can be more productive. You can write lots of simple unit tests for the functional part of the application. This gets even better when the business rule is complex, as you can write tests for the so many different paths in a cheap way. 

Once you are done with the functional testing, you then focus on exercising all the magic that needs to exist in such apps. You may not need dozens or hundreds of tests like this, maybe a bunch will do. Maybe you have a mechanism that handles these things for all your APIs, and a single set of generic tests is enough. 

Third, can we trust that the contracts are stable? Maybe yes. If this app is developed by just a few developers or teams, good communication may be your main way of finding that a contract will change. If that's not enough, you may go for things like Consumer-Driven Contracts or Contract Testing (a topic for another post).

The thing is: if we try to test everything at once and altogether, we are doomed to fail. It's just too hard and complex. We have to divide the problem so that we can (more easily) conquer it. Focus on identifying and isolating the parts you can properly test with simple (unit) tests. Let complex testing be just a small part of the whole.