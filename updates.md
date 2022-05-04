---
title: "Updates"
layout: post
permalink: /updates
hide_newsletter: false
---

There are always things that can be improved in a book. This page contains my thoughts on what I would have written differently or added to it.

# Chapter 1

* The exercise mentions _defect clustering_ but the term doesn't appear in the book. Although not explicitly mentioned, this is discussed in Section 1.3.4, Bugs happen in some places more than others. After all, defects like to cluster in some places more than others.

# Chapter 2

* A recurrent perception after reading this chapter is that _domain testing is then all about testing nulls and empties and corner cases._ As if the technique was more about following some generic checklist rather than really thinking of good test cases. This is definitely not it. Domain testing is all about the requirements. You look at the requirements, you understand them, and then you start to partite the domain space based on the requirements. I suggest you to do it by looking at the inputs and outputs of the program, but aways in the light of the requirements! Again, nulls and empties, or for loops that run zero, one, and many times are very good test cases because bugs may live there, but that's not the point. 

# Chapter 4

* In our minds, we should separate between the concrete implementation of the pre- and post-conditions from the intention. Take the `toCamelCase` method from the Apache Commons as an example. It receives a `str` as parameter, and it doesn't define any pre-conditions to it. Meaning, it accepts any strings, even null and empty. The first line of the method's implementation is something like `if(str==null) return str;`. This line is there to make sure the method can handle the null case, given that it has no pre-conditions. If we now talk about implementation, this line in itself is not a pre-condition check. The developer could have opted for a stronger pre-condition, e.g., `str` can't be null. In this case, the first line of this method would probably be `if(str==null) throw new RuntimeException()`, or `assert str != null`. In these examples, these lines are pre-conditions checks. 

# Chapter 5

* The Basket example nicely illustrates JQWik's functionality of enabling us to create actions and therefore test more complex objects that store state. However, in an attempt to show the tool itself, I may have written a bad property-based test. Why? Because the test code has some duplication with the production code. We should write our tests in a way that we can test the property without having to "make the test code to do the same as the production code".

