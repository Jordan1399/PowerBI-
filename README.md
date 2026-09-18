# Power BI Practice

Practice dashboards, reports, and data models built in Power BI Desktop. Includes work on Microsoft's built-in **Financials** sample dataset (single flat table) and the public **Brazilian Olist E-Commerce** dataset (nine related raw tables, requiring actual data modeling).

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
| `04-decomposition-tree-with-multiline-chart.png` | A decomposition tree breaking Sum of Profit down interactively across Country → Product → Date, paired with a multi-line chart tracking Sum of Profit by Quarter for each of the six products |
| `05-buttons-bookmark-navigation.png` | Three pie charts (Sum of Sales, Sum of Profit, Average of Profit, all by Product) alongside a row of custom bookmark buttons (`Sum(Sales)`, `Average Profit by Product`, `Total Profit by Product`, `Full View Reset`, `Sum Sales by Country`) that swap the report view on click |
| `06-bubble-map-multi-measure-tooltip.png` | A bubble map plotting Sum of Sales (bubble size) by Country, with a custom tooltip on hover showing Sum of Sales, Sum of Gross Sales, Sum of Units Sold, and Max of Profit for the selected country in one combined view |
| `07-filled-map-conditional-formatting-setup.png` + `08-filled-map-country-profit-sales-tooltip.png` | The **Filled Map** page, shown as a pair: `07` is the conditional formatting setup, a three-point gradient (red → orange → green) applied to Sum of Profit to color each country; `08` is the resulting choropleth map with a custom tooltip (Country, Sum of Profit, Average of Sales) shown on hover over Canada |
| `09-stacked-bar-chart-country-segment.png` | The **Stacked Bar Chart** page: a horizontal stacked bar chart of Sum of Profit by Country, broken into five colored segments (Channel Partners, Enterprise, Government, Midmarket, Small Business) per country |
| `10-filter-slicer-multi-visual-page.png` | The **Filter_Slicer** page: a compact multi-visual layout (pie chart, donut chart, column chart, line chart, and cards) all scoped to a Country slicer, with the Year field's drill-through configuration panel open, showing how a field is set to "Used as category" so it can drive a separate drill-through detail page |

**Skills demonstrated:**
- Multi-page report structure with a bookmark-based navigation landing page
- Pie chart visuals across multiple measures and dimensions
- Card visuals for quick-read aggregations (count, sum, average) sliced by category
- Dynamic/interactive text callouts that respond to visual selection (likely built with a DAX measure using `SELECTEDVALUE`)
- Decomposition tree for ad-hoc, user-driven breakdown of a measure across multiple dimensions
- Bookmarks + button navigation to let a viewer swap between saved report states without needing filters
- Bubble map with a custom multi-field tooltip, packing four measures into a single hover interaction
- Filled map (choropleth) with custom three-point gradient conditional formatting, plus a configured tooltip
- Stacked bar chart with a categorical legend (Segment) broken out per country
- Configuring a field's drill-through behavior so a slicer page can route to a dedicated detail page
- Filter and slicer panels scoped per page
- Report organization across dedicated pages by visual type, useful for a portfolio/reference structure

---

### 3. Brazilian Olist E-Commerce — data modeling & drill-down practice

**Folder:** [`brazilian-olist-ecommerce-model/`](brazilian-olist-ecommerce-model/)

Unlike the Financials projects above (a single flat table), this project works from the public **Olist Brazilian E-Commerce** dataset, nine separate raw tables (`olist_customers_dataset`, `olist_geolocation_dataset`, `olist_order_items_dataset`, `olist_order_payments_dataset`, `olist_order_reviews_dataset`, `olist_orders_dataset`, `olist_products_dataset`, `olist_sellers_dataset`, `product_category_name_translation`) that have to be related to each other before any visual can be built. This is data modeling practice, not just chart-building.

| Screenshot | What it shows |
|---|---|
| `01-relationship-editor-reviews-to-orders.png` | The relationship editor connecting `olist_order_reviews_dataset` to `olist_orders_dataset` on `order_id`, set to a Many-to-one (`*:1`) cardinality with cross-filter direction set to Both and the relationship marked active |
| `02-full-data-model-diagram.png` | The full model view showing how all the tables connect: reviews → orders → customers, orders → payments, and order items bridging orders → products, each relationship labeled with its cardinality (1 / \*) |
| `03-drill-down-review-score-by-month.png` | A line chart of Average review_score by Month (filtered to 2017), with the drill menu open showing Drill up / Drill down options and a tooltip for April (4.04) |
| `04-drill-up-review-score-by-quarter.png` | The same measure one level up the date hierarchy, Average review_score by Quarter, with a tooltip for Qtr 3 (4.20) |
| `05-drill-up-review-score-by-year.png` | The same measure at the top of the hierarchy, Average review_score by Year, with a tooltip for 2017 (4.11) |

**Skills demonstrated:**
- Building relationships between raw, un-joined tables: selecting the correct key column on each side, setting cardinality (many-to-one), and choosing a cross-filter direction
- Reading and reasoning about a full data model diagram, tracing how a fact table (orders) connects out to multiple dimension and bridge tables
- Using a built-in date hierarchy (Year → Quarter → Month → Day) with drill up/drill down to move fluidly between levels of time granularity on the same visual, rather than building a separate chart per granularity
- Interpreting a trend across drill levels: review satisfaction dipped mid-2017 (visible at the month level) before settling, useful for practicing how to read a metric at different resolutions without losing the underlying story

## Notes to self

- The dynamic callout text in the stacked bar chart page is worth documenting in more detail later, it's a good example of combining a DAX measure with `SELECTEDVALUE()` (or similar) to build a sentence that updates with user selection, rather than a static title.
- The Buttons page is a good one to walk through in an interview: bookmarks capture a specific state of the report (which visual is visible, which filters are applied) and buttons trigger a jump to that saved state, this is different from a slicer, which filters data rather than swapping the whole view.
- The Filled Map's conditional formatting is worth remembering as a talking point: a three-point gradient (min/center/max) gives more nuance than a simple two-color scale, useful when values cluster around a midpoint rather than spreading evenly.
- Only `Table&Matrix` is left undocumented out of the 11 report pages.
- The Olist model is the strongest single piece for demonstrating real data modeling skill, since the Financials dataset comes pre-flattened as one table. Worth leading with the Olist project if asked to walk through one example in an interview.
- Many-to-one relationships in Power BI always point from the "many" side (the fact table, like reviews or order items) to the "one" side (the dimension table, like orders); getting this backwards is a common beginner mistake worth double-checking on each relationship.
