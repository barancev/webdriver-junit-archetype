Webdriver JUnit Archetype
==========================

This archetype generates a new Maven project that can be used as a start point to develop tests in Java with [Selenium WebDriver](https://github.com/SeleniumHQ/selenium) and [JUnit](https://github.com/junit-team/junit4).

To create a project from this archetype:

```
mvn archetype:generate -DarchetypeGroupId=ru.stqa.selenium -DarchetypeArtifactId=webdriver-junit-archetype -DarchetypeVersion=2.1 -DgroupId=<mygroupId> -DartifactId=<myartifactId>
```

where `mygroupId` is a group id of the project you are creating, and `myartifactId` is an artifact id of the project you are creating.

Project Structure
-----------------------------------

The project follows the standard Maven structure, so all the tests go in the `src/test/java` folder. Tests should inherit from the `JUnitTestBase` class that performs common setup and teardown tasks. This class uses [WebDriverFactory](https://github.com/barancev/webdriver-factory) to manage drivers.

`SampleJUnitTest` class (in `src/test/java`) is an example of a test class for testing the homepage of a web application. In the setup method of this class, the `PageFactory` class is used
 to help supporting the [PageObjects](https://github.com/SeleniumHQ/selenium/wiki/PageObjects) pattern.

All test classes should be listed in `JUnitTestSuite` class that is used as a start point to run the tests.

Project Configuration
-----------------------------------

The project uses Maven profiles to set configuration parameters. There are three profile groups: 1) to specify a browser, 2) to specify the target application properties, 3) to specify Selenium Grid location.

For example, to run tests in Chrome on the localhost without grid use this profile set:

```
mvn -P chrome,localhost,nogrid test
```

Default profile set is `firefox,localhost,nogrid`

The target application URL and the grid location should be specifies in the `pom.xml` file in the corresponding profiles.

Driver capabilities can be tuned in the files `src/test/resources/*.capabilities`.
