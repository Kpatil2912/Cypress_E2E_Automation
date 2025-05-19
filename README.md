# 🚀 Cypress E2E Automation Practice Project

This is a sample end-to-end (E2E) test automation project using [Cypress](https://www.cypress.io/). It includes basic test scenarios, fixtures for test data, and best practices for scalable Cypress testing.

---

## 🧰 Tech Stack

* **Framework**: Cypress
* **Language**: JavaScript
* **Assertions**: Chai (Cypress built-in)
* **CI/CD Support**: GitHub Actions / Jenkins (optional)
* **Reporting**: Mochawesome or Allure (optional)

---

## 📁 Folder Structure

```
cypress-e2e-project/
├── cypress/
│   ├── e2e/                 # Test specs
│   ├── fixtures/            # Static test data (JSON, etc.)
│   ├── support/             # Custom commands and setup
├── screenshots/             # Auto-saved screenshots on failure
├── videos/                  # Auto-saved videos of test runs
├── cypress.config.js        # Cypress configuration file
├── package.json             # Project metadata and dependencies
└── README.md                # This file
```

---

## 🔧 Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/your-username/cypress-e2e-project.git
cd cypress-e2e-project
```

### 2. Install dependencies

```bash
npm install
```

---

## ▶️ Running Tests

### Interactive Mode (Cypress UI)

```bash
npx cypress open
```

### Headless Mode (CLI)

```bash
npx cypress run
```

---

## 🧪 Sample Test

A simple login test (`cypress/e2e/login.cy.js`):

```js
describe('Login Test', () => {
  it('should login with valid credentials', () => {
    cy.visit('/login');
    cy.get('#username').type('testuser');
    cy.get('#password').type('Password123');
    cy.get('#loginButton').click();
    cy.contains('Welcome').should('be.visible');
  });
});
```

---

## 📦 Using Fixtures

**File:** `cypress/fixtures/user.json`

```json
{
  "username": "testuser",
  "password": "Password123"
}
```

**Usage in test:**

```js
cy.fixture('user').then((user) => {
  cy.get('#username').type(user.username);
  cy.get('#password').type(user.password);
});
```

---

## ⚙️ Configuration

**File:** `cypress.config.js`

```js
const { defineConfig } = require('cypress');

module.exports = defineConfig({
  e2e: {
    baseUrl: 'https://example.com',
    setupNodeEvents(on, config) {
      // Add plugins here
    },
  },
});
```

---

## 🧼 Clean Up

To remove videos and screenshots from failed tests:

```bash
rm -rf cypress/videos cypress/screenshots
```

---

## 📊 Optional Reporting

To use Mochawesome:

```bash
npm install --save-dev mochawesome
```

---

## 📄 License

This project is licensed under the MIT License.

---

## 🙌 Contributing

Fork this repo, add your tests, and submit a pull request for review!

---

## 📚 Resources

* [Cypress Docs](https://docs.cypress.io)
* [Cypress Best Practices](https://docs.cypress.io/guides/references/best-practices)
