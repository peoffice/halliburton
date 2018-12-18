## Overview
> Intuitively, one can view a unit as the smallest testable part of an application. In procedural programming, a unit could be an entire module, but it is more commonly an individual function or procedure. In object-oriented programming, a unit is often an entire interface, such as a class, but could be an individual method.Unit tests are short code fragments created by **programmers** or occasionally by **white box testers** during the development process. It forms the basis for component testing

> Unit tests are short, quick, and automated tests that make sure a specific part of your program works. They test specific functionality of a method or class that have a clear pass/fail condition. By writing unit tests, developers can make sure their code works, before passing it to QA for further testing.
## Benefits
* Make the process agile
  > One of the main benefits of unit testing is that it makes the coding process more agile. When you add more and more features to a software, you sometimes need to change old design and code. But changing already tested code is both risky and costly. If we have unit tests in place, then we can proceed for refactoring confidently.
  
  > Unit testing really goes hand in hand with agile programming of all flavors because it builds in tests that allow you to make changes more easily. In other words, unit tests facilitate safe refactoring
* Quality of code
  > Unit testing improves the quality of the code; it identifies every defect which may have aroused, before code is sent further for integration testing. Writing tests before actual coding makes you think harder on the problem. It exposes the edge cases and makes you write better code
* Find software bugs early
  > Issues are found at early stage. Since unit testing are carried out by developers where they test their individual code before the integration, issues can be found very early and can be resolved then and there without impacting the other piece of codes. This includes both bugs in the programmer’s implementation and flaws or missing parts of the specification for the unit
* Facilitates changes & simplifies integration
  > Unit testing allows the programmer to refactor code or upgrade system libraries at a later date, and make sure the module still works correctly. Unit tests detect changes which may break a design contract. They help with maintaining and changing the code.
  
  > Unit testing really reduces defects in the newly developed features or reduces bugs when changing the existing functionality. 
  
  > Unit Testing verifies the accuracy of the each unit. Afterward, the units are integrated into an application, by testing parts of the application via unit testing, later testing of the application during the integration process is easier due to the verification of the individual units.
* Provides documentation
  > Unit testing provides a documentation of the system. Developers looking to learn what functionality is provided by a unit, and how to use it, can look at the unit tests to gain a basic understanding of the unit’s interface (API).
* Debugging Process
  > Unit testing helps in simplifying the debugging process. If a test fails then only latest changes made in code needs to be debugged.
* Design
  > Writing the test first forces you to think through your design and what it must accomplish before you write the code. This not only keeps you focused, it makes you create better designs.
  
  > Testing a piece of code forces you to define what that code is responsible for. If you can do this easily, that means the code’s responsibility is well-defined and therefore that it has high cohesion
* Reduce the costs
  > Since the bugs are found early in unit testing, it helps in reducing the cost of bug fixes. Just imagine the cost of bug found during the later stages of development like during system testing or during acceptance testing. And of course, bugs detected earlier are easier to fix, because bugs detected later are usually the result of many changes, and you don’t really know which one caused the bug
* ...

## Reason for not writing unit testing
* We don’t have time to write tests!
* Unit tests are waste of time. They slow you down and decrease your productivity!
* I don’t know how to write unit tests!
* ...
## Principles
* Know what you're testing
* Unit tests should be self-sufficient
  > A good unit test should be isolated. **Avoid dependencies such as environment settings, register values, or databases.** A single test should not depend on running other tests before it, nor should it be affected by the order of execution of other tests. Running the same unit test 1,000 times should return the same result every time.
* Tests should be deterministic
  > he worst test is the one that passes some of the time. A test should either pass all the time or fail until fixed. Having a unit test that passes some of the time is equivalent to not having a test at all.
* Naming conventions
  > To know why a test failed, we need to be able to understand it at a glance. The first thing that you notice about a failed test is its name -- the test method name is very important. When a well-named test fails, it is easier to understand what was tested and why it failed
* Do repeat yourself
  >  In production code, you should avoid duplication because it causes maintainability issues. Readability is very important in unit testing, so it is acceptable to have duplicate code. 
