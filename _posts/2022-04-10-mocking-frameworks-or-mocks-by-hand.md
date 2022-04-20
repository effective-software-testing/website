---
title: "Mocking framework vs mocks by hand"
layout: post
---

There was an [interesting discussion on Twitter](https://twitter.com/mauricioaniche/status/1478448315188617221?s=20) a few weeks ago on whether we should use mocking frameworks or not:

* [I asked](https://twitter.com/mauricioaniche/status/1478448315188617221) to the author of the original post, _why do you prefer hand-crafted stubs and fakes, Ted?_

* [Ted M. Young's response](https://twitter.com/jitterted/status/1478457034227945473) was: _"The ease of using a tool to create them means you won't notice how complex the real thing has become. So, if it becomes difficult or tedious to create them by hand, that often points to interfaces or classes that have become too large, with too many responsibilities."_

Ted has a good point here. **If you need complex mocking, then, maybe something is more complex than it should or needs to be.**

I still support the use of a mocking framework, though. It's so much easier to use the Mockito's two lines of code to create a stub. But you should look at all the mock code and think _"I could do this by hand if I wanted to"_. That's the key.

