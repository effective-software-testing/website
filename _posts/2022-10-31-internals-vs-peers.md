---
title: "Internals vs peers, a nice guide on when to mock"
layout: post
---

We are all past the idea that a unit testing has to only test a single class, isolating it from all its dependencies. We can, but it doesn't mean we should do it always. Deciding, however, which dependencies to mock and which not to mock can be tricky.

The most straightforward answer is: if that dependency is a pain, mock it. Say, the dependency communicates with a web service. Or it requires some complex configuration. Mocking will help you focus on the test under class.

Another nice way of exploring the problem is to think of _internals_ and _peers_. I got this definition from Freeman and Pryce's book on [Growing Object-Oriented Systems Guided by Tests](http://www.growing-object-oriented-software.com/).

You can see some of your dependencies as simple _peers_. Imagine that you are testing a Service and this Service needs some data that another Repository knows how to retrieve. The service then makes use of this Repository. The Repository is just a "peer" of the Service. It helps the Service to do its job, but it's not really part of the Service per se. Peers are great candidates to be mocked. After all, from the perspective of the Service, you don't really care about how the Repository works. You just want it to return a list of something so that you can move on. 

Now, some other dependencies are more about the _internals_ of the class. Imagine that an Invoice entity needs to keep a reference to the Customer it belongs to. Implementation-wise, you will probably make your Invoice class to depend on the Customer class. Different from the previous case, Customer is not a peer of the Invoice class. It is an internal detail of the implementation of the Invoice. You somewhat care about what the Customer does. You there may not want to mock Customer, as your tests may benefit from these two classes being exercised together.

Another example, imagine you are modeling some complex tax calculation process. Instead of writing it fully in a single class, you break it up into small classes to facilitate readability or maintenance in general. These small classes compose a single behavior altogether, and can't each be seen as a "separate" thing. They are all internal details of the implementation of this tax calculation rule. Therefore, you may not want to mock them.

As always, this is not a strict rule, and you should take the context into consideration. Nevertheless, understanding that it is ok to have internal classes that you don't want to mock separately but test altogether was a big relief for me back in the days I was fighting my own thoughts of what a unit test really is.

PS: My definition of internals vs peers may be fully match the one in the original book. I read it over 10+ years ago. Please, read the original piece once you are done with this one!