* Test results, not implementation
  > Successful unit testing requires writing tests that would only fail in case of an actual error or requirement change. There are a few rules that help avoid writing fragile unit tests. These are tests that would fail due to an internal change in the software that does not affect the user.
  
  > Since the same developer that wrote the code and knows how the solution was implemented usually writes unit tests, it is difficult not to test the inner workings of how a feature was implemented. The problem is that implementation tends to change and the test will fail even if the result is the same.
  
  > Another issue arises when testing internal/private methods and objects. There is a reason that these methods are private -- they are not meant to be "seen" outside of the class and are part of the internal mechanics of the class. Only test private methods if you have a very good reason to do so. Trivial refactoring can cause complication errors and failures in the test
* Avoid overspecification
  > It is tempting to create a well-defined, controlled, and strict test that observes the exact process flow during the test by setting every single object and testing every single aspect being tested. The problem is that this "locks" the scenario under test, preventing it from changing in ways that do not affect the result
* Use an isolation framework
  > Writing good unit tests can be hard when the class under test has internal or external dependencies. In order to run a test, you may need a connection to a fully populated database or a remote server. In some cases, you may need to instantiate a complex class created by someone else
## F.I.R.S.T Princiles
* Fast
  * A developer should not hesitate to run the tests as they are slow.
  * All of these including setup, the actual test and tear down should execute really fast (milliseconds) as you may have thousands of tests in your entire project.
* Isolated/Independent
  * A test method should do the 3 As => Arrange, Act, Assert
  * Arrange: The data used in a test should not depend on the environment in which the test is running. All the data needed for a test should be arranged as part of the test.
  * Act: Invoke the actual method under test.
  * Assert: A test method should test for a single logical outcome, implying that typically there should be only a single logical assert. A logical assert could have multiple physical asserts as long as all the asserts test the state of a single object. In a few cases, an action can update multiple objects.
  * Avoid doing asserts in the Arrange part, let it throw exceptions and your test will still fail.
  * No order-of-run dependency. They should pass or fail the same way in suite or when run individually.
  * Do not do any more actions after the assert statement(s), preferably single logical assert.
* Repeatable
  * A test method should NOT depend on any data in the environment/instance in which it is running.
  * Deterministic results - should yield the same results every time and at every location where they run.
  * No dependency on date/time or random functions output.
  * Each test should setup or arrange it's own data.What if a set of tests need some common data? Use Data Helper classes that can setup this data for re-usability.
* Self-Validating
  * No manual inspection required to check whether the test has passed or failed.
* Thorough
  * Should cover every use case scenario and NOT just aim for 100% coverage.
  * Tests for corner/edge/boundary values.
  * Tests for large data sets - this will test runtime and space complexity.
  * Tests for security with users having different roles - behavior may be different based on user's role.
  * Tests for large values - overflow and underflow errors for data types like integer.
  * Tests for exceptions and errors.
  * Tests for illegal arguments or bad inputs.
