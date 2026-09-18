# Power BI Practice — Financials Sample Dataset

Practice dashboards and reports built in Power BI Desktop using Microsoft's built-in **Financials** sample dataset. The dataset contains one `financials` table with fields including `Segment`, `Country`, `Product`, `Discount Band`, `Units Sold`, `Manufacturing Price`, `Sale Price`, `Gross Sales`, `Discounts`, `Sales`, `COGS`, `Profit`, and a `Date` hierarchy (Year, Month Name, Month Number).

## Projects

### 1. Financials Dashboard Practice — single-page executive summary

**Folder:** [`financials-dashboard-practice/`](financials-dashboard-practice/)

A one-page dashboard designed to answer "how's the business doing" at a glance, with drill-down via slicers.

| Screenshot | What it shows |
|---|---|
| `01-overview-unfiltered.png` | Full dataset view: KPI cards (Sum of Sales, Sum of Profit, Sum of Units Sold), a donut chart of Sum of Sales by Country and Product, a dual-line chart tracking Sum of Sales against %GT Average of Profit by month, a filled map of Sum of Sales by country, and a stacked bar chart of Average Profit by Segment and Discount Band |
| `02-overview-filtered-canada-amarilla.png` | The same dashboard after selecting Canada + Amarilla in the slicers, demonstrating cross-filtering: every visual on the page (cards, donut, map, line chart, stacked bar) updates in sync to reflect just that country/product combination |

**Skills demonstrated:**
- KPI card visuals for headline metrics
- Donut chart with two-level category breakdown (Country → Product)
- Dual-measure line chart combining an absolute value (Sales) with a percentage growth trend (%GT Average of Profit)
- Filled map visual using geographic data
- Stacked bar chart with two grouping dimensions (Segment × Discount Band)
- Cross-highlighting/filtering: slicers on Country and Product driving every visual on the page simultaneously

---

### 2. Practice BI — multi-page report (11 pages)

**Folder:** [`practice-bi-multipage-report/`](practice-bi-multipage-report/)

A more extensive practice report covering a wider range of visual types across dedicated pages (`Bar_Chart`, `Pie_Chart`, `Cards_Aggregations`, `Filter_Slicer`, `Map`, `Filled Map`, `Decomposition_Tree`, `Buttons`, `Table&Matrix`, `Stacked Bar Chart`, and an `Exercise_Bookmark_Navigator` landing page). Screenshots below cover three of these pages.

| Screenshot | What it shows |
|---|---|
| `01-stacked-bar-chart-with-dynamic-narrative.png` | Stacked bar chart of Sum of Profit by Product and Country, paired with a dynamic text callout ("Paseo in Country Canada made up 7.49% of Sum of Profit") that updates based on the selected bar, alongside a supporting map and Country/Product slicers |
| `02-pie-charts-multi-measure.png` | Six pie charts side by side, each slicing a different measure by a different dimension: Average Sales by Product, %GT Average of Discounts by Segment, Average Profit by Country, Sum of Sales by Product, Count of Units Sold by Segment, and Sum of Sales by Country |
| `03-cards-and-kpi-aggregations.png` | A grid of card visuals showing multiple aggregation types (count, average, sum) sliced by different dimensions: Count of Units Sold by Segment, Average Discounts, Average Gross Sales, and Sum of Sales broken out by Discount Band (High/Low/Medium), with Country and Month slicers |

**Skills demonstrated:**
- Multi-page report structure with a bookmark-based navigation landing page
- Pie chart visuals across multiple measures and dimensions
- Card visuals for quick-read aggregations (count, sum, average) sliced by category
- Dynamic/interactive text callouts that respond to visual selection (likely built with a DAX measure using `SELECTEDVALUE`)
- Filter and slicer panels scoped per page
- Report organization across dedicated pages by visual type, useful for a portfolio/reference structure

## Notes to self

- The dynamic callout text in the stacked bar chart page is worth documenting in more detail later, it's a good example of combining a DAX measure with `SELECTEDVALUE()` (or similar) to build a sentence that updates with user selection, rather than a static title.
- Worth adding screenshots of the remaining pages (`Filter_Slicer`, `Map`, `Filled Map`, `Decomposition_Tree`, `Buttons`, `Table&Matrix`) to fully document the 11-page report.
