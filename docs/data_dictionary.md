# Data dictionary

## `data/raw/eatery_sales_raw.csv`

| Field | Type | Description |
|---|---|---|
| Order ID | Text | Unique identifier assigned to each recorded transaction line. |
| Date | Date | Transaction date between January and August 2026. |
| Customer ID | Text | Reusable synthetic customer identifier. |
| Item Code | Text | Menu-item identifier linked to the assumptions table. |
| Dish | Text | Name of the purchased menu item. |
| Category | Text | Rice Meals, Traditional Meals, Swallow, Sides, or Beverages. |
| Quantity | Integer | Number of portions or units sold. |
| Unit Price (₦) | Currency | Listed selling price per item before discount. |
| Discount % | Decimal | Discount rate applied to the transaction line. |
| Unit Cost (₦) | Currency | Estimated direct cost per portion or unit. |
| Order Channel | Text | Walk-in, Takeaway, or Delivery. |
| Payment Method | Text | Cash, Transfer, or POS. |
| Meal Period | Text | Breakfast, Lunch, or Dinner. |
| Hour | Integer | Hour of day when the transaction occurred. |
| Rating | Integer/blank | Submitted satisfaction rating from 1 to 5; blank means no rating. |

## `data/processed/eatery_sales_processed.csv`

The processed file contains all raw fields plus:

| Field | Type | Description |
|---|---|---|
| Revenue (₦) | Currency | Quantity × Unit Price × (1 − Discount Rate). |
| Total Cost (₦) | Currency | Quantity × Unit Cost. |
| Gross Profit (₦) | Currency | Revenue − Total Cost. |

## `data/raw/menu_cost_assumptions.csv`

| Field | Type | Description |
|---|---|---|
| Item Code | Text | Unique menu-item identifier. |
| Dish | Text | Menu-item name. |
| Category | Text | Menu grouping. |
| Unit Price (₦) | Currency | Assumed selling price per item. |
| Unit Cost (₦) | Currency | Assumed direct cost per item. |
| Opening Stock (portions) | Integer | Illustrative opening quantity expressed as available portions. |

## Data-quality notes

- The data is synthetic and contains no real customer information.
- Blank ratings represent customers who did not submit feedback.
- One row represents one transaction line; therefore, the row count should not automatically be interpreted as distinct customer visits in a real multi-line order system.
- Currency values are nominal Nigerian naira and are not adjusted for inflation.

