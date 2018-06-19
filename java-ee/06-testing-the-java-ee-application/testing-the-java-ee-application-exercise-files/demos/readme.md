# Module 06: Testing the Java EE Application

This module uses JUnit and Arquillian frameworks to test the first components of our BookStore application


## Structure 

The BookStore application is divided into a Java EE REST back-end (`bookstore-back`) and an Angular front-end (`bookstore-front`).


### Bookstore Back 

The code of this module follows the [Maven](http://maven.apache.org/) directory structure. The `src/main/` directory contains the main source code while you will find the test class under `src/test/`. The `pom.xml` file is Maven specific and it describes the project and its dependencies.

Once [Maven](http://maven.apache.org/) and a [JDK 8](http://www.oracle.com/technetwork/java/javase/downloads/index.html) are installed, enter the following Maven commands:

* `mvn help:help`       : shows Maven help
* `mvn clean`           : cleans the `target` directory
* `mvn compile`         : compiles the code
* `mvn test`            : runs the test case (you need WildFly to be up and running)
* `mvn package`         : packages the code into a war file
* `mvn clean package`   : executes a clean and then a package

Once [Wildfly](http://wildfly.org/) is installed, deploy the war file and go to [http://localhost:8080/bookstore-back/]()



## Demo 

* In the `src/test/java` directory create a `com.pluralsight.bookstore.repository` package with a `BookRepositoryTest` test class. This should test the repository with methods such as shouldGetNoBook, shouldCreateABook, shouldFindTheCreatedBook, shouldGetOneBook, shouldDeleteTheCreatedBook, shouldGetNoMoreBook
* Add the `src/test/resources/META-INF/test-persistence.xml` file for test purpose
* Add the `src/test/resources/arquillian.xml` file for Arquillian test with the `arquillian-wildfly-remote` qualifier
* Startup WildFly and run `mvn clean test` so the Arquillian tests pass

*To execute the application you have to build it (`mvn clean package`) and then deploy the `bookstore-back.war` into [WildFly](https://wildfly.org).*
