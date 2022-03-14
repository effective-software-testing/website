---
title: "Should my end-to-end tests never stub stuff?"
layout: post
---

My PhD supervisor used to say what words like **always** and **never** should *never* be used in software engineering.

So, should my end-to-end tests *never* stub stuff? Well, it can "stub stuff", it that's gonna help you. Why not?

Remember it's all about **what you want to test**. If you are writing an end-to-end test, but your goal is not really exercise that other component, and your test wouldn't be missing much if that component isn't the real one, then, stubbing it is fine, if you ask me.

*Oh, but then this is not an end-to-end test anymore.* Well, by the book, it is not. But it's ok. The three types of test levels we commonly use (unit, integration, and system/end-to-end tests) are there to guide us more than restrain us.