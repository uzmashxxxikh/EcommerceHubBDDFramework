# 🛒 EcommerceHub BDD Automation Framework

A scalable, modular, and maintainable Behavior-Driven Development (BDD) test automation framework built using **Java**, **Selenium WebDriver**, **Cucumber**, and **TestNG**. Designed following the **Page Object Model (POM)** design pattern, this framework supports cross-browser execution, parallel testing, and rich HTML/Extent reporting with automated failure screenshots.

---

## 📋 Table of Contents
- [Tech Stack & Tools](#-tech-stack--tools)
- [Framework Architecture](#-framework-architecture)
- [Key Features](#-key-features)
- [Prerequisites](#-prerequisites)
- [Getting Started](#-getting-started)
- [Running Tests](#-running-tests)
- [Reporting & Logs](#-reporting--logs)
- [Contributing](#-contributing)

---

## 🛠 Tech Stack & Tools

| Category | Technology |
| :--- | :--- |
| **Language** | Java (JDK 11 / 17+) |
| **UI Automation** | Selenium WebDriver |
| **BDD Framework** | Cucumber (Gherkin) |
| **Test Runner & Assertions** | TestNG |
| **Build & Dependency Management** | Apache Maven |
| **Design Pattern** | Page Object Model (POM) with PageFactory |
| **Reporting** | ExtentReports (Spark), Cucumber HTML/JSON Reports |
| **Logging** | Log4j2 |
| **CI/CD & Version Control** | Git & GitHub |

---

## 🏗 Framework Architecture

```text
EcommerceHubBDDFramework/
├── src/
│   ├── main/
│   │   └── java/
│   │       └── pageObjects/          # Page Object classes & WebElement locators
│   └── test/
│       ├── java/
│       │   ├── hooks/                # Cucumber @Before & @After hooks (setup, teardown, screenshots)
│       │   ├── runners/              # TestNG Cucumber TestRunner classes
│       │   ├── stepDefinitions/      # Gherkin step definition implementations
│       │   ├── testBase/             # BaseClass (WebDriver initialization, config loading)
│       │   └── utilities/            # Reusable helpers (DataProviders, Excel/JSON readers, waits)
│       └── resources/
│           ├── features/             # Gherkin .feature files (Login, Registration, Cart, Checkout)
│           ├── config.properties     # Environment URLs, browser settings, credentials
│           ├── extent.properties     # ExtentReports configuration
│           └── log4j2.xml            # Log4j2 logging configuration
├── testData/                         # External test data files (Excel, JSON, CSV)
├── testng.xml                        # TestNG suite configuration (cross-browser & parallel setup)
├── pom.xml                           # Maven dependencies and build plugins
├── .gitignore                        # Ignored build artifacts (target/, test-output/, logs/)
└── README.md                         # Project documentation
```

---

## ✨ Key Features

- **Behavior-Driven Development (BDD):** Human-readable test scenarios written in Gherkin syntax (`.feature` files) bridging the gap between business stakeholders and QA engineers.
- **Page Object Model (POM):** Clean separation between test logic and UI locators for effortless maintenance when UI elements change.
- **Cross-Browser Execution:** Seamlessly run tests across **Chrome**, **Edge**, and **Firefox** via `testng.xml` parameters or Maven CLI properties.
- **Automated Screenshot Capture on Failure:** Cucumber `@After` hooks automatically capture and embed screenshots directly into ExtentReports whenever a scenario fails.
- **Centralized Configuration:** Environment variables, base URLs, timeouts, and browser preferences are managed cleanly in `config.properties`.
- **Comprehensive Logging:** Detailed execution logs tracked via Log4j2 for rapid debugging.

---

## 💻 Prerequisites

Before setting up the project locally, ensure you have the following installed:
1. **Java Development Kit (JDK)** 11 or higher (`java -version`)
2. **Apache Maven** 3.8+ (`mvn -version`)
3. **Git** (`git --version`)
4. **IDE** (Eclipse, IntelliJ IDEA, or VS Code with Cucumber & TestNG plugins)
5. **Browsers:** Google Chrome, Microsoft Edge, or Mozilla Firefox installed locally

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/uzmashxxxikh/EcommerceHubBDDFramework.git
cd EcommerceHubBDDFramework
```

### 2. Configure Environment Settings
Open `src/test/resources/config.properties` and update the application URL, default browser, or test credentials as needed:
```properties
appURL=https://your-ecommerce-application-url.com
browser=chrome
execution_env=local
```

### 3. Install Dependencies
Run Maven to download all required dependencies defined in `pom.xml`:
```bash
mvn clean install -DskipTests
```

---

## 🧪 Running Tests

### Option 1: Run via Maven Command Line
Execute the entire test suite using Maven:
```bash
mvn clean test
```

Run tests filtered by specific Cucumber tags (e.g., `@smoke` or `@regression`):
```bash
mvn test -Dcucumber.filter.tags="@smoke"
```

### Option 2: Run via TestNG (`testng.xml`)
1. Open the project in **Eclipse** or **IntelliJ IDEA**.
2. Right-click on `testng.xml` in the project root.
3. Select **Run As > TestNG Suite** (this will trigger cross-browser execution across Chrome, Edge, and Firefox as configured in the suite).

### Option 3: Run via Cucumber `TestRunner`
1. Navigate to `src/test/java/runners/TestRunner.java`.
2. Right-click inside the class and select **Run As > TestNG Test**.

---

## 📊 Reporting & Logs

After test execution completes, reports and logs are generated automatically (note: these directories are ignored in Git):

- **Extent Spark Report:**  
  `target/ExtentReport/ExtentSpark.html` — Interactive dashboard displaying passed/failed scenarios, execution duration, step-by-step logs, and embedded failure screenshots.
- **Cucumber Native HTML Report:**  
  `target/cucumber-report.html`
- **TestNG Reports:**  
  `test-output/emailable-report.html` and `test-output/index.html`
- **Execution Logs:**  
  `logs/automation.log` — Detailed runtime logs generated by Log4j2.

---

## 🤝 Contributing

1. Fork the repository.
2. Create a new feature branch (`git checkout -b feature/your-feature-name`).
3. Commit your changes (`git commit -m "feat: add new checkout scenario"`).
4. Push to your branch (`git push origin feature/your-feature-name`).
5. Open a Pull Request.
