# UI lab results

Selected tools:
- Robot Framework
- Cypress

## Part 0
- Step 0.1, Chrome version: 157.0.8103.79
- Step 0.3, ChromeDriver version: 157.0.8103.79
- Step 0.4: Locators

| Element | CSS Locator |
|---|---|
| Pizza, Please! | [name="pizza-please"] |
| Excluded tools | select |
| Must be vegetarian | #default-checkbox |
| Custom Pizza Name | input#pizza-name |

The ID floating_filled is not unique.
Therefore, XPath based on the field label
is used to locate the maximum calories input.
- Step 0.5, pizza name, tool and calories of the run by hand:
    - Pizza name: Lab Pizza 20261124-011121
    - Maximum calories per slice: 600
    - Excluded tool: Knife
    - Vegetarian: Yes
    - Admin username: admin
    - Admin password: admin

| Step | Action | Expected Result | Actual Result | Status |
|---|---|---|---|---|
| 1 | Open QuickPizza | Correct heading appears | The correct heading was displayed. | Pass |
| 2 | Turn on Advanced | Four advanced fields appear | All four fields were displayed. | Pass |
| 3 | Fill in the restrictions and name | Fields contain the specified values | All input values matched the test data. | Pass |
| 4 | Click Pizza, Please! | Correct name, tool other than Knife, and calories <= 600 | The pizza name and restrictions matched the expected results. | Pass |
| 5 | Click Love it! without logging in | Please log in first. | The login message was displayed. | Pass |
| 6 | Open /admin and sign in | Latest pizza recommendations appears | The recommendation list was displayed. | Pass |
| 7 | Find the pizza in the admin list | Same pizza name and tool | The pizza name and tool matched the recommendation. | Pass |

## Part 3: Robot Framework

### Step 3.1: Installation

Robot Framework and SeleniumLibrary were installed
successfully in a Python virtual environment.

### Step 3.2: First Test

| Run | Expected Title | Result |
|---|---|---|
| 1 | Web form | Pass |
| 2 | Web Form | Fail |
| 3 | Web form | Pass |

**Failure message:**

Title should have been 'Web Form' but was 'Web form'.

**Explanation:**

The test failed because the expected title did not
match the actual page title. After correcting the
expected title, the test passed again.

### Step 3.3: Web Form Testing

**Test:** Every Kind Of Field

The automated test filled in text fields, password,
textarea, dropdown, checkbox, radio button, and date.

The form was submitted successfully, and the page
displayed the expected message "Received!".

**Result:** Pass

### Step 3.4: Resource File

A resource file was created to store reusable keywords
and locators for the QuickPizza website.

The test successfully opened the home page and verified
the expected heading.

**Result:** Pass

### Step 3.5: Advanced Fields

The test opened the Advanced section and verified that
all four required fields were visible.

The maximum calories, excluded tool, vegetarian option,
and unique pizza name were entered and verified.

**Result:** Pass

### Step 3.6: Pizza Recommendation

The automated test verified that:

- The recommended pizza name matched the input.
- The recommended tool was not Knife.
- The calories per slice did not exceed 600.

**Result:** Pass

### Step 3.7: Rating and Admin List

The test verified that rating a pizza without logging
in displayed the message "Please log in first."

The administrator successfully signed in and found
the newly created pizza with the same recommended tool.

**Result:** Pass

### Step 3.8: Evidence from Two Full Runs

| Run | Pizza Name | Elapsed Time | Recommended Tool | Calories per Slice | Result |
|---|---|---|---|---|---|
| Run 1 | Lab Pizza 20261125-014335 | 18.774 s | Pizza cutter | 400 | Pass |
| Run 2 | Lab Pizza 20261125-014411 | 17.080 s | Pizza cutter | 425 | Pass |

Both runs used unique pizza names to prevent conflicts
with data from previous runs.

#### Test Summary

| Metric | Run 1 | Run 2 |
|---|---|---|
| Total tests | 1 | 1 |
| Passed | 1 | 1 |
| Failed | 0 | 0 |
| Screenshots captured | 4 | 4 |

#### Evidence

**Run 1**

