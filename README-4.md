# Financial Planning & Business Analysis Dashboard

An Excel-based financial planning model for a fictional Indian FMCG distribution business, built around budgeting, actual-vs-budget variance analysis, profit planning, forecasting and scenario planning.

## Business Problem

Small distribution businesses typically track sales and expenses, but rarely build a proper planning layer on top of that data: a budget to measure against, a clear view of where and why performance deviated from plan, a break-even point, and a simple way to test "what if" questions before making decisions. This project builds that planning layer.

## Objective

The model is built to answer the questions a small business owner or manager actually asks at month-end and at planning time:

- What did we budget for revenue and expenses, and how did we actually perform?
- Where are the biggest favourable and unfavourable variances, and what is driving them?
- What is our break-even point, and how much safety margin do we have above it?
- What revenue do we need to hit a target profit?
- What does the next two quarters look like on current trends?
- How does profit change under a conservative, base-case or optimistic scenario?

## Business Scenario

**Nandini FoodWorks** is a fictional small FMCG distribution business based in India, selling four product categories through a distributor network: Packaged Snacks, Beverages, Dairy Products and Bakery Items. Revenue is built up from monthly sales volume and average selling price per category. Costs are split between Cost of Goods Sold (COGS, which varies by category) and nine operating expense lines, each classified as Fixed or Variable. All figures are in Indian Rupees (Rs.) and follow an April-March financial year.

## Dataset Overview

| Dataset | Coverage | Rows |
|---|---|---|
| Historical Actual & Budget Revenue | Apr-24 to Mar-25, 4 categories | 48 |
| Historical Actual & Budget Expense | Apr-24 to Mar-25, 9 categories | 108 |
| Forecast Revenue | Apr-25 to Sep-25, 4 categories | 24 |
| Forecast Expense | Apr-25 to Sep-25, 9 categories | 54 |

The data was generated to follow realistic, logically consistent patterns rather than random numbers: festive-season demand spikes in October-November, a monsoon-linked dip in July-August (lower dispatch volumes and higher input costs for perishable categories), and a post-festive slowdown in January. These patterns are what the Variance Analysis and Business Analysis sections actually pick up and explain.

## Key Features

- **Executive Dashboard** with 12 KPI cards and 8 charts covering revenue, expenses, profit, variance and forecast trends
- **Revenue Planning** by month and category, with budget/actual volume, price and COGS
- **Expense Budget** across 9 categories, classified Fixed/Variable, with variance status
- **Budget vs Actual** monthly roll-up for revenue, expense and net profit
- **Variance Analysis** that decomposes revenue variance into volume and price effects, and flags the likely driver of each month's profit variance
- **Profit Planning** using a contribution-margin model (Revenue - Variable Costs = Contribution - Fixed Costs = Net Profit)
- **Financial Forecast** for the next 6 months using a transparent trend-based method
- **Scenario Analysis** with three editable what-if scenarios (Conservative / Base / Optimistic)
- **Break-Even Analysis** with blended contribution margin, break-even revenue and break-even volume
- **Target Profit Analysis** that calculates the revenue required to hit a management profit target
- **Financial KPIs** consolidating growth, margin and efficiency metrics
- **Business Analysis** with recommendations grounded directly in the computed figures

## Tools & Technologies

- Microsoft Excel (formulas: SUMIF, SUMIFS, SUMPRODUCT, INDEX/MATCH, IFERROR, nested IF)
- Excel Tables with AutoFilter for filtering by month, quarter and category
- Native Excel charts (bar, line, pie)

## Financial Planning Methodology

**Budget vs Actual method:** Budget figures are treated as the plan set at the start of FY 2024-25; Actual figures are the recorded outcome. Variance = Actual - Budget for revenue and profit; for expenses the same variance is read in reverse, since an expense coming in above budget is a cost overrun, not a gain.

**Variance Analysis:** Total revenue variance for each month is split into a Volume Variance (the effect of selling more or fewer units than budgeted, priced at the budgeted rate) and a Price Variance (the effect of the actual selling price differing from budget, applied to actual volume). This is a standard sales variance decomposition and is shown as an approximation, since a small joint volume-price interaction term is not separately broken out.

**Forecasting method:** Each revenue and expense line is forecast using its own average month-on-month growth rate calculated from the 12 months of FY 2024-25 actuals, capped to a realistic range and then applied forward from the March 2025 actual base. COGS is forecast using each category's average actual COGS-to-revenue ratio. This is a deliberately simple, transparent method rather than a black-box model - see the Financial Forecast sheet for the full assumptions and limitations.

