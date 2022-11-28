---
title: "How we can make it easy? An example with code"
layout: post
---

Many readers have been asking me to show a code example that illustrates the previous post, "It has to be easy". 

As I said there, if you want to convince your engineering teams to write tests, all you gotta do is to make it easy for them to do it. If it's just too hard to write a single test, engineers won't do it. It's that simple.

How do you make it easy? Most of the time you do it by providing APIs that simplify the testing process. Is it hard to create all the complex entities for the tests? Provide engineers with an API that makes it easy. Is it hard to assert that the behaviour was the expected one? Provide an API that makes it easy to do so. 

I'm going to illustrate this with an example extracted from Andy. Andy is a tool that we develop at TU Delft. The tool grades students' test code in my CSE1110, software testing, course. It works as follows. Students write (JUnit) tests for a pre-defined class. They submit these tests to Andy. Andy gets their code, compiles the code under the test and the tests, runs tests, get coverage information, runs mutation testing, and runs static analysis. In the end, Andy collects the results from all these sensors and comes up with a final grade. Say, final grade is a composition of 50% code coverage and 50% mutation testing, and the student code achieves only 50% coverage and 30% mutation coverage, then, Andy gives a final grade of 5.5.

We decided that Andy should be mostly tested via integration tests. Why? Because it'd be too hard to mock a component and test the others with confidence. For example, if we don't compile the code, we can't precisely ensure that the JUnit runner component works as expected.

The challenge became then: how to invoke the entire Andy's engine in an easy way? Plus, how to make sure we can assert any corner case in our tests, like there's one test failing or code doesn't compile?

After some exploration, see what writing a test looks like (you can see the source code [here](https://github.com/cse1110/andy/blob/main/src/test/java/integration/JUnitTestsTest.java#L43)):

```java
@Test
void someTestsFailing() {

    Result result = run(Action.TESTS, "PlayerPointsLibrary", "PlayerPointsSomeTestsFail");

    assertThat(result.getTests().getTestsSucceeded()).isEqualTo(1);
    assertThat(result.getTests().getTestsRan()).isEqualTo(4);
    assertThat(result.getTests().getNumberOfFailingTests()).isEqualTo(3);
    assertThat(result.getTests()).has(failingTest("lessPoints()"));
    assertThat(result.getTests()).has(failingTest("manyPointsAndManyLives()"));
    assertThat(result.getTests()).has(failingTest("manyPointsButLittleLives()"));
}
```

Let me walk you through it.

* **It's easy to exercise the entire engine.** The `run` method is the one responsible for invoking Andy, setting up all the details we have to so that Andy executes in a test environment.

* **It's easy to pass inputs to the test.** Note the `PlayersPointsLibrary` and `PlayerPointsSomeTestsFails`. They are names of files in our test resources. The first one indicates the program under test. The second one indicates the student's submission that we created. The `PlayerPointsSomeTestsFails` one, for example, contains 4 tests, one of them failing. You can see their entire code [here](https://github.com/cse1110/andy/blob/main/src/test/resources/grader/fixtures/Library/PlayerPointsLibrary.java) and [here](https://github.com/cse1110/andy/blob/main/src/test/resources/grader/fixtures/Solution/PlayerPointsSomeTestsFail.java). The `run` method ensures that these two files are then the ones compiled and executed!

* **It's easy to assert the executed behaviour.** The `run` method returns this `Result` data structure. This data structure contains virtually everything that happened in each step of the pipeline. You want to know anything about test execution? Go for `results.getTests()`. Want to know anything about compilation? Go for `results.getCompilation()`. Also, notice the failingTest helper method. Navigating into this data structure can be complicated, so we provide helper methods that simplify the developers’ lives even more, like this one that looks for a specific test name that failed. 

As you can see, it takes one line of code to execute the entire engine (just call `run`). It takes virtually zero effort to pass the desired inputs to the program (just create the java files emulating the program under test and the student's test). It takes virtually zero effort to assert the behaviour (just navigate through the complete Result data structure).

Of course, none of this was for free. We spent some energy creating this run method. We also spent some time modelling the internals of our engine so that we could return this beautiful Result data structure. By the way, this data structure is also used by the production code to generate the final grade output to the student. So, this was a design decision that helped us in production and in test. We also spent some time creating helper methods for the most common assertions.

The consequence? We wrote hundreds of tests for Andy. And most of them were actually written by 1st computer science students that had just learned how to write tests. Again, this was only possible because all the hassle of writing tests was taken away. 

> Understand what tests your developers want to write. And make it easy for them to do so.

This is what you need to do to make writing tests easy! It's an investment, for sure, but one that pays off very quickly.