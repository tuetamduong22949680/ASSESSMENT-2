# ASSESSMENT 2
# Smart Savings & Spending Planner

## Overview

The Smart Savings & Spending Planner is a personal finance assistant created for ISYS2001 Introduction to Business Programming.

The application helps users organise their income, expenses and saving goals into a weekly financial plan.

Users can describe their financial information using natural language. Gemini extracts the information, while Python performs the financial calculations so that the results are based on verified user data.

## Main Features

- Create a simple personal profile
- Extract income, expenses and saving goals using Gemini
- Convert different payment frequencies into weekly amounts
- Calculate weekly income and expenses
- Calculate money available for saving goals
- Manage multiple saving goals with priorities and deadlines
- Identify whether a saving plan is achievable
- Suggest optional expense reductions or deadline adjustments
- Add transactions manually or upload a CSV
- Compare planned and actual weekly spending
- Display a Planned vs Actual spending chart
- Generate a weekly spending summary
- Ask an AI finance assistant questions about the current plan
- Save and reload progress using JSON

## Example Input

### Income

I earn 900 dollars every week from my part-time job.
My partner earns 700 dollars per week but only contributes
300 dollars per week toward our shared budget.

### Expenses

Our rent is 520 dollars per week.
I spend around 180 dollars per week on groceries,
70 dollars per week on petrol and 25 dollars per week
on gym membership.

My phone bill is 60 dollars per month.
I spend around 90 dollars per week eating out and
30 dollars per month on streaming subscriptions.

### Saving Goal

I want to save 3000 dollars for a Vietnam trip by
2026-12-20.

I have already saved 500 dollars and this goal
is a Must have.

## Example Output

Using the example input above and a weekly safety buffer of $50, the planner produces results such as:

- Usable weekly income: $1,200.00
- Total weekly expenses: $905.77
- Weekly safety buffer: $50.00
- Money available for saving goals: $244.23
- Minimum weekly saving required for the goals: $354.24
- Weekly shortfall: $110.01
- Plan status: Not achievable

The planner then suggests possible changes such as reducing optional spending or adjusting a lower-priority goal deadline.

The user can also track actual transactions, compare planned and actual spending, and view the results in a bar chart.

## How to Run

1. Open the Colab notebook.
2. Add a Gemini API key to Colab Secrets using the name:

   `GEMINI_API_KEY`

3. Allow notebook access to the secret.
4. Run the notebook cells from top to bottom.
5. Open the Gradio link created by the final cell.
6. Enter profile, income, expense and saving goal information.
7. Create the financial plan and use the tracking and assistant features.

## Transaction CSV Format

CSV transaction files should contain:

```text
Date,Category,Amount,Description
2026-10-13,Groceries,120,Weekly grocery shopping
2026-10-14,Petrol,60,Fuel refill
