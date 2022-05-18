---
title: "It's not about following a recipe!"
layout: post
---


One of my favorite testing techniques is _specification-based testing_. I learned it more formally a bit later in my career, and since then, I feel my tests are just much better because of it. I explain it already in chapter 2 of my book. However, a common misunderstanding for those that are just introduced to the topic is to believe that specification-based testing is all about following a recipe: _oh, I see an array, let me try a null array, an empty array, an array with one element, and an array with multiple elements, and I'm done!_

I can see where this misconception comes from. We are very used to do testing in an ad-hoc manner. The next test we write is just the next thing that comes to mind. My colleagues and I have even observed such behavior in a laboratory experiment [1]. 

Let me assure you that specification-based testing **is not** about following a recipe. **Specification-based testing is all about using the requirements of the program in a systematic way to derive test cases.**

What I like most about specification-based testing is that:

- First, it allows me to take a step back from the actual code. When we are too deep in the code, it is hard to really explore the program from a requirements perspective. Specification-based testing lets you "forget the code for a little bit" and just focus on what the program should do.

- Second, it gives me a systematic approach that I can use to guide my exploration. For example, I can look at the inputs of the program, and together with the specification, explore the different expected behaviors of the program.

- Third, it gives me a nice way to reason about the different boundaries of the program. As I say in the book, bugs love boundaries. When doing specification-based testing, you elicit the different possible inputs and outputs of that program. This list helps you to see how the program changes its behavior when the inputs slight change.

That being said, I do suggest a set of test cases for different specific types of inputs. Not only me, but Cem Kaner and colleagues also do that in their book [2]. Why? Because bugs tend to happen more in corner and boundary cases than in happy flows. 

There are basically two types of corner and boundary cases. Some boundaries are related to the specification and the business logic of the program. These boundaries you can only find through decent reasoning, and specification-based testing. Other boundaries happen because we have to express these requirements in code. And experience shows us that we often forget to handle common cases, such as null pointer exceptions, empty arrays, or arrays with single elements. 

Luckily for us, many of these "common mistakes" can be put in a list, which we can just go through with it. Therefore, when doing specification-based testing, focus on the requirements and on the identification of all the different possible inputs and outputs of the program. Once you are done with it, just (mechanically) test for the "common mistakes". It's cheap and I'm sure you won't regret it.


References:

[1] Maurício Aniche, Christoph Treude, Andy Zaidman. How Developers Engineer Test Cases: An Observational Study. Transactions on Software Engineering (TSE), 2021. https://www.mauricioaniche.com/publications/how-developers-engineer-test-cases/


[2] Kaner, Cem, Sowmya Padmanabhan, and Douglas Hoffman. "The Domain Testing Workbook". Context Driven Press, 2013.