**Scenario Analysis:** Each of the three scenarios (Conservative, Base Case, Optimistic) has independent, editable assumptions for volume change %, selling price change % and expense growth %. Revenue growth is derived as `(1 + Volume%) x (1 + Price%) - 1` and applied to the FY 2024-25 actual base; the outputs (projected revenue, cost, profit and margin) recalculate live when any assumption is changed.

**Break-Even Analysis:** Uses the FY 2024-25 blended actual contribution margin ratio and fixed costs. Break-even volume additionally uses a blended average selling price and average variable cost per unit across all four categories, since the business sells a product mix rather than a single product - this is stated as an explicit assumption on the sheet.

## KPI Definitions

| KPI | Formula |
|---|---|
| Revenue Growth % | 2nd-half FY actual revenue vs 1st-half FY actual revenue |
| Gross Profit Margin % | (Revenue - COGS) / Revenue |
| Net Profit Margin % | Net Profit / Revenue |
| Expense Ratio % | Total Expense (incl. COGS) / Revenue |
| Budget Achievement % | Actual Revenue / Budget Revenue |
| Forecast Growth % | Forecast Revenue (Apr-Sep 25) vs Actual Revenue (Apr-Sep 24), same period |
| Contribution Margin % | Contribution / Revenue |
| Break-Even Revenue | Fixed Costs / Contribution Margin Ratio |
| Target Profit Gap | Required Revenue (for target profit) - Current Revenue |

## Key Business Insights

- FY 2024-25 Actual Revenue closed at Rs. 3.56 crore against a Budget of Rs. 3.57 crore (-0.35%) - close to target for the year as a whole, but the monthly pattern varies significantly.
- October and November (festive season) were the strongest months, with Actual Profit beating Budget by +18% and +13% - increased festive marketing spend paid for itself in volume.
- January 2025 was the weakest month (Actual Profit -37% vs Budget), consistent with a post-festive demand slowdown.
- July and August (monsoon season) were also unfavourable, driven by lower dispatch volumes and a rise in the input-cost ratio for Dairy and Bakery products.
- Beverages was the weakest-performing revenue category for the year (-1.9% vs budget); Dairy Products was the strongest (+0.5%).
- Total operating expenses ran only 0.6% over budget for the year - overall cost control was solid, with the festive-period Marketing overspend being the one deliberate, revenue-linked exception.
- Dairy Products carries the lowest gross margin of the four categories (~31%, versus 38-43% for the others), which pulls down the blended contribution margin used in the Break-Even and Target Profit models.

## Business Recommendations

1. Build a monsoon contingency into the July-August budget for Beverages and Bakery Items, based on this year's actual shortfall pattern, rather than assuming flat performance.
2. Treat the October-November festive marketing increase as a repeatable, budgeted play for FY 2025-26 given its proven payback this year.
3. Investigate the January shortfall further before finalising the FY 2025-26 budget - if it is a recurring post-festive pattern, budget for it explicitly.
4. Review Dairy Products input sourcing or pricing, since its lower gross margin dilutes the overall contribution margin ratio.

## Limitations

- This is a planning and analysis model built on realistic fictional data, not a live accounting system - it does not post journal entries or reconcile to a general ledger.
- The forecast uses a simple trend/average-growth method by design; it will not capture unmodelled demand shocks or one-off events.
- The model assumes no separate interest or tax expense, so Net Profit and Operating Profit are the same figure throughout.
- Break-even and target-profit figures are blended across four product categories and assume a stable product mix.

## How to Use / View the Project

1. Open `Excel/Financial_Planning_Business_Analysis.xlsx` in Microsoft Excel.
2. Start on the **Dashboard** sheet for the executive summary, then move through the sheet tabs in order for the underlying detail.
3. Use the filter dropdowns on the **Revenue Planning** and **Expense Budget** sheets to slice by month, quarter or category.
4. On the **Scenario Analysis** and **Target Profit Analysis** sheets, edit the yellow input cells to see the model recalculate live.
5. Raw source data is available separately under `Data/` as CSV files.

## Project Structure

```
financial-planning-business-analysis/
├── README.md
├── Excel/
│   └── Financial_Planning_Business_Analysis.xlsx
├── Data/
│   ├── Historical_Actual_and_Budget_Revenue.csv
│   ├── Historical_Actual_and_Budget_Expense.csv
│   ├── Forecast_Revenue_Apr25_Sep25.csv
│   └── Forecast_Expense_Apr25_Sep25.csv
└── Screenshots/
    ├── 01_dashboard_kpi_cards.png
    ├── 02_dashboard_revenue_expense_charts.png
    └── 03_dashboard_category_charts.png
```
