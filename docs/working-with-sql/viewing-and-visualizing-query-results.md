---
title: "Viewing and visualizing query results"
---

# {{ page.title }}

When you run SQL statements in IBM Db2 Genius Code, the query results are displayed in the **DB2 GENIUS CODE** panel in the terminal area. Each executed query generates its own tab (for example, **Query 1**, **Query 2**), allowing you to review, search, filter, export, and visualize your data interactively.

![Query results window]({{site.baseurl}}/assets/images/results-window.png)

## Working with tabular results

The table view presents your query results in a structured grid with the following interactive features:

- **Search results**: Enter keywords in the **Search results** bar to quickly find matching data across all returned rows.
- **Filter results**: Click the filter icon to apply specific filtering criteria to the result columns.
- **Drag and drop columns**: Click and drag column headers to reorder columns in the table so that the most relevant information is positioned where you need it.
- **Sort columns**: Click a column header to sort values in ascending or descending order.
- **Pagination**: Use the pagination controls at the bottom of the table to set **Items per page** (for example, 25, 50, 100) and navigate between result pages.
- **Export to CSV or JSON**: Click the export icon (**⤓**) in the toolbar to download your query results in CSV or JSON format for offline analysis, reporting, or sharing.
- **Open in Db2 SQL Editor**: Click the open icon (**⧉**) in the toolbar to open the results in a full editor tab (`Results: Db2 SQL Editor`).

## Exploring data in the Data Viewer

A dedicated **DATA VIEWER** panel is displayed alongside the query results. When you click on any result cell containing large-object (LOB) or complex data types—such as BINARY, VARBINARY, BLOB, CLOB, DBCLOB, XML, Spatial, or Vector Embeddings—its complete content is displayed in the Data Viewer.

Key features of the **Data Viewer** include:

- **Multiple tab support**: Each clicked cell opens in its own tab (for example, `C_BLOB #1`, `C_DBCLOB #2`, `C_XML #3`), making it easy to inspect and compare multiple data values side by side. Clicking an already open cell switches focus to its existing tab.
- **Detailed cell metadata**: The top header of each tab displays:
  - **Column name**: Name of the column.
  - **Data type**: Specific data type (for example, `XML`, `BLOB`, `BINARY`).
  - **Size**: Formatted data size (for example, `61 bytes`).
  - **Row** and **Col**: The row number and column position of the cell in the result set.
- **Copy content**: Click the copy icon in the upper-right corner of the viewer tab to copy the formatted content to the clipboard.
- **Close tabs**: Click the close icon (**×**) on any tab to dismiss it when finished.

## Visualizing results in Chart / Graph mode

Instead of analyzing results only in tabular format, you can switch to chart mode to visualize data patterns, trends, and comparisons:

1. In the **Query Results** toolbar, click the **Chart mode** icon (bar chart icon) next to the table view icon.
2. In the configuration panel on the left:
   - **Chart type**: Select your desired chart type from the dropdown (for example, **Bar**, **Line**, **Area**, **Pie**, or **Scatter**).
   - **X-Axis**: Select the column to use for the X-axis (category or horizontal dimension).
   - **Y-Axis**: Select the column to use for the Y-axis (metric or vertical dimension).
   - **+ Add column**: Click **+ Add column** to add additional metrics or data series to compare multiple values on the same chart.

The chart updates interactively as you configure your dimensions and series.
