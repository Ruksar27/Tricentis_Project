# Tricentis_Project
The Tricentis Insurant Vehicle project focuses on automating the testing processes for a vehicle insurance application using Selenium WebDriver. This project aims to ensure the application's functionality, reliability, and performance through comprehensive automated testing strategies.

Project Overview
The Tricentis Insurant Vehicle project utilizes Selenium to automate end-to-end testing of the vehicle insurance application. The primary goal is to validate user interactions, data processing, and overall application behavior in various scenarios, ensuring that all features perform as expected under different conditions.
Key Features
End-to-End Testing: The project covers critical user journeys within the vehicle insurance application, including quote generation, policy management, and customer information updates.
Selenium WebDriver: Employed for automating browser interactions, allowing for the simulation of real user behavior on the web application.
TestNG Framework: Utilized for organizing test cases, managing test execution, and providing detailed reporting capabilities.
Data-Driven Testing: Supports various input scenarios through external data sources (e.g., CSV or Excel files), enhancing test coverage and flexibility.

Technologies Used
Selenium WebDriver: The primary tool for automating web application testing.
Java: The programming language used for writing test scripts.
TestNG: A testing framework that provides advanced features such as parallel execution and dependency management.
Maven: Used for project management and dependency resolution.

Testing Scenarios
The project includes a variety of testing scenarios such as:
Navigating to the insurance quote page and entering user information.
Generating quotes based on different vehicle types and coverage options.
Validating the accuracy of quotes against expected values.
Updating customer information and verifying changes in the system.
Testing error handling by submitting invalid data.

Execution and Reporting
Tests are executed using Maven commands, which compile the test classes and run the TestNG test suite. After execution, detailed reports are generated that provide insights into test results, including passed/failed tests and any errors encountered during execution.

Benefits
By implementing this automation project, organizations can achieve significant improvements in their software testing processes. The use of Selenium allows for faster test execution cycles, reduced manual testing efforts, and increased reliability in detecting defects early in the development lifecycle. This ultimately leads to higher quality software releases and improved customer satisfaction in the vehicle insurance domain.

This project demonstrates the implementation of Automation Testing for the Tricentis Insurant Vehicle application using Selenium WebDriver, TestNG, and Maven. The purpose of this project is to automate the testing of key functionalities of the Tricentis Insurant Vehicle application, ensuring that all user interactions and system behaviors are thoroughly tested.

Prerequisites
Before setting up the project, make sure you have the following tools and software installed:

Java JDK 8 or above: Required for running Selenium and TestNG tests.
Maven: Dependency management and build tool.
Eclipse IDE or IntelliJ IDEA: IDE for writing and executing test scripts.
Selenium WebDriver: A tool for automating browsers.
TestNG: A testing framework used to create and execute tests.
ChromeDriver: Required for running the tests on the Chrome browser.
Step-by-Step Setup:
Java Installation:
Download and install Java JDK from the official Oracle website. Ensure that you set up the JAVA_HOME environment variable correctly.

Maven Installation:
Download and install Maven from the official Maven website. After installation, set up the MAVEN_HOME environment variable and add Maven to your system's PATH.

Browser Driver:
Download the appropriate WebDriver for your browser:

ChromeDriver: Download ChromeDriver
GeckoDriver: Download GeckoDriver
Make sure to add the driver path to your system’s PATH environment variable.
IDE Setup:
Download and install an IDE of your choice:

