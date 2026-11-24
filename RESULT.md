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

## Part 1: Selenium IDE
- Firefox version and Node.js version:
- Step 1.4, the line of the failed check and the line Tests:
- Step 1.5, target chosen for Submit, and why the recorded one was fragile:
- Step 1.6, commands changed, added or deleted after recording:
- Step 1.6, the pizza names of run 1 and run 2:
- Step 1.6, the line Tests: of both runs:
- Step 1.7, one line of QP01customerTest.java that needs rewriting, and why:

## Part 4: Cypress
- node --version, npm --version and npx cypress version:
- Step 4.3, failure message for the wrong title:
- Step 4.6, tool and calories in the answer of POST /api/pizza:
- Step 4.7, the line of the admin list that shows your pizza:
- Step 4.8, run 1, result, duration and pizza name:
- Step 4.8, run 2, result, duration and pizza name:
- Step 4.9 (optional), browser and result:

## Part B
1.
2.
3.
4.
5.
6.
7.