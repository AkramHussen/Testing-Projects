
# Automation Testing Project - SauceDemo.com with Jenkins CI/CD Integration (DEPI – Digital Egypt Pioneers Initiative Graduation Project)

Maintained and showcased by **Akram Hussen Ibraheem**.

---

## 📚 Contents

- [📋 Project Overview](#-project-overview)
- [🎯 Scope](#-scope)
- [🛠️ Tools & Technologies](#-tools--technologies)
- [📁 Project Structure](#-project-structure)
- [🚀 Architecture & Design Patterns](#-architecture--design-patterns)
- [🧩 Key Components](#-key-components)
- [🧱 Test Design with TestNG](#-test-design-with-testng)
- [📊 Allure Reporting](#-allure-reporting)
- [🔁 Jenkins CI/CD Integration](#-jenkins-cicd-integration)
- [▶️ How to Run the Tests Locally](#️-how-to-run-the-tests-locally)
- [✨ Future Enhancements](#-future-enhancements)
- [👥 Project Team](#-project-team)
- [📧 Contact](#-contact)

---

## 📋 Project Overview

This project is an end‑to‑end UI automation testing framework for the **SauceDemo** web application.  
It is built using **Java, Selenium WebDriver, TestNG, Maven, Allure Reports, and Jenkins CI/CD** and follows modern automation best practices.

The framework automates the full purchase flow on SauceDemo, from login to order confirmation, and is designed to be:

- Readable and maintainable
- Scalable for adding new test cases and features
- Suitable for CI/CD pipelines and team collaboration

### ✅ Key Framework Practices

- **Page Object Model (POM)**
- **Fluent Design Pattern**
- **Reusable Utilities & Custom Bot Wrapper**
- **Structured Test Suites via `testng.xml`**
- **Allure Reporting Integration**
- **Jenkins CI/CD Integration**
- **Data‑driven testing using JSON**

---

## 🎯 Scope

The automated tests cover the core business flows of SauceDemo:

- Login functionality (valid, invalid, and edge cases)
- Home page and product listing
- Add to cart functionality
- Shopping cart management
- Checkout process (information, overview, confirmation)
- End‑to‑end user purchase workflows
- Product filtering and sorting

---

## 🛠️ Tools & Technologies

- **Language:** Java (17+)
- **Automation:** Selenium WebDriver (4.x)
- **Test Runner:** TestNG (7.x)
- **Build Tool:** Maven (3.6+)
- **Design Patterns:** Page Object Model (POM), Singleton, Bot Pattern
- **Logging:** Log4j2
- **Reporting:** Allure Reports
- **CI/CD:** Jenkins Pipeline (`Jenkinsfile`)
- **IDE:** IntelliJ IDEA
- **Testing Website:** https://www.saucedemo.com
- **Training Provider:** Skills Dynamix

---

## 📁 Project Structure

NHA-201 [Team201_SaucedemoTesting]/
│
├── .allure/ # Allure configuration files
├── .idea/ # IntelliJ IDEA configuration
├── allure-report/ # Generated Allure reports
├── allure-results/ # Allure test results
│
├── src/
│ ├── main/
│ │ └── java/
│ │ ├── Drivers/
│ │ │ └── DriverFactory.java # WebDriver creation and management
│ │ │
│ │ ├── Engine/
│ │ │ ├── Bot.java # Bot pattern implementation
│ │ │ ├── BotData.java # JSON test data handling
│ │ │ └── BotLogger.java # Logging utility (Log4j2)
│ │ │
│ │ └── SauceDemoPages/
│ │ ├── CartPage.java # Shopping cart page object
│ │ ├── CheckoutConfirmationPage.java # Order confirmation page object
│ │ ├── CheckoutPage.java # Checkout form page object
│ │ ├── HomePage.java # Home/Inventory page object
│ │ ├── LoginPage.java # Login page object
│ │ └── SortingFilterPage.java # Product filtering/sorting page object
│ │
│ ├── test/
│ │ └── java/
│ │ ├── Base/
│ │ │ └── BaseTest.java # Abstract base class with setup/teardown
│ │ │
│ │ ├── DataDrivenTest/
│ │ │ └── TestDataProvider.java # Data-driven test data provider (JSON)
│ │ │
│ │ ├── Listener/
│ │ │ ├── IInvokedMethodResultListener.java # Test method listener
│ │ │ └── ITestResultListener.java # Test result listener
│ │ │
│ │ └── SauceDemoTests/
│ │ ├── CartPageTests.java # Cart functionality tests
│ │ ├── CheckoutConfirmationPageTests.java
│ │ ├── CheckoutPageTests.java # Checkout process tests
│ │ ├── EndToEndTest.java # End-to-end workflow tests
│ │ ├── HomePageTest.java # Home page tests
│ │ ├── LoginPageTests.java # Login tests
│ │ └── SortingFilterPageTest.java # Filtering and sorting tests
│ │
│ └── resources/ # Test resources and configuration
│
├── resources/ # Project-level resources
├── test-output/ # TestNG default test output
├── pom.xml # Maven configuration and dependencies
├── Jenkinsfile # Jenkins Pipeline configuration
├── README.md # Project documentation
│
└── tests/
├── Smoke.xml # TestNG suite for smoke tests
└── Regression.xml # TestNG suite for regression tests

text

---

## 🚀 Architecture & Design Patterns

The framework uses several design patterns to keep the codebase clean and maintainable.

### Page Object Model (POM)

- Each page in the application has a dedicated class.
- UI locators and actions are encapsulated inside page classes.
- Reduces duplication and improves readability.

### Singleton Pattern

- Ensures a single WebDriver instance is reused when appropriate.
- Centralized driver management via `DriverFactory`.
- Helps with resource usage and test stability.

### Bot Pattern

- High‑level semantic methods group multiple actions into readable steps, such as `performLogin()` or complete checkout flows.
- Tests become more expressive and closer to business language.

### Abstract Base Class

- `BaseTest` provides shared setup (`@BeforeMethod`) and teardown (`@AfterMethod`).
- Centralizes WebDriver initialization, configuration, and cleanup.
- Common utilities and hooks for logging and reporting.

---

## 🧩 Key Components

### 1️⃣ BotData (Engine)

- Centralized JSON reader for test data.
- Handles parsing of objects and arrays from JSON files.
- Enables clean and scalable data‑driven testing.

### 2️⃣ BotLogger (Engine)

- Custom logger built on **Log4j2**.
- Logs each important action and assertion.
- Integrates with Allure to attach logs for failed test analysis.

### 3️⃣ DriverFactory (Drivers)

- Manages WebDriver setup and teardown.
- Supports multiple browsers (Chrome, Firefox, Edge).
- Contains browser‑specific configurations and options.
- Extensible for adding more browsers or remote drivers (e.g. Selenium Grid).

---

## 🧱 Test Design with TestNG

TestNG is used for:

- Test structure and annotations (`@Test`, `@BeforeMethod`, `@AfterMethod`, etc.)
- Parallel execution support
- Data Providers for data‑driven tests
- Custom listeners for logging and reporting
- Organizing suites via:
    - `tests/Smoke.xml`
    - `tests/Regression.xml`

---

## 📊 Allure Reporting

The project integrates **Allure** to provide:

- Rich visual reports for each test run
- Screenshots on failure
- Step‑level reporting via annotations and logging
- Attached logs to help debugging failed tests

To generate the report after running tests:

allure serve allure-results

text

---

## 🔁 Jenkins CI/CD Integration

The project includes a `Jenkinsfile` to enable CI/CD pipelines:

- Checkout the repository
- Run `mvn clean test` with the selected TestNG suite
- Generate Allure results
- Publish Allure reports inside Jenkins

This allows continuous feedback on the health of the automated tests (for example, on every push or scheduled build).

---

## ▶️ How to Run the Tests Locally

1. **Clone the repository**

git clone <repo-url>
cd <project-folder>

text

2. **Install dependencies**

mvn clean install

text

3. **Run Smoke suite**

mvn clean test -DsuiteXmlFile=tests/Smoke.xml

text

4. **Run Regression suite**

mvn clean test -DsuiteXmlFile=tests/Regression.xml`

text

5. **Generate Allure report**

allure serve allure-results

text

---

## ✨ Future Enhancements

- Add more functional and negative test cases
- Extend coverage for edge cases and error handling
- Integrate CI/CD with **GitHub Actions** in addition to Jenkins
- Add support for **WebDriverManager** to simplify driver binaries
- Add cross‑browser and cross‑platform execution options

---

## 👥 Project Team

This project was originally developed as a team graduation project (Group 201) in the DEPI Software Testing Track.  
Below are the team members who contributed to the project:

- **Akram Hussen**
- **Ali Nabil**
- **Nada Khamis**
- **Ola Sabry**
- **Mohamed Mahmoud**

---

## 📧 Contact

For questions or collaboration opportunities related to this project:

**Akram Hussen Ibraheem**  
QA Engineer / Test Automation  
LinkedIn: https://www.linkedin.com/in/akram-hussen-bb5599357  
WhatsApp: https://wa.me/201225385589