---
title: "What do I mean by effective and systematic testing?"
layout: post
---

I would say that the main difference between my book and others out there is that I focus on _systematic and effective testing_. What do I mean by that?

Software testing is not something really new. Most developers today leave their bootcamps or university courses with already some knowledge on testing tools, such as JUnit or Selenium. If they don't, it's easy to find online material, courses, and books on the topic.

However, I fear that what's out there mostly focus on the _tooling_ part of writing tests. Meaning, how to use JUnit framework or the Selenium library, what the coding best practices are, how to use Mockito to generate mocks, etc. However, **very little is said about how to engineer the test case itself.** 

A lot of the books and tutorials follow the "gut feeling approach" when it comes to propose test cases. You test what you see: "Oh, there's an if there, let me write a test."

This approach is super dependent on the engineer writing the tests. Sure, senior engineers are very experienced and their gut feelings show them what should be tested. However, younger engineers can't fully rely on their gut feelings yet.

My book challenges this. It shows how one can follow **systematic** steps to generate test cases. In a nutshell:

1. Start by the **requirements** of the program or method under test. Break the requirements down into what's the input and what's the expected output of the program. Explore the different inputs we pass to the program, how they may interact with each other, and how they change the output. Generate tests for the right combinations of inputs and outputs.

1. Then make use of**structural testing and code coverage** to augment your test suite. What doesn't your test suite cover yet? Why not? Maybe you simply forgot it, you then write the test.

1. Explore possible **properties** of the program for which you don't want to write example-based tests, but stronger property-based tests.

1. If your unit is more complex and has (complex or expensive) dependencies, consider **mocking** them.

1. If your code can't properly be exercised via unit testing, go for **integration testing**. That may require you to write some infrastructure beforehand.

For each of the steps above, I provide a small and easy to follow recipe. My hope is that a less experienced developer, when following these recipes, _will_ engineer a test suite maybe as strong as the one from the senior engineer. 

True, _nothing replaces experience_, and the senior may see corner cases that are not clear in the requirements or the source code. Software engineering is _that hard_. But having a good enough test suite is always a good start, I would say.

What about _effectiveness_? Because the hope is that, if you follow the steps, you will produce an (effective) test suite that is strong enough to catch the bugs that matter, while skipping tests that don't really matter or add value. 

The idea of being as systematic as possible is not something new. It is, in fact, quite popular in the academic circles. Researchers have been trying to find systematic ways to identify all possible bugs of a software system for decades. My book just takes a more pragmatic approach on it. A lot of the specific techniques also comes from related work. My take on specification-based testing, for example, was highly inspired by Cem Kaner and colleagues as well as the paper from Ostrand and Balcer; the boundary testing technique I discuss in the book is based on Jeng's and Weyuker's paper. 

In a way, I think we all always wanted to have nice "recipes" to follow when it comes to software testing. Let me know what you think of mine!

References:

1. Kaner, Cem, Sowmya Padmanabhan, and Douglas Hoffman. "The Domain Testing Workbook". Context Driven Press, 2013.

1. Jeng, Bingchiang, and Elaine J Weyuker. "A Simplified Domain-Testing Strategy." ACM Transactions on Software Engineering and Methodology (TOSEM), 3 (3), 1994.

1. Ostrand, Thomas J., and Marc J. Balcer. "The Category-Partition Method for Specifying and Generating Fuctional Tests." Communications of the ACM, 31 (6), 2013.
