CAB302 Software Development
===========================

# Practical 3: Automated Unit Testing

This week's practical exercises aim to get you familiar with designing and implementing automated unit tests using JUnit and IntelliJ.

* * *

## Setting up

When you import the project in the accompanying practical material into Eclipse, it should already come with JUnit 5. However, when it comes to adding test cases to your own code, you will need to know how to import these libraries.

For IntelliJ to recognise JUnit, it needs to be in the dependency list for the project (File->Project Structure->Modules->Dependencies). If it's not there, there are a few ways to add it.

One is to just download the jar files directly from the Maven. You want `junit-jupiter-api` from  [https://search.maven.org/search?q=g:org.junit.jupiter](https://search.maven.org/search?q=g:org.junit.jupiter), `junit-platform-commons` from [https://search.maven.org/search?q=g:org.junit.platform](https://search.maven.org/search?q=g:org.junit.platform) `apiguardian-api` from [https://search.maven.org/search?q=g:org.apiguardian](https://search.maven.org/search?q=g:org.apiguardian) and `opentest4j` from [https://search.maven.org/search?q=g:org.opentest4j](https://search.maven.org/search?q=g:org.opentest4j). You can then save these somewhere and link them externally, either by going to Project Structure->Libraries and clicking the plus button, or by going to Project Structure->Global Libraries and doing the same. The benefit to adding them as global libraries is that for future projects, you can just go to global libraries, right-click on the libraries and choose 'add to module'.

The other way is to simply start working on your test class by creating a new class (e.g. TotaliserTests) and adding the JUnit imports to it:

    import static org.junit.jupiter.api.Assertions.*;
    import org.junit.jupiter.api.*;

Then, when IntelliJ complains that the imports aren't in your classpath, you can just move your text cursor onto the import line and either click the red lightbulb or type Alt+Enter to access the intention actions for that import:

![Intention actions for import](imgs/intentionactions.png "Add JUnit 5.3 to classpath")

Then you can click 'Add JUnit 5.3 to classpath'. IntelliJ will then pop up a dialog asking to download the libraries from Maven.

## Practical Exercises

### Group Exercise 1: Test case brainstorming (Totaliser example)

This exercise will give you practice at devising black-box test cases for a simple class.

In the materials supplied for this practical session you will find API documentation for three classes, including one called `Totaliser`. (This documentation was generated from a correct version of the program.) Read the documentation for the `Totaliser` class (you will find it in the JavaDoc that is inside the `doc` folder in the repository you cloned. Open the `index.html` file in this repository in a browser; right click and choose 'Open in Browser') and then, as a group, identify a small, but sufficient, set of test cases that will exercise the `Totaliser` implementation's functionality. Your tutor will write the test cases selected on the whiteboard.

* * *

### Individual Exercise 1: Testing with JUnit (Totaliser example)

This exercise will give you practice at using JUnit to test a simple class.

In the materials supplied for this practical session you will find an implementation of the `Totaliser` class in the `totaliserQuestion` package. The purpose of the exercise is to test the supplied program as a black box, i.e., without looking at the source code. Instead use the API documentation above to see which methods Totaliser implements and write test cases to test them.

Create a new package called `totaliserAnswers` and inside that create a new class called `TotaliserTest`. In this class, implement the various tests identified in the previous exercise. Use Week 3's lecture as a reference for creating new test classes. Note that you will need to import totaliserQuestion.Totaliser because it is in a different package. Once you get started, your code should look something like this:

![Beginning of test class for Totaliser](imgs/testclass.png "Beginning of test class for Totaliser")

**Hint:** There are (at least) two errors in the code, one obvious and one a bit harder to detect.

When you think your tests have identified the problems with the program examine the `Totaliser.java` source code file to confirm your suspicions. Then correct the errors in the code and rerun your tests to ensure that the problems have been fixed.

* * *

### Group Exercise 2: Test case brainstorming (AllSame example)

This exercise will give you practice at devising black-box test cases for a more complicated, but stateless, class.

Read the API documentation for the `AllSame` class and, as a group, identify a sufficient set of tests for it. Note that the method provided by this class is a pure function, i.e., it does not update any fields within the class and thus has no 'memory' from one invocation to the next, which simplifies testing.

### Individual Exercise 2: Testing with JUnit (AllSame example)

This exercise will give you practice at using JUnit to test a complicated, stateless class.

In the materials supplied for this practical session you will find three different
implementations of the `AllSame` class in the package `allSameQuestion`: `AllSameA.java`, `AllSameB.java` and `AllSameC.java`. Develop a test class `AllSameTests.java` using the test cases identified in the previous exercise, your challenge is to identify which, if any, of these implementations is correct, and what the problems with the incorrect implementations are. Once again, use the API documentation above to see what AllSame's methods are and write test cases to test them. Look at the code only when you have completed the exercise, in order to confirm your findings.

**Hint:** In the three implementations there are (at least) three distinct errors in total.

**Note:** Testing three different programs with one set of test cases is an unusual situation and is a little awkward, no matter how it's done. One approach is to, in your JUnit test class, manually edit which of the three programs is imported into the test class to change from one to the other. Another approach is to put each of the three programs in its own package and have a copy of the test case class in each one. (There is a much more elegant solution which works by creating a superclass for the three programs under test, but it is felt to be a little complex for this one-off exercise.)

* * *

### Group Exercise 3: Test case brainstorming (JourneyPlanner example)

This exercise will give you practice at devising black-box test cases for a complicated, stateful class.

Read the API documentation for the `JourneyPlanner` class and, as a group, identify a sufficient set of tests for it. Note that this class updates private fields and thus retains a 'memory' from one method invocation to the next, making it hard to devise test cases with good 'coverage'.

![Manhattan distances example](imgs/blocks.png "Manhattan distances example")

**Background:** The class calculates journey times based on 'Manhattan distances', i.e., the distance you must travel in a grid-like environment by following the grid lines only (with no diagonal steps). The name derives from the exceptionally regular layout of streets in New York city, which forces people to travel in this way. Notice in the diagram above that the journey from point P1 to P2 is of the same length, no matter which route is taken.

* * *

### Individual Exercise 3: Testing with JUnit (JourneyPlanner example)

This exercise will give you practice at using JUnit to test a complicated, stateful class.

In the materials supplied for this practical session you will find two different implementations of the `JourneyPlanner` class in the `journeyPlannerQuestion` package: `JourneyPlannerA.java` and `JourneyPlannerB.java` - ***again, do not look at the code for these yet***.  Develop a test class `JourneyPlannerTests.java` using the test cases identified in the previous exercise, your challenge is to identify which, if any, of these implementations is correct, and what the problems are in the incorrect class or classes. Look at the code only when you have completed the tests, in order to confirm your findings.

**Hint:** In the two implementations there are (at least) two distinct errors in total.
