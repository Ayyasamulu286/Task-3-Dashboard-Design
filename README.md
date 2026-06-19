# Task 3 — Dashboard Design: Superstore Sales & Profit

An end-to-end retail analytics deliverable built on the classic Superstore dataset — covering sales, profit, discount and shipping performance across 9,994 order lines (2014–2017).

## Folder structure

```
Task-3-Dashboard-Design/
├── dataset/
│   └── SampleSuperstore.csv        # Cleaned source data (9,994 rows × 21 columns)
├── dashboard/
│   ├── Dashboard_Interactive.html  # Self-contained interactive dashboard (open in any browser)
│   └── PowerBI_Build_Guide.md      # Step-by-step guide to rebuild this dashboard as Dashboard.pbix
├── ppt/
│   └── Task3_Summary.pptx          # 8-slide executive summary deck, native editable charts
├── screenshots/
│   ├── dashboard.png               # Full capture of the interactive dashboard
│   ├── sales_trend.png             # Monthly sales & profit trend chart
│   └── insights.png                # 4-panel key insights summary
└── README.md
```

## A note on `Dashboard.pbix`

A native Power BI file can only be created and saved from inside Power BI Desktop — it isn't something that can be generated programmatically outside the application. In its place, this deliverable includes:

1. **`Dashboard_Interactive.html`** — a fully working, interactive equivalent you can open right now in any browser (no installs, no internet connection required — all charts are rendered in plain SVG).
2. **`PowerBI_Build_Guide.md`** — exact steps, DAX measures, and a matching color theme to rebuild the same dashboard natively as `Dashboard.pbix` in Power BI Desktop in about 15–20 minutes.

## Key numbers

| Metric | Value |
|---|---|
| Total Sales | $2,297,201 |
| Total Profit | $286,397 |
| Profit Margin | 12.47% |
| Total Orders | 5,009 |
| Average Discount | 15.62% |

## Headline findings

- **Technology** is the strongest category — leads on both sales ($836K) and profit ($145K).
- **Furniture** generates almost as much revenue as Technology ($742K) but returns only $18K profit (2.5% margin), dragged down by Tables and Bookcases.
- **Tables (–$17.7K), Bookcases (–$3.5K) and Supplies (–$1.2K)** operate at a net loss across the dataset — candidates for discount caps or repricing.
- **West and East** regions deliver the best profit margins; **Central** trails at roughly 8%.
- **Consumer** is the largest customer segment (~50% of sales); **Standard Class** shipping accounts for 60% of all orders.
- Profit visibly erodes once discount rates climb above ~20%.

## How to view each deliverable

- **Interactive dashboard** — double-click `dashboard/Dashboard_Interactive.html`, or drag it into any browser tab.
- **Power BI version** — follow `dashboard/PowerBI_Build_Guide.md` inside Power BI Desktop.
- **Summary deck** — open `ppt/Task3_Summary.pptx` in PowerPoint; all charts are native and editable.
- **Raw data** — `dataset/SampleSuperstore.csv`, ready to load into Excel, Power BI, or pandas.

## Source

Built from `Superstore_Cleaned.xlsx`, the standard Superstore retail dataset (Order Date range: Jan 2014 – Dec 2017).
