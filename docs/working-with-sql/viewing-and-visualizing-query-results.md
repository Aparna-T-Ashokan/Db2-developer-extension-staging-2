---
title: "Viewing and visualizing query results"
---

# {{ page.title }}

When you run SQL statements in IBM Db2 Genius Code, the query results are displayed in the **DB2 GENIUS CODE** panel in the terminal area. Each executed query generates its own tab (for example, **Query 1**, **Query 2**), allowing you to review, search, filter, export, and visualize your data interactively.

![Query results window]({{site.baseurl}}/assets/images/results-window.png)

## Query results features

The **Query Results** panel provides several interactive tools:

- **View modes**: Toggle between **Table view** (grid) and **Chart mode** (graph) by using the view icons.
- **Search results**: Use the **Search results** bar to search for specific text across returned rows.
- **Filter**: Click the filter icon to apply filters to result columns.
- **Sort columns**: Click a column header to sort values in ascending or descending order.
- **Drag and drop columns**: Drag and drop column headers to rearrange column positions.
- **Pagination**: Adjust **Items per page** (for example, 25, 50, 100) and navigate through pages.
- **Export**: Click the export icon (**⤓**) to export query results in CSV or JSON format.
- **Open in Db2 SQL Editor**: Click the open icon (**⧉**) to open the query results in a full editor tab (**Results: Db2 SQL Editor**).

## Viewing LOB and complex data in Data Viewer

When a result cell contains large-object (LOB) or complex data types — such as BINARY, VARBINARY, BLOB, CLOB, DBCLOB, XML, Spatial, Vector Embeddings, or Metadata — click the cell to open it in the **Data Viewer** pane. The **Data Viewer** displays:

- **Column name**, **Data type**, formatted **Size** (for example, in bytes), and the **Row** and **Col** numbers.
- The formatted or captured cell content.
- A **Copy** button in the upper-right corner to copy the full content to the clipboard.

You can open multiple cells simultaneously — each opens in its own tab (such as `C_BLOB #1`, `C_DBCLOB #2`, `C_XML #3`). Clicking an already open cell switches focus to its existing tab rather than opening a duplicate. Click the close icon (**×**) on any tab to dismiss it when finished.

> **Note**: A zero-byte or null value is rendered as `NULL` in the viewer regardless of the data type.
{: .note-right}
