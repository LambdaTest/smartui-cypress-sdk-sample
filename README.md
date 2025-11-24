# SmartUI SDK Sample for Cypress

Welcome to the SmartUI SDK sample for Cypress. This repository demonstrates how to integrate SmartUI visual regression testing with Cypress.

## Repository Structure

```
smartui-cypress-sdk-sample/
├── cypress/
│   └── e2e/
│       └── smartuiSDKLocal.cy.js    # Test file
├── cypress.config.js                # Cypress configuration
├── package.json                     # Dependencies
└── smartui-web.json                # SmartUI config (create with npx smartui config:create)
```

## 1. Prerequisites and Environment Setup

### Prerequisites

- Node.js installed
- Cypress >= 10.0.0 (SmartUI SDK only supports Cypress versions >= 10.0.0)
- Chrome browser (for Local tests)

### Environment Setup

**For Local:**
```bash
export PROJECT_TOKEN='your_project_token'
```

## 2. Initial Setup and Dependencies

### Clone the Repository

```bash
git clone https://github.com/LambdaTest/smartui-cypress-sdk-sample
cd smartui-cypress-sdk-sample
```

### Install Dependencies

Install required NPM modules for LambdaTest Smart UI Cypress SDK:

```bash
npm i @lambdatest/smartui-cli @lambdatest/cypress-driver cypress@^13
```

**Dependencies included:**
- `@lambdatest/smartui-cli` - SmartUI CLI
- `@lambdatest/cypress-driver` - SmartUI Cypress driver
- `cypress@^13` - Cypress framework

### Configure Cypress Support File

Add the following import to your `cypress/support/e2e.js` file:

```javascript
import '@lambdatest/cypress-driver'
```

### Create SmartUI Configuration

```bash
npx smartui config:create smartui-web.json
```

## 3. Steps to Integrate Screenshot Commands into Codebase

The SmartUI screenshot function is already implemented in the repository.

**Test File** (`cypress/e2e/smartuiSDKLocal.cy.js`):
```javascript
describe('Test Case name', () => {
  beforeEach(() => {
    cy.visit('Required URL')
  })

  it('SmartUI Snapshot', () => {
    cy.smartuiSnapshot('Screenshot Name');
  })
})
```

**Note**: The code is already configured and ready to use. You can modify the URL and screenshot name if needed.

## 4. Execution and Commands

### Local Execution

```bash
npx smartui exec -- npx cypress run --spec cypress/e2e/smartuiSDKLocal.cy.js --browser chrome --headed
```

**Note**: The `--config` flag is optional if your config file is named `smartui-web.json` and located in the current directory. If you need to specify a different config file, use: `npx smartui --config <path> exec -- npx cypress run --spec cypress/e2e/smartuiSDKLocal.cy.js --browser chrome --headed`

## Test Files

### Test File (`cypress/e2e/smartuiSDKLocal.cy.js`)

- Runs Cypress locally using Chrome
- Requires Chrome browser installed
- Takes screenshot with name: `Screenshot Name`

## Configuration

### Cypress Config (`cypress.config.js`)

The Cypress configuration file is pre-configured for SmartUI integration.

### SmartUI Config (`smartui-web.json`)

Create the SmartUI configuration file using:
```bash
npx smartui config:create smartui-web.json
```

The default configuration includes:
- Browsers: chrome, firefox, safari, edge
- Viewports: 1920, 1366, 360 (full page screenshots by default)
- Optional: `waitForPageRender` and `waitForTimeout` for slow-loading pages

## View Results

After running the tests, visit your SmartUI project dashboard to view the captured screenshots and compare them with baseline builds.

## More Information

For detailed onboarding instructions, see the [SmartUI Cypress Onboarding Guide](https://www.lambdatest.com/support/docs/smartui-onboarding-cypress/).
