---
title: "When do I do TDD?"
layout: post
---

I have been doing TDD and test-first development for many years now. In fact, my [TDD book](https://www.casadocodigo.com.br/products/livro-tdd), the first one in Brazilian Portuguese, will celebrate its 10th anniversary!

After many years of practice, I now have a much more pragmatic view on when to do it:

* I go for TDD when I do not know very well how to design, architect, or implement a specific requirement. In such cases, I like to take it slow and use my tests as a way to experiment with the different possibilities. If I am working on a problem I know well and I already know the best way to solve the problem, I do not mind skipping a few cycles.

* I also use TDD when I am dealing with a complex problem or a problem that I lack expertise to solve. Whenever I am facing a new challenging implementation, TDD helps me in taking a step back and learn on the way. Writing very small tests enables me to learn more about the requirement.

* I do not use TDD when there is simply nothing to be learned in the process. Supposing that I already know the problem and I already know how to best solve it, I feel comfortable enough to go and code the solution directly. 

Note that, even if I do not do TDD, I am always writing tests promptly. I never leave it to the end of the day or to the end of the sprint. I code a bit of the production code, and then I code a bit of the test code. Whenever I face some trouble, I have no shame in taking a step back and slow it down.

The way I see TDD (and test-first) is that it is all about _creating opportunities for me to learn more about the code I am writing_. From an implementation point of view (does it do what it needs to do?) and from a design point of view (is it structured in a way that I want?). 

TDD gives me the chance to reflect on these points after every test case. But that is not the only practice I use to get quick feedback about something I am doing. In situations I have zero idea where to start, I also enjoy prototyping. In other words, I simply try out ideas by writing a bunch of code and reflecting on it. If I like what I did, I then throw it away and start again from scratch, now taking proper care of things I did not pay attention when coding the prototype (e.g. variable names, code comments). If I did not like what I did, I simply throw it away and try out another idea.

Why don't I do TDD in such cases? In some cases, where the complexity of the feature relies primarily on how to design the classes or how to make it flexible and extensible enough, I find it very hard to even know what the first test should look like. Even more than that: my mind already knows that that is the challenge ahead of me and knows that, once this is sorted out, the rest will simply follow. 

Let me give you a very recent example. We were about to develop some tooling that would grade our students' solutions (in fact, we were assessing the quality of their test suites – I did mention I teach software testing before, didn't I?). I knew in advance all the metrics I would like to have from their solution: different coverage metrics, mutation coverage, and a bunch of other checks that we have per exercise (e.g. did the solution mock the right classes?). I knew that the main challenge, design-wise, would be to ensure we could have as many assessment criteria and as many specific checks per exercise as needed.

What would my first TDD test look like? I could indeed have written the first one, focused on the business. Maybe something like "solutions with coverage higher than the established threshold are a pass". But that would not really help me in reflecting on the most complex part of the problem. I could also have started with something like "an exercise should contain its own set of checks", but that also would not help me in reflecting on the bigger picture. 

For me, it was simply easier to try out a bunch of ideas and pick the one I liked the most. That's precisely what I did. At some point, I liked the design idea, and I started to write tests to see how testable it was. Writing the tests forced me to change a thing or two in the initial design idea. See? The same outcome but done differently.

Now, maybe you could have TDD'd this problem out; I could not. In the end, it does not matter. What we need are ways to stop and think, to stop and reflect on what we are doing. TDD is a perfect way for that, but surely not the only one. 

Now, truth be told: over time, I started to prefer prototyping over TDD. Maybe because my mind already knows many of the patterns that make code more testable (which I discuss in Chapter 7 of my book) and so, although not really writing the test first, I feel I take similar (if not the same) decisions. 

Deciding when to TDD or not will come with experience. Unfortunately, there is no silver bullet in software engineering (as far as we know). My book has a chapter on TDD, which I hope you find useful and pragmatic!