- [Report](robot/results/run1/report.html)
- [Execution Log](robot/results/run1/log.html)
- [XML Output](robot/results/run1/output.xml)
- [Step 3 - Advanced Fields](robot/results/run1/qp01-step3-fields.png)
- [Step 4 - Pizza Recommendation](robot/results/run1/qp01-step4-pizza.png)
- [Step 5 - Login Required](robot/results/run1/qp01-step5-login-needed.png)
- [Step 7 - Admin List](robot/results/run1/qp01-step7-admin-list.png)

**Run 2**

- [Report](robot/results/run2/report.html)
- [Execution Log](robot/results/run2/log.html)
- [XML Output](robot/results/run2/output.xml)
- [Step 3 - Advanced Fields](robot/results/run2/qp01-step3-fields.png)
- [Step 4 - Pizza Recommendation](robot/results/run2/qp01-step4-pizza.png)
- [Step 5 - Login Required](robot/results/run2/qp01-step5-login-needed.png)
- [Step 7 - Admin List](robot/results/run2/qp01-step7-admin-list.png)

#### Overall Result

The QP-01 test scenario passed in two consecutive runs.
Both recommendations satisfied the specified restrictions.
The use of reusable keywords, explicit waits, and unique
pizza names helped make the automated test reliable
and repeatable.

**Overall Result: PASS**

## Part 4: Cypress

### Step 4.1: Installation

The following tools were installed and used:

- Cypress version: 16.2.1
- Node.js version: 22.14.0
- Browser: Chrome 157

**Result:** Pass

### Step 4.2: Project Configuration

The Cypress project was configured for end-to-end
testing using JavaScript.

Two test specifications were created:

- `web-form.cy.js`
- `pizza-scenario.cy.js`

**Result:** Pass

### Step 4.3: Web Form Testing

The automated test filled in the required fields,
submitted the form, and verified the expected result.

#### Intentional Failure

The expected page title was intentionally changed
from "Web form" to "Web Form".

**Failure message:**

    Timed out retrying after 10000ms
    + expected - actual

    -'Web form'
    +'Web Form'

The test failed because the expected title did not
match the actual page title. After correcting the
expected title, the test passed in both full runs.

**Result:** Pass

### Step 4.4: QuickPizza Homepage and Advanced Fields

The test opened QuickPizza, verified the homepage
heading, enabled the Advanced section, and checked
the required input fields.

The test generated a unique pizza name using the
current date and time.

**Result:** Pass

### Step 4.5: Pizza Recommendation and Rating

The automated test verified that:

- The recommended pizza name matched the input.
- The recommended tool was not Knife.
- The calories per slice did not exceed 600.
- Rating without authentication displayed
  "Please log in first."

**Result:** Pass

### Step 4.6: Network Request Verification

Cypress network interception was used to inspect
the pizza recommendation request and response.

The test checked the API response and compared
the returned recommendation with the information
displayed on the user interface.

**Result:** Pass

### Step 4.7: Admin Login and Custom Command

A reusable custom command, `adminLogin`, was used
to perform administrator authentication.

#### Issue Encountered

During an earlier execution, the test failed at
QP-01 step 7 because the expected pizza name could
not be found in the admin list within 10 seconds.

**Failure message:**

    Timed out retrying after 10000ms:
    Expected to find content:
    'Lab Pizza 20261125-022305'
    within the selector: 'li' but never did.

A longer timeout was suggested for the admin list
verification. The exact cause of the initial
failure was not confirmed.

Both subsequent full runs passed successfully,
including the admin list verification.

**Result:** Pass

### Step 4.8: Evidence from Two Full Runs

Both test specifications were executed twice
using Chrome in headless mode.

#### Execution Results

| Metric | Run 1 | Run 2 |
|---|---|---|
| Browser | Chrome 157 | Chrome 157 |
| Total tests | 2 | 2 |
| Passing | 2 | 2 |
| Failing | 0 | 0 |
| QP-01 duration | 9 s | 9 s |
| Web form duration | 6 s | 2 s |
| Total duration | 16 s | 12 s |
| Screenshots | 3 | 3 |
| Videos | 2 | 2 |
| Overall result | Pass | Pass |

#### Pizza Recommendation Results

| Run | Pizza Name | Recommended Tool | Calories per Slice |
|---|---|---|---|
| Run 1 | Lab Pizza 20261125-024403 | Pizza cutter | 475 |
| Run 2 | Lab Pizza 20261125-024542 | Pizza cutter | 325 |

