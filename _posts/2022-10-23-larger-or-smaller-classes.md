---
title: "Why are smaller classes better than large classes?"
layout: post
---


In the amazing [The Philosophy of Software Design](https://www.amazon.com/Philosophy-Software-Design-John-Ousterhout/dp/1732102201), John Ousterhout argues that having large classes that implement the full expected behaviour can be better than smaller classes that have to get together to do the same. He calls the idea of creating too many small classes, "classitis".

I do not agree with it. On the contrary: **I prefer building complex behaviour through the composition of smaller classes.**

First, it allows me **to read less code**. If the entire implementation is in front of me, I am more likely to spend time reading it whether I need or it. Instead, if I simply have a method call to another class, I'll only open that code when I need to. One of the arguments in the book is that navigation gets trickier when you have to keep jumping from one class to another. True, but IDEs nowadays made navigation much easier, all you gotta do is master it.

Second, it **enables extensibility from day one**. Breaking down complex behaviour into smaller classes is often an exercise of identifying "the different parts of the puzzle". Once this is all modeled, each of these parts can easily be replaced by new ones if needed. In practice, I find that whenever I feel like "this should be another piece of the puzzle", it is often because that part is likely be extended or modified in the future. On the contrary, whenever I don't feel it's another part of the puzzle, that part is likely not to be extended, and I don't move it to another class. Yes, what I just described is inline with the Open-Closed Principle (The "O" of the SOLID principles). 

Last but not least, **testability**. Having smaller classes gives me the chance of deciding whether I want to write unit or integration tests to that complex behaviour. Sometimes I want to exercise one piece of the puzzle in isolation, some other times all the pieces together. If the behaviour is composed of smaller pieces, I am free to take any decision. If the behaviour is in a single place, I don't have this choice.

I am not arguing you should break down all (complex) behaviour in multiple classes. Classitis can hurt you. Sometimes it simply makes no sense to separate code. I tend to keep code together when I don't see these two parts being far apart or when I don't see that piece of the puzzle ever being replaced by a different one. As always, **pragmatism is key**.
