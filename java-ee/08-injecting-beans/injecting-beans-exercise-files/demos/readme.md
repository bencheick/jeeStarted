# Module 08: Injecting Beans

In object oriented programming, objects depend on others. Thanks to injection we can easily ask the container to provide the needed dependencies.


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

* In the package `com.pluralsight.bookstore.util` create the new bean `IsbnGenerator` with a `generateNumber` returning a random ISBN number
* The `BookRepository` uses injection to get a reference of the `IsbnGenerator` bean that it uses in the `create` method
* For injection to work, create an empty `src/main/webapp/WEB-INF/beans.xml` file
* Adjust the Arquillian tests so it can test injection

*To execute the application you have to build it (`mvn clean package`) and then deploy the `bookstore-back.war` into [WildFly](https://wildfly.org).*