Both recommendations satisfied the specified
restrictions. Each run generated a unique pizza
name to avoid conflicts with previous test data.

#### Run 1 Evidence

- [Step 4 - Pizza Recommendation](cypress/results/run1/screenshots/pizza-scenario.cy.js/qp01-step4-recommendation.png)
- [Step 5 - Login Required](cypress/results/run1/screenshots/pizza-scenario.cy.js/qp01-step5-login-needed.png)
- [Step 7 - Admin List](cypress/results/run1/screenshots/pizza-scenario.cy.js/qp01-step7-admin-list.png)
- [QP-01 Test Video](cypress/results/run1/videos/pizza-scenario.cy.js.mp4)
- [Web Form Test Video](cypress/results/run1/videos/web-form.cy.js.mp4)

#### Run 2 Evidence

- [Step 4 - Pizza Recommendation](cypress/results/run2/screenshots/pizza-scenario.cy.js/qp01-step4-recommendation.png)
- [Step 5 - Login Required](cypress/results/run2/screenshots/pizza-scenario.cy.js/qp01-step5-login-needed.png)
- [Step 7 - Admin List](cypress/results/run2/screenshots/pizza-scenario.cy.js/qp01-step7-admin-list.png)
- [QP-01 Test Video](cypress/results/run2/videos/pizza-scenario.cy.js.mp4)
- [Web Form Test Video](cypress/results/run2/videos/web-form.cy.js.mp4)

#### Overall Result

Both test specifications passed in two consecutive
full runs, with no failed or skipped tests.

Cypress automatic retries, network interception,
reusable custom commands, and unique test data
supported reliable and repeatable UI testing.

**Overall Result: PASS**

### Step 4.9: Cross-Browser Testing (Optional)

Not performed.

## Part B
## Part B: Reflection

### 1. Locating Max Calories per Slice

The tests locate the Max Calories per Slice field
through its label because the ID `floating_filled`
is shared by three input elements. Using this ID
alone could select the wrong field. I would assign
a unique ID, such as `max-calories`, to the input.
This would make the locator more reliable, readable,
and easier to maintain.

### 2. Test Oracle

The comparison between the recommended tool and the
tool in the admin list is a consistency test oracle.
It checks whether two parts of the same system
display consistent information. For example, it
would detect a fault where the recommendation shows
Pizza cutter but the admin list records Knife.
Both automated tests included this comparison.

### 3. Vegetarian Verification

Checking the vegetarian checkbox only confirms that
the input was selected, not that the resulting pizza
is vegetarian. I would add an assertion to verify
that every ingredient in the recommendation is
vegetarian. The test would need the ingredient list
from the page and a reliable source that identifies
which ingredients are vegetarian.

### 4. Tool Comparison

Robot Framework uses explicit wait keywords, such as
`Wait Until Element Contains`, while Cypress
automatically retries queries and assertions.
I found Robot Framework easier to write initially
because its keywords were similar to plain English.
However, Cypress required less explicit waiting code.
Robot Framework provided detailed HTML logs, while
Cypress provided screenshots and videos that made
the execution easier to observe. During my Cypress
testing, the admin list assertion initially failed
because the pizza name was not found within 10 seconds.

### 5. Tool Selection for Project 2

I would choose Cypress for Project 2. Its automatic
retry mechanism reduces the need to write explicit
waits for dynamic web pages. It also provides video
recordings and screenshots, which are useful for
debugging and demonstrating test results. Both of
my final Cypress runs passed all tests successfully.

### 6. Robot Framework Resource File

If QuickPizza changes the locator of the calories
field, I would update the `${MAX CALORIES}` variable
in `resources/quickpizza.resource`. The keywords
that use this variable would automatically use the
updated locator. The `pizza_scenario.robot` test
file would not need to change. This separation
reduces duplicated code and makes maintenance easier.

### 7. Cypress Test Isolation

QP-01 must remain a single Cypress test because
Cypress clears cookies before each test. QuickPizza
uses cookies to maintain the browser's connection
to the same server. If the admin login and
verification were placed in a separate test, the
browser could connect to a different server and
fail to find the pizza created earlier. Keeping all
seven steps together preserves the required session.