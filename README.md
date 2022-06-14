![Logo](https://www.facebook.com/lambdatest/)

# lambdatest Examples Cucumber JUnit5 <a href="https://cucumber.io"><img src="https://brandslogos.com/wp-content/uploads/images/large/cucumber-logo.png" alt="Cucumber" height="22" /></a> <a href="https://junit.org/junit5/"><img src="https://junit.org/junit5/assets/img/junit5-logo.png" alt="JUnit5" height="22" /></a>

## Introduction

JUnit 5 is the next generation of JUnit. The goal of JUnit 5 is to create an up-to-date foundation for developer-side testing on the JVM. Cucumber is a software tool that supports behavior-driven development (BDD).

This lambdatest Example repository demonstrates a Selenium test framework written in Cucumber and Junit 5 with parallel testing capabilities. The Selenium test scripts are written for the open source [BrowserStack Demo web application](https://bstackdemo.com) ([Github](https://github.com/browserstack/browserstack-demo-app)). This BrowserStack Demo App is an e-commerce web application which showcases multiple real-world user scenarios. The app is bundled with offers data, orders data and products data that contains everything you need to start using the app and run tests out-of-the-box.

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

  This run profile executes the entire test suite sequentially on a single browser, on your own machine.

  
---



## Running Your Tests

### Run a specific test on the docker infrastructure

- How to run the test?

  - Start the Docker by running the following command:

  ```sh
  docker-compose up -d
  ```

  - To run the default test scenario (e.g. End to End Scenario) on your own machine, use the following command:

  Maven:
  ```sh
  mvn test -P docker
  ```

  Gradle:
    ```sh
  gradle docker
  ```

  To run a specific test scenario, use the following command with the additional 'test-name' argument:

  Maven:
  ```sh
  mvn test -P docker -Dtest-name="<Test scenario name>"
  ```

  Gradle:
  ```sh
  gradle docker -Dtest-name="<Test scenario name>"
  ```



### Run the entire test suite in parallel using Docker

- How to run the test?

  - Start the docker image first by running the following command:

  ```sh
  docker-compose up -d
  ```

  - To run the entire test suite in parallel on the docker image, use the following command:

  Maven:
  ```sh
  mvn test -P docker-parallel
  ```

  Gradle:
  ```sh
  gradle docker-parallel
  ```

  - After the tests are complete stop the Selenium grid by running the following command:

  ```sh
  docker-compose down
  ```

- Output

  This run profile executes the entire test suite in parallel on a single browser, deployed on a docker image.

- Note: By default, this execution would run maximum 5 test threads in parallel on Docker. Refer to the section ["Configuring the maximum parallel test threads for this repository"](#Configuring-the-maximum-parallel-test-threads-for-this-repository) for updating the parallel thread count based on your requirements.

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

### Run a specific test on BrowserStack

In this section, we will run a single test on Chrome browser on Browserstack. To change test capabilities for this configuration, please refer to the `single` object in `caps.json` file.

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



### Run the entire test suite in parallel on a single BrowserStack browser

In this section, we will run the tests in parallel on a single browser on Browserstack. Refer to `single` object in `caps.json` file to change test capabilities for this configuration.

- How to run the test?

  To run the entire test suite in parallel on a single BrowserStack browser, use the following command:

  Maven:
  ```sh
  mvn test -P parallel
  ```
  Gradle:
    ```sh
  gradle parallel
  ```


-
