# Methodology

## Analytical scope

The project evaluates sales and gross profitability for a synthetic Lagos eatery from 1 January to 31 August 2026. The unit of analysis is a transaction line representing the sale of one menu item in a recorded order.

## Data architecture

The raw sales file contains operational fields that could reasonably be captured by a point-of-sale system. The processed file retains those fields and adds calculated revenue, cost, and gross-profit columns. Menu prices and unit costs are maintained in a separate assumptions file and workbook sheet.

```text
Menu and cost assumptions + Raw transaction data
                     ↓
        Calculated transaction metrics
                     ↓
         Monthly and dish summaries
                     ↓
           Excel management dashboard
```

## Data-generation approach

The sample was generated with a fixed random seed so the same inputs reproduce the same records. Plausible weights were applied to menu demand, meal periods, order channels, and payment methods. The model intentionally assigns greater demand to major rice dishes to create a realistic small-eatery case for analysis.

Because this is synthetic data, apparent relationships are scenario properties rather than evidence about the broader Lagos restaurant market.

## Preparation steps

1. Generated unique order identifiers and reusable customer identifiers.
2. Restricted transaction dates to January–August 2026.
3. Standardized item codes, dish names, categories, channels, payment methods, and meal periods.
4. Stored quantities, prices, costs, discounts, hours, and ratings as numeric values.
5. Retained blank feedback values rather than replacing them with zero.
6. Calculated transaction-level revenue, total cost, and gross profit.
7. Loaded the records into a filterable Excel table.

## Metric definitions

| Metric | Definition |
|---|---|
| Revenue | Quantity × Unit Price × (1 − Discount Rate) |
| Total Cost | Quantity × Unit Cost |
| Gross Profit | Revenue − Total Cost |
| Gross Margin | Gross Profit ÷ Revenue |
| Orders | Count of recorded transaction lines in this sample |
| Quantity Sold | Sum of item quantities |
| Average Order Value | Total Revenue ÷ Orders |
| Unique Customers | Distinct customer identifiers |
| Average Rating | Arithmetic mean of nonblank submitted ratings |
| Revenue Share | Dish Revenue ÷ Total Revenue |

## Hypothesis-evaluation rules

- H1 is supported if Rice Meals produce the largest category revenue.
- H2 is supported if Jollof Rice and Chicken ranks first by dish revenue.
- H3 is supported if overall gross margin is at least 45%.
- H4 is supported only if monthly revenue increases consistently across the complete period.
- H5 is supported if the average submitted rating is at least 4.0 out of 5.

The project uses descriptive comparisons rather than inferential statistical significance tests because the data is synthetic and represents the complete generated scenario rather than a probabilistic sample from a real business.

## Quality controls

- Bounded formula ranges prevent accidental inclusion of unrelated rows.
- Dashboard KPIs reconcile to the processed transaction table.
- Monthly revenue totals reconcile to overall revenue.
- Dish revenue totals reconcile to overall revenue.
- Revenue and cost calculations preserve numeric values rather than formatted text.
- Missing ratings remain blank and are excluded from averages.
- Workbook formulas were scanned for common spreadsheet errors.
- Each worksheet was rendered and visually reviewed.

## Interpretation boundaries

The analysis evaluates gross profitability only. It does not establish net profit, cash flow, or return on investment. Real deployment would require overhead costs, ingredient-level purchasing, wastage, taxes, refunds, delivery commissions, staffing, and operating-day data.