Eclipse IDE
IntelliJ IDEA
Project Setup
1. Clone the repository:
bash
Copy code
git clone https:[//github.com/your-username/tricentis-insurant-vehicle-automation.git](https://github.com/Ruksar27/Tricentis_Project)
2. Import the project into your IDE:
Open your IDE (Eclipse/IntelliJ IDEA).
Import the project as a Maven Project.
3. Maven Dependencies:
Maven will automatically download the necessary dependencies as defined in the pom.xml file. Here’s an example of some of the key dependencies included:

xml
Copy code
<!--
			https://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java -->
			<dependency>
				<groupId>org.seleniumhq.selenium</groupId>
				<artifactId>selenium-java</artifactId>
				<version>4.24.0</version>
			</dependency>
			
			<!-- https://mvnrepository.com/artifact/org.testng/testng -->
<dependency>
    <groupId>org.testng</groupId>
    <artifactId>testng</artifactId>
    <version>7.10.2</version>
    <scope>test</scope>
</dependency>
<!-- https://mvnrepository.com/artifact/org.testng/testng -->


<!-- https://mvnrepository.com/artifact/org.apache.poi/poi -->
<dependency>
    <groupId>org.apache.poi</groupId>
    <artifactId>poi</artifactId>
    <version>5.3.0</version>
</dependency>

<!-- https://mvnrepository.com/artifact/org.apache.poi/poi-ooxml -->
<dependency>
    <groupId>org.apache.poi</groupId>
    <artifactId>poi-ooxml</artifactId>
    <version>5.3.0</version>
</dependency>

<!-- https://mvnrepository.com/artifact/commons-io/commons-io -->
<dependency>
    <groupId>commons-io</groupId>
    <artifactId>commons-io</artifactId>
    <version>2.18.0</version>
</dependency>

<!-- https://mvnrepository.com/artifact/com.aventstack/extentreports -->
<dependency>
    <groupId>com.aventstack</groupId>
    <artifactId>extentreports</artifactId>
    <version>5.1.2</version>
</dependency>
Project Structure
1. TestNG Configuration:
Test cases are organized in TestNG XML format and executed in sequence as defined in the testng.xml file.

Sample testng.xml configuration:

xml
Copy code
<?xml version="1.0" encoding="UTF-8"?>
<suite name="Tricentis Insurant Vehicle Suite">
    <test name="Login Tests">
        <classes>
            <class name="com.tricentis.tests.LoginTest"/>
        </classes>
    </test>
    <test name="Vehicle Insurance Tests">
        <classes>
            <class name="com.tricentis.tests.VehicleTest"/>
        </classes>
    </test>
</suite>
2. Test Classes:
Test cases are written in Java using Selenium WebDriver for browser automation and TestNG for creating and running tests.

Example:

LoginTest.java
java
Copy code
package com.tricentis.tests;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.annotations.AfterMethod;
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.Test;

public class LoginTest {

    WebDriver driver;

    @BeforeMethod
    public void setup() {
        // Set path for the WebDriver (e.g., ChromeDriver)
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        driver = new ChromeDriver();
        driver.get("https://www.tricentis.com/insurant-vehicle");
    }

    @Test
    public void testLogin() {
        // Perform login and validate successful login
        LoginPage loginPage = new LoginPage(driver);
        loginPage.enterUsername("user");
        loginPage.enterPassword("password");
        loginPage.clickLoginButton();

        Assert.assertTrue(driver.getTitle().contains("Insurant Vehicle"));
    }

    @AfterMethod
    public void teardown() {
        // Close the browser after each test
        driver.quit();
    }
}
3. Page Object Model (POM):
To improve maintainability and readability, the Page Object Model (POM) design pattern is used. Each page of the application will have its own corresponding page class, where interactions with that page are defined.

For example, for the login page:

LoginPage.java (Page Object)
java
Copy code
package com.tricentis.pages;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

public class LoginPage {

    WebDriver driver;

    // Locators for the login page elements
    By usernameField = By.id("username");
    By passwordField = By.id("password");
    By loginButton = By.id("login");

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }

    public void enterUsername(String username) {
        WebElement usernameElem = driver.findElement(usernameField);
        usernameElem.sendKeys(username);
    }

    public void enterPassword(String password) {
        WebElement passwordElem = driver.findElement(passwordField);
        passwordElem.sendKeys(password);
    }

    public void clickLoginButton() {
        driver.findElement(loginButton).click();
    }
}
Running the Tests
1. Running via Maven:
Run all the test cases using the following Maven command:

bash
Copy code
mvn clean test
This command will:

Clean the project.
Execute the tests defined in the TestNG XML file.
2. Running via IDE:
You can also run the tests directly from your IDE:

Right-click the testng.xml file.
Select Run As > TestNG Suite.
Reporting
After the tests are executed, TestNG generates a detailed report in the target/test-classes folder. You can open the index.html file in your browser to view the test results.

Features
Selenium WebDriver: Used for automating browsers (Chrome, Firefox, etc.).
TestNG: Testing framework to organize and run tests, as well as generate reports.
Maven: For dependency management and building the project.
Page Object Model (POM): Keeps the code clean and maintainable by separating the test logic from page interactions.
Contribution
If you'd like to contribute to this project, feel free to fork the repository, make changes, and submit a pull request.

License
This project is licensed under the MIT License. See the LICENSE file for details.

