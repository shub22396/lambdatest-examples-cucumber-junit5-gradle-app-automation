![Logo](https://www.facebook.com/lambdatest/)

# lambdatest Examples Cucumber JUnit5 <a href="https://cucumber.io"><img src="https://brandslogos.com/wp-content/uploads/images/large/cucumber-logo.png" alt="Cucumber" height="22" /></a> <a href="https://junit.org/junit5/"><img src="https://junit.org/junit5/assets/img/junit5-logo.png" alt="JUnit5" height="22" /></a>

## Introduction

JUnit 5 is the next generation of JUnit. The goal of JUnit 5 is to create an up-to-date foundation for developer-side testing on the JVM. Cucumber is a software tool that supports behavior-driven development (BDD).



The Selenium test tests are run on different platforms like on-prem, docker and lambdatest using various run configurations and test capabilities.

---

## Repository setup

- Clone the repository

- For this infrastructure configuration (i.e on-premise), create the `drivers` folder at `/src/test/resources` and ensure that the ChromeDriver executable is placed in the `/src/test/resources/drivers` folder.

- Ensure you have the following dependencies installed on the machine
  - Java >= 8
  - Maven >= 3.1+
  - Gradle >= 5.0+

  Maven:
    ```sh
    mvn install
    ```

  Gradle:
    ```sh
    gradle build
    ```

#





## Configuring the maximum parallel test threads for this repository

For all the parallel run configuration profiles, you can configure the maximum parallel test threads by changing the settings below.

- Docker

  [docker-compose.yml](docker-compose.yml)
  
  scale = 4

- Lambdatest

  - Maven:

    [pom.xml](pom.xml)

    parallel-count = 5

  - Gradle:

    [build.gradle.kts](build.gradle.kts)

    parallelCount = 5

## Test Reporting

- [Allure reports](#generating-allure-reports)

---


## Running Your Tests

### Run a specific test on your own machine

- How to run the test?

  To run the default test scenario (e.g. End to End Scenario) on your own machine, use the following command:

  Maven:
    ```sh
  mvn test -P single
  ```

  Gradle:
    ```sh 
  gradle single
  ```

  To run a specific test scenario, use the following command with the additional 'test-name' argument:

  Maven:
  ```sh
  mvn test -P on-prem -Dtest-name="<Test scenario name>"
  ```

  Gradle:
  ```sh
  gradle on-prem -Dtest-name="<Test scenario name>"
  ```


### Run the entire test suite on your own machine

- How to run the test?

  To run the entire test suite on your own machine, use the following command:

  Maven:
  ```sh
  mvn test -P parallel
  ```

  Gradle:
  ```sh
  gradle parallel
  ```

- Output

  This run profile executes the entire test suite sequentially on a single 
  
  , on your own machine.

  
---





---

# Lambdatest


## Prerequisites

- For Mac 

  ```sh
  export LT_USERNAME=Lamdatest-username
  export LT_ACCESS_KEY=lambdatest-access
  ```

  - For Windows:

  ```shell
   export LT_USERNAME=Lamdatest-username
  export LT_ACCESS_KEY=lambdatest-access
  ```

 
- We have configured a list of test capabilities in the [caps.json](resources/conf/caps/caps.json) file. You can certainly update them based on your device / browser test requirements.



## Running Your Tests

### Run a specific test on lambdatest

In this section, we will run a single test on Chrome browser on lambdatest. To change test capabilities for this configuration, please refer to the `single` object in `caps.json` file.

- How to run the test?

  - To run the default test scenario (e.g. End to End Scenario) on your own machine, use the following command:

  Maven:
  ```sh
  mvn test -P single
  ```

  Gradle:
    ```sh
  gradle single
  ```

  To run a specific test scenario, use the following command with the additional 'test-name' argument:
  Maven:
  ```sh
  mvn test -P single -Dtest-name="<Test scenario name>"
  ```

  Gradle:
  ```sh
  gradle single -Dtest-name="<Test scenario name>"
  ```

  where,  the argument 'test-name' can be any Cucumber scenario name configured in this repository.



- Output



### Run the entire test suite in parallel on a single lambdatest browser

In this section, we will run the tests in parallel on a single browser on lambdatest. Refer to `single` object in `caps.json` file to change test capabilities for this configuration.

- How to run the test?

  To run the entire test suite in parallel on a single lambdatest browser, use the following command:

  Maven:
  ```sh
  mvn test -P parallel
  ```
  Gradle:
    ```sh
  gradle parallel
  ```


-
