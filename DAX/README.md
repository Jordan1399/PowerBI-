# DAX Practice Reference

These screenshots document DAX practice in Power BI using the `financials`, `menu_items`, and `carbon_footprint_by_product` tables. The formulas below are transcribed from the visible formula bars. Where a field is visible but its formula is not shown, the reference describes only what can be confirmed from the screenshot.

## Measures

### `SUM`

```DAX
Total_Revenue = sum(financials[Sales])
```

**Type:** Measure  
**Purpose:** Adds the `Sales` column and returns revenue in the current filter context. The accompanying card shows the result changing when the country slicer is used.

### `COUNTROWS`

```DAX
Total_Transactions/Rows = COUNTROWS(financials)
```

**Type:** Measure  
**Purpose:** Counts rows in `financials`, representing the number of transactions/records visible under the current filter context. The screenshot shows 140 in the card and also shows the same formula in the model.

### `DISTINCTCOUNT`

```DAX
Unique Products = DISTINCTCOUNT(carbon_footprint_by_product[Product])
```

**Type:** Measure  
**Purpose:** Counts distinct product values rather than every row. The accompanying card shows 10 unique products.

### `AVERAGE`

```DAX
Average Menu Item Value = AVERAGE(menu_items[price])
```

**Type:** Measure  
**Purpose:** Calculates the arithmetic mean of menu item prices. The accompanying card shows 13.25.

## Calculated columns

Calculated columns evaluate row by row when the table is refreshed. The screenshots show these examples using row-context arithmetic:

```DAX
UnitsSold x SP = financials[Units Sold] * financials[Sale Price]
```

Multiplies units sold by sale price for each row. This is a row-level sales-value calculation.

```DAX
Profit Less GrossSales = financials[Profit] - financials[Gross Sales]
```

Subtracts gross sales from profit for each row. The displayed results are negative because gross sales are much larger than profit; if the intended business metric was profit after costs, this formula may be a modeling or naming issue rather than a useful margin calculation.

```DAX
SP Less MP = financials[Sale Price] - financials[Manufacturing Price]
```

Subtracts manufacturing price from sale price for each row, producing the per-unit difference between those fields.

## Calculated tables with `FILTER`

```DAX
HighValue Profits = FILTER(financials, [Profit] > 150000)
```

**Type:** Calculated table  
**Purpose:** Returns rows from `financials` whose profit exceeds 150,000. The screenshot shows 16 resulting rows.

```DAX
HighValue Profits Canada = FILTER(financials, [Profit] > 150000 && [country] = "canada")
```

**Type:** Calculated table  
**Purpose:** Applies both a numeric threshold and a country condition, returning high-profit rows for Canada. The screenshot shows three rows. The formula uses lowercase `"canada"` while the source values display as `Canada`; DAX text comparisons are generally case-insensitive, but consistent casing is still clearer for maintainability.

## Date and month helper fields

The `financials` screenshots visibly include `Date`, `Month Number`, `Month Name`, and `Year` fields, and the calculated-column view shows values such as `12`, `December`, and `2014`. Their formula bars are not visible in the supplied images, so their exact DAX expressions are not reproduced here.

## Screenshot index

| Screenshot | Topic |
|---|---|
| [`01-total-revenue-measure.png`](01-total-revenue-measure.png) | `SUM` measure formula |
| [`02-total-revenue-card.png`](02-total-revenue-card.png) | Total revenue card and country slicer |
| [`03-total-transactions-card.png`](03-total-transactions-card.png) | Total transactions card |
| [`04-unique-products-measure.png`](04-unique-products-measure.png) | `DISTINCTCOUNT` measure formula |
| [`05-unique-products-card.png`](05-unique-products-card.png) | Unique products card |
| [`06-total-transactions-measure.png`](06-total-transactions-measure.png) | `COUNTROWS` measure formula |
| [`07-average-menu-item-measure.png`](07-average-menu-item-measure.png) | `AVERAGE` measure formula |
| [`08-average-menu-item-card.png`](08-average-menu-item-card.png) | Average menu item card |
| [`09-highvalue-profits-canada-table.png`](09-highvalue-profits-canada-table.png) | Numeric and country `FILTER` |
| [`10-units-sold-times-sale-price-column.png`](10-units-sold-times-sale-price-column.png) | Row-context multiplication |
| [`11-highvalue-profits-table.png`](11-highvalue-profits-table.png) | Numeric `FILTER` |
| [`12-profit-less-gross-sales-column.png`](12-profit-less-gross-sales-column.png) | Row-context subtraction |
| [`13-sale-price-less-manufacturing-price-column.png`](13-sale-price-less-manufacturing-price-column.png) | Sale-price/manufacturing-price subtraction |
