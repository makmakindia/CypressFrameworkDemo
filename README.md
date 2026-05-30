# Cypress Automation Framework

## Overview

This repository contains a Cypress automation framework for end-to-end web testing. The framework is designed for maintainable, scalable test automation with reusable page objects, centralized test data, and CI-friendly execution.

## Project Structure

- `cypress/`
  - `e2e/`: Test specification files.
  - `fixtures/`: Test data and mock data.
  - `support/`: Custom commands, utilities, and reusable helper functions.
  - `pages/`: Page object models for application pages.
- `cypress.config.js`: Cypress configuration file and environment settings.
- `package.json`: Project dependencies and npm scripts.
- `README.md`: Project documentation.

## Setup

1. Install dependencies:
   ```bash
   npm install
   ```
2. Open Cypress Test Runner:
   ```bash
   npx cypress open
   ```
3. Run tests in headless mode:
   ```bash
   npx cypress run
   ```

## Architecture

This framework separates concerns into test definitions, page interactions, and shared helpers.

### 1. High-level Workflow

```
[Tester / CI] --> [Cypress Test Runner]
[Cypress Test Runner] --> [Test Specs (cypress/e2e)]
[Test Specs] --> [Page Objects (cypress/pages)]
[Page Objects] --> [UI Actions / Assertions]
[UI Actions / Assertions] --> [Browser / Application Under Test]
```

### 2. Component Diagram

```
+----------------------+      +---------------------------+
| Cypress Automation    |<---->| Web Application / Browser |
| Framework             |      +---------------------------+
+----------------------+                ^
         ^                              /
         |                             /
+----------------------+    +---------------------------+
| Test Specs           |    | Fixtures / Test Data      |
| (cypress/e2e)        |    | (cypress/fixtures)        |
+----------------------+    +---------------------------+
         |
         v
+----------------------+    +---------------------------+
| Page Objects         |--->| Support / Helpers         |
| (cypress/pages)      |    | (cypress/support)         |
+----------------------+    +---------------------------+
```

### 3. Execution Flow

```
[CI / Local] -> npm script -> Cypress runner -> load spec file -> use page object -> interact with UI -> verify results -> report outcome
```

## Key Concepts

- Page Object Model (POM): Encapsulates page actions and selectors into reusable modules.
- Custom Commands: Extend Cypress with reusable commands in `cypress/support/commands.js`.
- Fixtures: Store structured test data separately from the test code.
- Configurable Environment: Use `cypress.config.js` for baseUrl, viewport, retries, and environment variables.

## Best Practices

- Keep test cases small and independent.
- Use page objects for UI interactions and selectors.
- Use fixtures for test data and expected values.
- Avoid hard-coded waits; rely on Cypress automatic waiting and retries.
- Add clear assertions for every test step.

## Notes

- Update `cypress.config.js` for the target environment and base URL.
- Integrate with CI for automated, repeatable test execution.
- Keep all selectors and helpers centralized for easier maintenance.
