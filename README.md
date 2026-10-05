[README.md](https://github.com/user-attachments/files/33046770/README.md)
# Sales Dashboard (Power BI)

An interactive Power BI report that summarises sales performance across time, geography, products and sales representatives.

- **File:** `Sales.pbix`
- **Report size:** 1280 × 720, 2 pages
- **Built with:** Power BI Desktop (July 2024 release)

---

## Report Pages

### Page 1 – Sales Dashboard

The main overview page, titled **"Sales Dashboard"**.

**KPI cards**

| KPI | Aggregation |
|---|---|
| Total Sales | Sum of `Total sales` |
| Average Sales | Average of `Total sales` |
| Gross Profit | Sum of `Gross Profit` |
| Units Sold | Sum of `Units` |

**Slicers (filters)**

- Country
- Year
- Month (from the Date Table's date hierarchy)

**Charts**

| Visual | Fields | What it shows |
|---|---|---|
| Donut chart | `SubCategory Name` × Sum of `Total sales` | Sales share by product sub-category |
| Column chart | `Country` × Sum of `Gross Profit` | Gross profit by country |
| Funnel chart | `Sales Rep Name` × Sum of `Total sales` | Sales rep ranking by total sales |
| Waterfall chart | `ProductName` × Sum of `Total sales` | Contribution of each product to total sales |

A **Back** button in the top-left corner is provided for navigation.

### Page 2 – Quarterly Detail

A table giving a detailed breakdown by:

- `Year`
- `Quarter`
- Sum of `Total sales`
- `TotalRevenue` (a DAX measure defined on the `sales` table)

---

## Data Model

The model contains 7 tables, laid out in a single "All tables" diagram:

| Table | Role |
|---|---|
| `sales` | Fact table (sales, gross profit, units, year, quarter, country, `TotalRevenue` measure) |
| `Product` | Product dimension (`ProductName`) |
| `Sub categories` | Product sub-category dimension (`SubCategory Name`) |
| `Categories` | Product category dimension |
| `Geography` | Location dimension |
| `SalesRep` | Sales representative dimension (`Sales Rep Name`) |
| `Date Table` | Calendar table used for the Date hierarchy and month slicer |

The model follows a star-schema layout, with `sales` at the centre and the other tables acting as dimensions.

---

## How to Use

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free).
2. Open `Sales.pbix`.
3. If prompted, refresh the data. The report was created from the cloud/Power BI service, so you may need to re-point or re-authenticate the data source.
4. Use the **Country**, **Year** and **Month** slicers on Page 1 to filter all KPI cards and charts.
5. Switch to Page 2 for the Year/Quarter table.

---

## Project Structure

```
Sales.pbix
├── Report/Layout      # Pages, visuals and formatting
├── DataModel          # Tables, relationships, measures (compressed)
├── DiagramLayout      # Model diagram positions
├── Settings / Metadata
└── Report/StaticResources   # Base theme (CY24SU06)
```

---

## Notes and Possible Improvements

- Add titles to the charts that currently have none, so each visual is self-explanatory.
- Page 1 and Page 2 are named with default names; renaming them (e.g. "Overview", "Quarterly Detail") would improve navigation.
- Consider adding a Year-over-Year growth measure and a profit margin (%) KPI.
- Document the DAX measures and data source connection details here once finalised.

---

## Author

_Add your name, contact details and the date here._
