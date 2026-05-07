# OrangeHRM Test Automation Framework 🚀

A robust, scalable, and maintainable **Data-Driven Test Automation Framework** built specifically to test the OrangeHRM web application. This framework leverages the power of **Python**, **Selenium WebDriver**, and **Pytest**, implementing the **Page Object Model (POM)** design pattern.

---

## 🛠️ Tech Stack & Dependencies

*   **Language:** Python 3.x
*   **Web Automation:** Selenium WebDriver
*   **Testing Framework:** Pytest
*   **Parallel Execution:** Pytest-xdist
*   **Test Data Management:** Openpyxl (Excel)
*   **Reporting:** Allure Reports & Pytest-HTML
*   **Configuration Management:** Configparser

---

## 🏗️ Framework Architecture

1.  **Page Object Model (POM):** UI Locators (XPaths) and action methods are strictly separated from test scripts. You can find these in the `pageObjects` directory.
2.  **Data-Driven Testing (DDT):** Test data is completely separated from code. Complex testing parameters (like login credentials and expected outcomes) are driven from external Excel files stored in `Test_Data`.
3.  **Centralized Configuration:** Base URLs, default credentials, and other environment variables are managed from `Configuration/config.ini`.
4.  **Custom Logging:** Configured in `Utilities/logger.py` to trace step-by-step test execution and catch failures directly in `Logs/OrangeHRM.log`.

---

## 📁 Directory Structure

```text
OrangeHRM/
│
├── Configuration/          # Environment variables (config.ini)
├── pageObjects/            # Page classes containing locators and action methods
├── testCases/              # Pytest test scripts (e.g., test_OrangeHRM_Login_001.py)
│   └── conftest.py         # Pytest fixtures and WebDriver initialization logic
├── Test_Data/              # Excel files (.xlsx) for Data-Driven Testing
├── Utilities/              # Helper functions (ConfigReader, Logger, ExcelReader)
├── Logs/                   # Execution log files (.log)
├── Screenshots/            # Test failure & success screenshots (.png)
├── Html_Reports/           # Standalone HTML execution reports
├── Allure_Reports/         # Raw Allure result files
├── pytest.ini              # Pytest markers and configuration settings
├── Run.bat                 # Windows batch script for one-click test execution
└── README.md               # Project documentation
```

---

## ⚙️ Installation & Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/RB-QX-byte/OrangeHRM.git
   cd OrangeHRM
   ```

2. **Create a Virtual Environment (Optional but recommended):**
   ```bash
   python -m venv venv
   source venv/Scripts/activate  # On Windows
   ```

3. **Install Required Packages:**
   Make sure you install the necessary Python packages using pip:
   ```bash
   pip install pytest selenium pytest-html pytest-xdist allure-pytest openpyxl
   ```

---

## 🚀 Execution Guide

### Using Batch Script (Windows)
The easiest way to execute the full suite in parallel is by running the batch file provided:
Double-click `Run.bat` or execute it from the terminal:
```cmd
Run.bat
```

### Using Pytest CLI Commands
You can also run specific tests from the command line using Pytest:

**1. Run tests sequentially on Chrome:**
```bash
pytest -v -s testCases/test_OrangeHRM_Login_001.py --browser chrome
```

**2. Run tests in parallel (2 workers) on Firefox:**
```bash
pytest -v -n=2 testCases/ --browser firefox
```

**3. Run only Smoke tests:**
```bash
pytest -v -m "smoke" testCases/ --browser chrome
```

---

## 📊 Generating Test Reports

The framework supports two types of reports:

1. **HTML Report:**
   Automatically generated during execution. You can view the report in:
   `Html_Reports/OrangeHRM_Login_chrome.html`

2. **Allure Report:**
   To view the visually rich Allure report, you need Allure Command Line installed on your system. Run this command after tests finish:
   ```bash
   allure serve Allure_Reports
   ```
