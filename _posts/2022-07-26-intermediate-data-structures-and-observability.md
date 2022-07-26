---
title: "Intermediate data structures and observability"
layout: post
---

Being able to observe the behavior of the program is key in testing. And we should make sure it is always easy to do it.

In a few cases, though, the main challenge in making code observable is that the data structures we developed don't really allow us to do it. Let me give you an example.

[Andy](https://github.com/cse1110/andy/) is a software tool we developed at TU Delft to grade students that take the software testing course. In a nutshell, Andy sees the tests submitted by the student, runs the tests, calculates branch and mutation coverage, runs static analysis,  compares the tests against the teacher's rubric, and, when all this is done, calculates the grade.

In most of our (integration) tests what we want to do is to provide Andy with an example solution and see if Andy correctly graded that exercise. We don't want to assert only the final grade, but whether Andy, e.g., counted the correct number of tests run or the achieved branch coverage of that solution.

In our first implementation, Andy would execute each of the steps in the pipeline and would then already write the result in the expected output format. This was the easiest thing to do. However, we quickly noticed that asserting that each step of the pipeline worked as expected was too hard. We had to assert complex strings, any small change would break our tests, and sometimes we couldn't really assert behavior that we didn't see in the final output.

How did we solve this? **We introduced an intermediate data structure to help the tests**. Instead of making Andy produce the final output right away (again, the simplest thing to do), we create a data structure called `Result`, which Andy now populates as the pipeline goes. In the end of the real execution, Andy navigates through this data structure and produces the expected output. In the tests, though, Andy simply returns it so that we can make our assertions.

This `Result` data structure contains every little piece of information we would like to assert. Do we need to assert the number of tests failed and which ones failed? Easy thing, as everything is in the data structure:

```
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

The `run` method is an utility test method that runs Andy and returns the data structure instead of the final output.

This intermediate structure enabled us to write much stronger test cases. Does it make the code more complex? Not really. In fact, it even enabled us to separate the responsibility of producing the final output from the, e.g., calculating the coverage.

**Therefore, if you feel it's been hard to write strong test cases, mostly because you can't observe the behavior of your system, consider adding an intermediate data structure.**
