# Advanced JS & Playwright Test Automation Framework

A scalable and maintainable UI Automation Framework built using **Playwright** and **JavaScript**, following industry-standard automation design patterns such as **Page Object Model (POM)**, **Fixture-Based Architecture**, **Browser Wrapper Design**, and **Custom Element Abstraction**.

This project demonstrates advanced automation engineering practices by building a reusable framework instead of writing standalone test scripts.


---

## ✨ Key Features & Technical Highlights

* **🚀 Playwright Native Power**: Executed on Chromium, Firefox, and WebKit, utilizing Playwright's parallel execution and auto-wait mechanisms.
* **🛡️ Strict Test Isolation (Custom Fixtures)**: Uses custom test-scoped fixtures to instantiate a fresh browser context, isolate download directories on disk, clear state, and guarantee zero test pollution.
* **📦 Custom Element Wrappers**: Encapsulates common elements (`Button`, `TextBox`, `Checkbox`, `Dropdown`, `FileInput`, `Label`) inheriting from `BaseElement`. This limits duplicate code and standardizes interactions.
* **⚙️ Dynamic State Assertion Handling**: An `ElementStateHandler` provides fail-safe assertions (`isEnabled`, `isDisplayed`, `isClickable`, `isSelected`) returning clean boolean values without throwing page-crashing locator exceptions.
* **📑 Page Object Model (POM) Structure**: Promotes readability and clean page object design with automatic page landmark verification via a base page constructor.
* **📂 Configuration Separability**: Environment configuration (`settings.json`) and test data values (`testdata.json`) are decoupled from code.
* **🌐 Embedded iFrames & Multi-Tab Support**: Includes robust helpers (`FrameUtils.js`) for nested frame automation and tab-switching handlers inside `Browser.js`.

---

## 🏗️ Project Structure

```text
a1qa-js-playwright-framework/
├── framework/
│   ├── config/
│   │   ├── settings.json         # Environment URL, timeouts, and download paths
│   │   └── testdata.json         # Decoupled test parameters & credentials
│   ├── ui/
│   │   ├── browser/
│   │   │   └── Browser.js        # Core wrapper managing pages, tabs, alerts, and downloads
│   │   ├── constants/
│   │   │   ├── ElementType.js    # Element type definitions
│   │   │   └── Timeouts.js       # Centralized timeout settings
│   │   ├── elements/             # Domain element wrappers
│   │   │   ├── helpers/
│   │   │   │   ├── ElementsList.js   # Wrapper for index-based locator arrays
│   │   │   │   └── elementState.js   # Robust page state validation
│   │   │   ├── BaseElement.js    # Parent class for element objects
│   │   │   ├── Button.js
│   │   │   ├── Checkbox.js
│   │   │   ├── Dropdown.js
│   │   │   ├── FileInput.js
│   │   │   ├── Label.js
│   │   │   ├── TextBox.js
│   │   │   └── index.js
│   │   ├── fixtures/
│   │   │   └── browser.fixture.js # Extension of test runners injecting customBrowser
│   │   └── page/
│   │       └── BasePage.js       # Abstract base class for Page Objects
│   └── utils/
│       ├── ConfigReader.js       # Central configuration loader
│       ├── FrameUtils.js         # Nested iFrame traversal utilities
│       └── locatorHelper.js      # Global locator helpers
├── tests/
│   ├── pages/                    # Domain Page Objects
│   │   ├── FileUploaderPages/
│   │   │   ├── FileUploaderPage.js
│   │   │   └── UploadedFilesPage.js
│   │   ├── FramePages/
│   │   │   ├── FramesPage.js
│   │   │   └── IFramePage.js
│   │   ├── DynamicControlsPage.js
│   │   ├── FileDownloadPage.js
│   │   ├── JavaScriptAlertsPage.js
│   │   ├── LoginPage.js
│   │   ├── MainPage.js
│   │   ├── SecureAreaPage.js
│   │   └── TablesPage.js
│   ├── resources/
│   │   └── test.txt              # Sample file for upload tests
│   ├── alert.spec.js             # Native JS Dialog execution
│   ├── dynamic_controls.spec.js  # Dynamic state change and waiter validation
│   ├── file_download.spec.js     # Browser download interception
│   ├── file_upload.spec.js       # Custom FileInput attachment validation
│   ├── formauth.spec.js          # Authentication flow validation
│   ├── iframe.spec.js            # iFrame traversal validation
│   └── tables.spec.js            # Column parsing and list mappings
├── package.json
├── playwright.config.js
└── README.md
```
* Allure Report

<img width="1919" height="920" alt="image" src="https://github.com/user-attachments/assets/120d6141-fa24-4436-97e0-4085afdf389c" />


## 🛠️ Setup & Installation

### Prerequisites
* **Node.js**: Version 18.x or higher
* **NPM**: (bundled with Node.js)

### 1. Clone & Install Dependencies
```bash
git clone https://github.com/<your-username>/JavaScript-Playwright-Framework.git
cd JavaScript-Playwright-Framework
npm install
```

### 2. Install Playwright Browsers
```bash
npx playwright install
```

---

## 🚦 Running Tests

To run the complete test suite:
```bash
npx playwright test
```

### Run Tests in Headed Mode
```bash
npx playwright test --headed
```

### Run a Specific Test File
```bash
npx playwright test tests/formauth.spec.js
```

### View Test Reports
```bash
allure serve allure-results
```

---
