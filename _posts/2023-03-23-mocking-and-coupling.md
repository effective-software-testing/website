---
title: "Tests breaking because of mocks, what to do?"
layout: post
---

I had to suddenly change the internals of a class a couple weeks ago. This class was responsible for sending messages to our developers through our internal chat. The algorithm was something like this:

* It would get the list of messages to be sent
* For each message, it would:
	* Get the user internal ID from our user directory
	* Send the formatted message + user internal ID to our chat bot

This is clearly too much to be done by a single class, so responsibilities were split. The `MessageSender` class controls the main flow of the feature. The `MessageRepository` returns the list of messages to be sent. The `UserDirectory` retrieves the user internal ID in our external user directory based on the user's email. And the `ChatBot` makes an HTTP request to the internal chat tool with the message and user id.

The class was working fine and highly covered with tests. The tests made use of mocks, so that we didn't have to depend on the real user directory and chatbot (both accessible through external web apis). We stubbed `UserDirectory` to return hard-coded values, and mocked `ChatBot` to verify that the interaction with the bot was correct.

Due to an update in our chat tool, we had to stop using the user internal ID and start using something else. 

I then opened the `MessageSender` and started to replace the `UserDirectory` by something else. As soon as I changed the internal implementation, my test code broke. More specifically, the calls to mocks.

My tests were quite coupled to the internals of the `MessageSender`. The tests knew exactly which methods had to be called in its dependencies. Changing a dependency means changing the entire test.

This can be a good and bad thing. There are different ways to see this:

* If we see the test more as an _interaction test_, meaning, a test that ensures that classes are collaborating with other classes correctly, then it's a good thing that the test broke. 

* If we want the test to ensure the overall behavior of that class, then, having a broken test due to an internal change is a bad thing.

For this precise test (and maybe for a lot of the tests I write), I wanted a bit of both. I wanted to verify the interaction with the `ChatBot` because that was the only way for me to know that the message was being sent. At the same time, I didn't want to care about internal details such as how to get the id of the user.

Ok, how do I fix this? There are a few ways: 

* Change the entire test class based on the new version of the `MessageSender`. This is the approach that requires less thinking. I just code and get things done. Never a bad option.

* See if I could create a new variation of `UserDirectory`, one that gets the new user id. We didn't design this to be an extension point, but that's an option. Do I want to open the system for different types of user directories? I'm not sure.

* Create a new implementation of `MessageSender` containing the new algorithm. Write its tests from scratch (although reusing the test cases from the other message sender). I'd then extract a common interface between the two message senders and have my DI inject the new one. This way, I'd be allowing future versions of my system to have different versions of message senders. That sounded right.

I opt for approach 3. It seems it's a lot of work, but it wasn't. Took me less than 15 minutes, as I could reuse lots of what was written already. 

Interestingly enough, a few days later, we had to rollback the change in our internal communication tool. It was a breeze for us as we still had the old version of message sender.

To sum up: 

* Interaction testing is very powerful but also makes your test code coupled to production code. 
* In practice, you often want a mix of testing interactions and behavior. You gotta ensure that your tests break only for the things you want it to break.
* If a new feature requires you to change code, don't rush up. Changing the design a bit so that you can add new behavior by writing new code instead of updating existing code can also be a good idea.