## 编写单元测试的良好准则
* 一个测试类只对应一个被测类。当前的测试类应该与其他的测试类、环境设置等没有任何依赖。
* 测试类的目录结构和被测试类的对应，这样便于快速找到错误位置。
* 一个测试方法只测试一个方法。同时，确保不要测试私有方法，它们是被封装起来的，并不是API。
* 测试用例的变量和方法都要有明确的含义。比如，将预期结果保存到 $expectedFoo 变量而不是只保存到 $foo。如果要测试很多复合结果，可使用组合变量名称诸如：$inputValue_NotNull，$inputValue_ZeroData，$inputValue_PastDate等等（这要看你的代码规范约定）。
* 测试用例具备可读性。测试用例代码应该遵循规范，像应用代码一样易于理解。以后的维护者会在阅读实现前去阅读你的测试，这将帮助他们在调试前理解被测类的逻辑。
* 测试用例干净整洁。程序中不要有流程控制语句(switch，if 等)。一个好的测试用例处理顺序简单直接，准备数据，验证结果顺序，如有必要，使用子方法分解结构，让测试用例更加易读。如果是多场景，使用多个方法测试；例如，一个测试用例的方法代码长度最多满屏，不要有滚动条，大概在 1 到 20 行左右。如果测试代码太长，考虑拆开成多个方法，以避免混在一起相互干扰；
* 测试用例要验证预期的异常。PHP中使用 @expectedException，不要忽略它们。
* 测试用例不要连接数据库。如果测试中需要连接数据库，那么每个新的测试方法都应自主引导到临时数据库（使用 Setup/Teardown做准备）。如果不是必须连接数据库，请使用mock产生确定的数据。
* 测试用例不要连接网络资源。测试某个方法时无法确保第三方的有效性，诸如网络和设备的有效性，而应该使用mocks代替。
* 不要在自己的类中测试第三方的类库。类库应该由它们自己的测试用例来测试，这也是我们选择类库的原因。如果它们自己没有，应该考虑使用mock来模拟类库的输出结果，确保输入数据的确定性。我们不应该在测试自己类功能的时候，还要考虑第三方库的的功能。
* 测试用例要处理好边界情况，极限值 (max, min) 和null变量（即使抛异常）。你要确保这些问题状况永远都不会发生，甚至在维护时不使用测试用例。
* 测试用例在任何情况下都可运行，并且不需要配置和人工干预。
* 测试用例通过当前测试，并且易于改进。测试用例要能够支持代码的演变，如果很难维护或者代码太轻而不能细化，那就成了负担（很多人不写单元测试用例就是这个原因）。
* 测试用例的输入要具体。在PHP中，测试的方法不要使用 time()作为输入，最好使用date_format()创建具体格式的时间。再如：name = "Smith"; 不要用 name = "name"或者 name = "test";
* 测试用例不要使用@ignored或者被注释掉，切记切记。
* 测试用例帮忙验证代码架构。如果你不能测试某个方法或者类，那么你的设计就不够灵活。
* 测试用例可以运行在任何平台，而不仅是指定目标平台。不要指望一个特定设备或者硬件配置。不然你的测试用例会迁移困难，这样会导致你会禁用他们。不应该出现“在我的机器上没问题啊”这种情况。
* 测试用例运行速度快。慢的测试会把你拖垮，快的速度会鼓励你经常运行他们，它还能帮助你减少持续集成系统上的构建时间。慎用delay() 或者 sleep() ，比如只有在某些边缘情况下，比如等待通知或者基于时钟的方法；
* 把断言从逻辑中分离出来。断言应该用来检验结果，不应该执行逻辑操作的。
* 测试类不要包含私有的方法。私有方法都是一些具体的实现，不应该包含在单元测试里。
* 一个测试不要超过一个模拟(mock对象)。不然如何消除错误和不一致性。
* 保持你的测试是幂等的。测试程序应该能运行多次保持结果一致，不论运行一次还是一百万次，它的效果都应该是一样的。并且，在测试过程中，我们不应该改变任何的数据或者添加任何东西
## Guidelines
* Keep unit tests small and fast
  > Ideally the entire test suite should be executed before every code check in. Keeping the tests fast reduce the development turnaround time.
* Unit tests should be fully automated and non-interactive
  > The test suite is normally executed on a regular basis and must be fully automated to be useful. If the results require manual inspection the tests are not proper unit tests.
* Make unit tests simple to run
  > Configure the development environment so that single tests and test suites can be run by a single command or a one button click.
* Measure the tests
  > Apply coverage analysis to the test runs so that it is possible to read the exact execution coverage and investigate which parts of the code is executed and not.
* Fix failing tests immediately
  > Each developer should be responsible for making sure a new test runs successfully upon check in, and that all existing tests runs successfully upon code check in. If a test fails as part of a regular test execution the entire team should drop what they are currently doing and make sure the problem gets fixed.
* Keep testing at unit level
  > Unit testing is about testing classes. There should be one test class per ordinary class and the class behaviour should be tested in isolation. Avoid the temptation to test an entire work-flow using a unit testing framework, as such tests are slow and hard to maintain. Work-flow testing may have its place, but it is not unit testing and it must be set up and executed independently.
