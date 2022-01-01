---
title: "Can we get fully rid of flaky tests?"
layout: post
---

Many things can cause tests to become flaky. Luo and colleagues shed some light on their causes after analyzing 201 flaky tests in open-source systems:

* Async Wait, Concurrency, and Test Order Dependency are the three most popular causes of flakiness.
* Most flaky tests are flaky from the first time they were written.
* Flaky tests are rarely due to the platform-specifics (i.e., they do not fail because of different operating systems).
* The flakiness is often caused due to dependencies on external resources and can be fixed simply by cleaning the shared state between test runs.

On top of that, I would add the inherent complexity of large-scale software systems. In those, too many things happen at the same time which you can't control. Think of integration tests that make use of a caching infrastructure. Once every a thousand runs, the caching infrastructure may fail for a second, and break your tests. You also might be stuck with some legacy architectural decisions, which makes things flaky.

The sad news is that, while we know a lot about the causes of flaky tests, rarely can we get rid of them for good. **The next best thing we can do is to extensively monitor for flakyness**.

Some ideas on how to do it:

* Detect flaky tests as soon as they happen. Gradle, for example, offers [features to report flaky tests](https://blog.gradle.org/gradle-flaky-test-retry-plugin).
* Configure your test pipeline to re-run the flaky test a few times. If the test passes at least once, consider not breaking the build and not preventing engineers from continuing the development. 
* Once a flaky test is detected, make sure the developers know about it. You may communicate the author of the test or the team or whatever your code ownership model recommends right away.
* Let developers know which tests are flaky directly in the code. In JUnit, you may want to tag them (`@Tag("flaky")`).
* If your testing execution pipeline is extensive, ensure that at least your unit test suite is free of flakyness. If you identify a flaky unit test, move it to another part of the pipeline.
* Identify the root causes of the flakyness, and either fix them or document them. Make sure developers are aware of the causes and avoid them in the next tests they write.

Good luck with your flaky tests!

**References**

Luo, Qingzhou, Farah Hariri, Lamyaa Eloussi, and Darko Marinov. "An empirical analysis of flaky tests." In Proceedings of the 22nd ACM SIGSOFT International Symposium on Foundations of Software Engineering, pp. 643-653. 2014.
