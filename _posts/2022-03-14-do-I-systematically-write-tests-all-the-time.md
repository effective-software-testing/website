---
title: "Do I systematically write tests all the time?"
layout: post
---

**No, I don't!** But maybe my book gives this impression, doesn't it?

Most of the code we write isn't that complex. Think about it. Most methods you probably wrote in your life have just a few lines of code and it doesn't go beyond a for and an if statement. Empirical software engineering research, in fact, backs up this sentence (see Herraiz et al.). Most methods in software systems are simple.

In such methods, I don't really feel the need for a more formal specification-based and structural testing, as I explain in chapters 2 and 3 of my book. I don't explicitly write down the categories and partitions for each of the inputs and output variables. 

Why not? Because, due to the simplicity of the method under test, I can quickly see all the test cases I have to write. A short method can't do much anyways, so it's clear to understand what it does and what I should test for. 

My knowledge in testing overall does help me, so, if I see an if statement, I automatically think about branch coverage and I know I have to perform boundary testing on the condition.

The beauty of the more formal and systematic specification and boundary testing techniques I discuss in the book is that **I can go for it whenever I feel I need it**. If I'm uncomfortable and I need more help testing, I go for it.


*References:*

Herraiz, I., German, D. M., & Hassan, A. E. (2011, July). On the distribution of source code file sizes. In ICSOFT (2) (pp. 5-14).