* Start off simple
  > One simple test is infinitely better than no tests at all. A simple test class will establish the target class test framework, it will verify the presence and correctness of both the build environment, the unit testing environment, the execution environment and the coverage analysis tool, and it will prove that the target class is part of the assembly and that it can be accessed.
  > The Hello, world! of unit tests goes like this:
     ```
     void testDefaultConstruction()
     {
       Foo foo = new Foo();
       assertNotNull(foo);
     }
     ```
* Keep tests independent
  > To ensure testing robustness and simplify maintenance, tests should never rely on other tests nor should they depend on the ordering in which tests are executed.
* Keep tests close to the class being tested
  > If the class to test is Foo the test class should be called FooTest (not TestFoo) and kept in the same package (directory) as Foo. Keeping test classes in separate directory trees makes them harder to access and maintain. Make sure the build environment is configured so that the test classes doesn't make its way into production libraries or executables.
* Name tests properly
  > Make sure each test method test one distinct feature of the class being tested and name the test methods accordingly. The typical naming convention is test[what] such as ```testSaveAs(), testAddListener(), testDeleteProperty()``` etc.
* Test public API
  > Unit testing can be defined as testing classes through their public API. Some testing tools makes it possible to test private content of a class, but this should be avoided as it makes the test more verbose and much harder to maintain. If there is private content that seems to need explicit testing, consider refactoring it into public methods in utility classes instead. But do this to improve the general design, not to aid testing.
* Think black-box
  > Act as a 3rd party class consumer, and test if the class fulfills its requirements. And try to tear it apart.
* Think white-box
  > After all, the test programmer also wrote the class being tested, and extra effort should be put into testing the most complex logic.
* Test the trivial cases too
  > It is sometimes recommended that all non-trivial cases should be tested and that trivial methods like simple setters and getters can be omitted. However, there are several reasons why trivial cases should be tested too:
  * Trivial is hard to define. It may mean different things to different people.
  * From a black-box perspective there is no way to know which part of the code is trivial.
  * The trivial cases can contain errors too, often as a result of copy-paste operations:
    ```
     private double weight_;
     private double x_, y_;

     public void setWeight(int weight)
     {
       weight = weight_;  // error
     }

     public double getX()
     {
       return x_;
     }

     public double getY()
     {
       return x_;  // error
     }
    ```
  > The recommendation is therefore to test everything. The trivial cases are simple to test after all.
* Focus on execution coverage first
  > Distinguish between execution coverage and actual test coverage. The initial goal of a test should be to ensure high execution coverage. This will ensure that the code is actually executed on some input parameters. When this is in place, the test coverage should be improved. Note that actual test coverage cannot be easily measured (and is always close to 0% anyway).
  
  > Consider the following public method:

    ``` void setLength(double length);```
  
  > By calling setLength(1.0) you might get 100% execution coverage. To acheive 100% actual test coverage the method must be called for every possible double value and correct behaviour must be verified for all of them. Surly an impossible task.
* Cover boundary cases
  > Make sure the parameter boundary cases are covered. For numbers, test negatives, 0, positive, smallest, largest, NaN, infinity, etc. For strings test empty string, single character string, non-ASCII string, multi-MB strings etc. For collections test empty, one, first, last, etc. For dates, test January 1, February 29, December 31 etc. The class being tested will suggest the boundary cases in each specific case. The point is to make sure as many as possible of these are tested properly as these cases are the prime candidates for errors.
* Provide a random generator
  > When the boundary cases are covered, a simple way to improve test coverage further is to generate random parameters so that the tests can be executed with different input every time.

  > To achieve this, provide a simple utility class that generates random values of the base types like doubles, integers, strings, dates etc. The generator should produce values from the entire domain of each type.

  > If the tests are fast, consider running them inside loops to cover as many possible input combinations as possible. The following example verifies that converting twice between little endian and big endian representations gives back the original value. As the test is fast, it is executed on one million different values each time.
  ```
    void testByteSwapper()
    {
      for (int i = 0; i < 1000000; i++) {
        double v0 = Random.getDouble();
        double v1 = ByteSwapper.swap(v0);
        double v2 = ByteSwapper.swap(v1);
        assertEquals(v0, v2);
      }
    }
  ```
