# Building Dashboard.pbix in Power BI Desktop

This guide rebuilds the same dashboard shown in `Dashboard_Interactive.html` natively in Power BI, since `.pbix` files can only be created and saved inside Power BI Desktop itself.

## 1. Load the data

1. Open Power BI Desktop → **Get Data** → **Text/CSV**
2. Select `dataset/SampleSuperstore.csv`
3. Click **Transform Data** to open Power Query Editor

## 2. Clean and shape (Power Query)

- Confirm column types: `Order Date` / `Ship Date` → Date, `Sales` / `Profit` / `Discount` → Decimal Number, `Quantity` → Whole Number, `Postal Code` → Text (prevents thousands-separator formatting)
- Remove `Row_ID` if not needed for visuals (keep it if you want a row-count measure)
- Add a calculated column **Order Month** = `Date.StartOfMonth([Order Date])` for time-series visuals
- Click **Close & Apply**

## 3. Create a Date table (recommended)

`Model` view → **New Table**:
```
DateTable = CALENDAR(MIN(SampleSuperstore[Order Date]), MAX(SampleSuperstore[Order Date]))
```
Mark it as a Date Table (`Table tools` → **Mark as Date Table**), then relate `DateTable[Date]` → `SampleSuperstore[Order Date]` (one-to-many).

## 4. Core DAX measures

```DAX
Total Sales = SUM(SampleSuperstore[Sales])
Total Profit = SUM(SampleSuperstore[Profit])
Total Orders = DISTINCTCOUNT(SampleSuperstore[Order_ID])
Total Quantity = SUM(SampleSuperstore[Quantity])
Profit Margin % = DIVIDE([Total Profit], [Total Sales])
Avg Discount % = AVERAGE(SampleSuperstore[Discount])
```

## 5. Page layout (matches the HTML dashboard)

**Page 1 — Overview**
- 5 **Card** visuals across the top: Total Sales, Total Profit, Profit Margin %, Total Orders, Avg Discount %
- **Line chart**: `Order Month` (axis) vs `Total Sales` and `Total Profit` (values) — monthly trend
- **Donut chart**: `Category` (legend) vs `Total Sales` (values)
- **Clustered bar chart**: `Region` (axis) vs `Total Sales` and `Total Profit` (values)
- **Stacked bar chart**: `Segment` (axis) vs `Total Sales` (values)

**Page 2 — Product & Geography**
- **Bar chart**: `Sub_Category` (axis, sorted descending by Sales) vs `Total Sales`, with `Total Profit` as a secondary value/tooltip — conditional formatting on negative profit (red)
- **Table/Matrix**: Top 10 `State` by `Total Sales` (use a Top N filter)
- **Donut chart**: `Ship Mode` (legend) vs count of orders
- **Table**: Top 10 `Customer_Name` by `Total Sales`

## 6. Formatting to match the deliverable's visual identity

| Element | Value |
|---|---|
| Background | `#F7F4EE` (warm paper) |
| Primary text / bars | `#15202B` (ink navy) |
| Accent (profit / alerts) | `#C1572C` (rust) |
| Secondary accent | `#2F5D50` (moss green) |
| Tertiary accent | `#C79A3D` (gold) |
| Title font | Georgia / serif |
| Body font | Segoe UI / Helvetica Neue |

Apply via **View → Themes → Customize current theme**, pasting the hex values above into the theme's name/colors.

## 7. Slicers (optional, for interactivity)

Add slicers for `Region`, `Category`, and `Order Date` (between two dates) at the top of each page so reviewers can filter the whole dashboard.

## 8. Save as .pbix

**File → Save As** → `Dashboard.pbix`, store it in the `dashboard/` folder of this project.

## 9. Export screenshots for the `screenshots/` folder

**File → Export → Export to PDF**, then capture full-page screenshots of each page, or use **File → Export → Export to Image** per visual.