* Test each feature once
  > When being in testing mode it is sometimes tempting to assert on "everything" in every test. This should be avoided as it makes maintenance harder. Test exactly the feature indicated by the name of the test method. As for ordinary code, it is a goal to keep the amount of test code as low as possible.
* Use explicit asserts
  > Always prefer assertEquals(a, b) to assertTrue(a == b) (and likewise) as the former will give more useful information of what exactly is wrong if the test fails. This is in particular important in combination with random value parameters as described above when the input values are not known in advance.
* Provide negative tests
  > Negative tests intentionally misuse the code and verify robustness and appropriate error handling.
  
  > Consider this method that throws an exception if called with a negative parameter:

    ```void setLength(double length) throws IllegalArgumentException;```

  > Testing correct behavior for this particular case can be done by:
    ```
    try {
      setLength(-1.0);
      fail();  // If we get here, something went wrong
    }
    catch (IllegalArgumentException exception) {
      // If we get here, all is fine
    }
    ```
* Design code with testing in mind
  > Writing and maintaining unit tests are costly, and minimizing public API and reducing cyclomatic complexity in the code are ways to reduce this cost and make high-coverage test code faster to write and easier to maintain.

  > Some suggestions:
    * Make class members immutable by establishing state at construction time. This reduce the need of setter methods.
    * Restrict the use of excessive inheritance and virtual public methods.
    * Reduce the public API by utilizing friend classes (C++), internal scope (C#) and package scope (Java).
    * Avoid unnecessary branching.
    * Keep as little code as possible inside branches.
    * Make heavy use of exceptions and assertions to validate arguments in public and private API's respectively.
    * Restrict the use of convenience methods. From a black-box perspective every method must be tested equally well. Consider the following trivial example:
        ```
        public void scale(double x0, double y0, double scaleFactor)
        {
          // scaling logic
        }

        public void scale(double x0, double y0)
        {
          scale(x0, y0, 1.0);
        }
        ```
       Leaving out the latter simplifies testing on the expense of slightly extra workload for the client code.
* Don't connect to predefined external resources
  > Unit tests should be written without explicit knowledge of the environment context in which they are executed so that they can be run anywhere at anytime. In order to provide required resources for a test these resources should instead be made available by the test itself. Consider for instance a class for parsing files of a certain type. Instead of picking a sample file from a predefined location, put the file content inside the test, write it to a temporary file in the test setup process and delete the file when the test is done.
* Know the cost of testing
  > Not writing unit tests is costly, but writing unit tests is costly too. There is a trade-off between the two, and in terms of execution coverage the typical industry standard is at about 80%.

  > The typical areas where it is hard to get full execution coverage is on error and exception handling dealing with external resources. Simulating a database breakdown in the middle of a transaction is quite possible, but might prove too costly compared to extensive code reviews which is the alternative approach.

* Prioritize testing
  > Unit testing is a typical bottom-up process, and if there is not enough resources to test all parts of a system priority should be put on the lower levels first.
* Prepare test code for failures
  > Consider the simple example:
    ```
    Handle handle = manager.getHandle();
    assertNotNull(handle);

    String handleName = handle.getName();
    assertEquals(handleName, "handle-01");
    ```
  > If the first assertion is false, the code crashes in the subsequent statement and none of the remaining tests will be executed. Always prepare for test failure so that the failure of a single test doesn't bring down the entire test suite execution. In general rewrite as follows:
    ```
    Handle handle = manager.getHandle();
    assertNotNull(handle);
    if (handle == null) return;

    String handleName = handle.getName();
    assertEquals(handleName, "handle-01");
    ```
    
* Write tests to reproduce bugs
  > When a bug is reported, write a test to reproduce the bug (i.e. a failing test) and use this test as a success criteria when fixing the code.
* Know the limitations
  > Unit tests can never prove the correctness of code!!
  
  > A failing test may indicate that the code contains errors, but a succeeding test doesn't prove anything at all.
  
  > The most useful appliance of unit tests are verification and documentation of requirements at a low level, and regression testing: verifying that code invariants remains stable during code evolution and refactoring.

  > Consequently unit tests can never replace a proper up-front design and a sound development process. Unit tests should be used as a valuable supplement to the established development methodologies.

  > And perhaps most important: The use of unit tests forces the developers to think through their designs which in general improve code quality and API's.

## Unit Testing Frameworks
#### GoogleTest for C&C++
* Description
  > Google Test is a unit testing library for the C++ programming language, based on the xUnit architecture.[1] The library is released under the BSD 3-clause license.[2] It can be compiled for a variety of POSIX and Windows platforms, allowing unit-testing of C sources as well as C++ with minimal source modification. The tests themselves could be run one at a time, or even be called to run all at once. This makes the debugging process very specific and caters to the need of many programmers and coders alike.

* Version 1.7.0
* License BSD 3-clause
* WebSite https://github.com/google/googletest
* Installation
  * Windows Installation
    * Open the project file with vs2013 and build
  * Linux
    * Suppose you put Google Test in directory ${GTEST_DIR)
    * ```g++ -isystem ${GTEST_DIR}/include -I${GTEST_DIR} -pthread -c ${GTEST_DIR}/src/gtest-all.cc```
    * ```ar -rv libgtest.a gtest-all.o```
  
#### VisualStudio Testing Tools for C#
* Description
  > Visual Studio testing tools can help you and your team develop and sustain high standards of code excellence.
    * The Test Explorer window makes it easy to integrate [**unit tests**](https://docs.microsoft.com/en-us/visualstudio/test/unit-test-your-code?view=vs-2017) into your development practice. You can use the Microsoft unit test framework or one of several third-party and open source frameworks.
    * [**IntelliTest**](https://docs.microsoft.com/en-us/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest?view=vs-2017) automatically generates unit tests and test data for your managed code.
    * [**Code coverage**](https://docs.microsoft.com/en-us/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested?view=vs-2017) determines what proportion of your project's code is actually being tested by coded tests such as unit tests.
    * [**Microsoft Fakes**](https://docs.microsoft.com/en-us/visualstudio/test/isolating-code-under-test-with-microsoft-fakes?view=vs-2017) help you isolate the code you are testing by replacing other parts of the application with stubs or shims.
    * [**Live Unit Testing**](https://docs.microsoft.com/en-us/visualstudio/test/live-unit-testing?view=vs-2017) automatically runs unit tests in the background, and graphically displays code coverage and test results in the Visual Studio code editor.
    * [**Coded UI tests**](https://docs.microsoft.com/en-us/visualstudio/test/use-ui-automation-to-test-your-code?view=vs-2017) enable you to test your application through its user interface.
    * [**Load testing**](https://docs.microsoft.com/en-us/visualstudio/test/quickstart-create-a-load-test-project?view=vs-2017) simulates load on a server application by running unit tests and web performance tests.
* Installation
  * VisualStudio testing tools are embeded in VS IDE, so you just intall vs.
  * Create unit tests
    > Create unit tests and run them frequently to make sure your code is working properly
      * Create a unit test project.
        > ![vs_ut_create_project](https://github.com/peoffice/halliburton/blob/master/png/vs_ut_create_project.png)
      * Name your project
        > ![vs_ut_name_project](https://github.com/peoffice/halliburton/blob/master/png/vs_ut_name_project.png)
        
        > The project added to your solution.
        
        > ![vs_ut_project_in_solution](https://github.com/peoffice/halliburton/blob/master/png/vs_ut_project_in_solution.png)
      * In the unit test project, add a reference to the project you want to test
        > ![vs_ut_add_reference](https://github.com/peoffice/halliburton/blob/master/png/vs_ut_add_reference.png)
      * Select the project that contains the code you'll test
        > ![vs_ut_project_in_view](https://github.com/peoffice/halliburton/blob/master/png/vs_ut_project_in_view.png)
      * Code your unit test.
        > ![vs_ut_project_code](https://github.com/peoffice/halliburton/blob/master/png/vs_ut_project_code.png)
    > You can also create unit test method stubs with the Create Unit Tests [**command**](https://docs.microsoft.com/en-us/visualstudio/test/create-unit-tests-menu?view=vs-2017)
    
    > ![vs_ut_project_in_command](https://github.com/peoffice/halliburton/blob/master/png/vs_ut_project_in_command.png)
  * Run unit tests
    * Open Test Explorer
      > ![vs_ut_run_explorer](https://github.com/peoffice/halliburton/blob/master/png/vs_ut_run_explorer.png)
    * Run unit tests
      > ![vs_ut_run_do](https://github.com/peoffice/halliburton/blob/master/png/vs_ut_run_do.png)
      
      > You can see the unit tests that passed or failed in Test Explorer

      > ![vs_ut_run_view](https://github.com/peoffice/halliburton/blob/master/png/vs_ut_run_view.png)
#### Java
## Samples
## CI 
## Reference
* 单元测试整理
  * [单元测试整理（一）——单元测试是什么，有什么好处](https://blog.csdn.net/potatostyles/article/details/79152107)
  * [单元测试整理（二）——断言篇，首个单元测试程序](https://blog.csdn.net/potatostyles/article/details/79169129)
  * [单元测试整理（三）——JUnit 测试组成和注释](https://blog.csdn.net/potatostyles/article/details/79175982)
  * [单元测试整理（四）——测试哪些内容及边界条件](https://blog.csdn.net/potatostyles/article/details/79177163)
  * [单元测试整理（五）—— Mock篇，测试一个servlet](https://blog.csdn.net/potatostyles/article/details/79207293)
  * [单元测试整理（六）—— 使用EasyMock和JUnit进行单元测试](https://blog.csdn.net/potatostyles/article/details/79210476)
* [Unit Testing - wikipedia](https://en.wikipedia.org/wiki/Unit_testing)
* [单元测试规范](https://blog.csdn.net/iprettydeveloper/article/details/55190852)
* [Junit测试代码编写命名规范](https://www.cnblogs.com/zishi/p/6762032.html)
* [阿里java单元测试准则](https://blog.csdn.net/wangpengzhi19891223/article/details/79373374)
* [编写单元测试的良好准则](https://www.awaimai.com/2379.html/amp)
* [UnitTest](https://martinfowler.com/bliki/UnitTest.html)
* [TOP 8 BENEFITS OF UNIT TESTING](https://apiumhub.com/tech-blog-barcelona/top-benefits-of-unit-testing/)
* [20 ADVANTAGES OF TEST DRIVEN DEVELOPMENT](https://apiumhub.com/tech-blog-barcelona/advantages-of-test-driven-development/)
* [Developers who don’t write tests!](https://programmingwithmosh.com/csharp/developers-dont-write-tests/)
* [What is Unit Testing and Why You Need to Learn It](https://programmingwithmosh.com/csharp/unit-testing/)
* [F.I.R.S.T Principles of Unit Testing](https://github.com/ghsukumar/SFDC_Best_Practices/wiki/F.I.R.S.T-Principles-of-Unit-Testing)
* [编写单元测试的良好准则](https://www.awaimai.com/2379.html/amp)
* [单元测试的基本准则](https://blog.csdn.net/hou549135295/article/details/51384042)
* [19条技巧教你更好的编写单元测试](http://www.techug.com/post/19-unit-test-code-tips.html)
* [**Unit Testing Guidelines**](https://petroware.no/unittesting.html)
* [浅谈测试驱动开发（TDD）](https://www.ibm.com/developerworks/cn/linux/l-tdd/)
* [JUnit best practices:Techniques for building resilient, relocatable, multithreaded JUnit tests](https://www.javaworld.com/article/2076265/testing-debugging/junit-best-practices.html)
* [Unit testing guidelines](https://pylonsproject.org/community-unit-testing-guidelines.html)

* [googletest - github](https://github.com/google/googletest)
* [Google Test - wikipedia](https://en.wikipedia.org/wiki/Google_Test)
* [Testing tools in Visual Studio](https://docs.microsoft.com/en-us/visualstudio/test/improve-code-quality?view=vs-2017)
