---
title: "Running SQL statements"
---



# {{ page.title }}


IBM Db2 Developer Extension supports running multiple SQL statements within a single editor session. You can run all statements at once or select specific statements to run individually. Each statement that is run generates its own result tab in the Results pane, making it easier to review and compare the output from each statement.

Each SQL file editor uses a dedicated database connection. The connection remains associated with the editor while it is active, which allows transaction state, temporary tables, and session variables to persist across query executions.

## Running multiple SQL statements in SQL Editor
---


To run multiple SQL statements, do the following steps.
1. Click **Open SQL Editor** (![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"}) in the DB2 CONNECTIONS pane. **Db2 SQL Editor** opens.
2. Select the database connection from the dropdown menu.
3. Write SQL statements in the editor.
4. Right‑click in the editor and select **Run All Queries**. Alternatively, you can click **Run** to run all the statements.


When you run multiple SQL statements, the extension runs them sequentially and presents the consolidated results in the **Results** pane. Each statement's result set appears in its own tab (for example, Query 1, Query 2).




![Run multiple queries]({{site.baseurl}}/assets/images/run-sql-mulitple.png)



> **Note**: When you click the layout toggle icon, the **Results** pane switches from the default vertical view to a horizontal view, where the results are aligned horizontally with the editor. Click the icon again to return the results to the vertical alignment with the editor.
{: .note-right}

You can search in the result set. Click **Export** to download your query results in CSV or JSON.

## Viewing complex data types

When a result cell contains a complex or large-object data type, a **View** button appears in the cell. Click **View** to open the data viewer, which displays the content formatted by type:

- **JSON and XML**: Displayed with readable formatting.
- **BLOB and Binary**: Displayed in hexadecimal notation.
- **Spatial**: Displayed using `x'...'` hex notation.
- **CLOB, VECTOR, and EMBEDDING**: Displayed as text content.

You can open multiple columns in the viewer simultaneously — each opens in its own tab. Clicking **View** on the same cell a second time focuses the existing tab rather than opening a duplicate. Click **Copy** in the viewer to copy the displayed content to the clipboard.

> **Note**: A zero-byte BLOB value is rendered as `NULL` in the viewer.
{: .note-right}

## Running transactions

Each SQL editor tab maintains a dedicated database connection. Because the same connection is used for all query executions within a tab, you can reliably run multi-statement transactions.

Statements such as `BEGIN`, `COMMIT`, and `ROLLBACK` execute on the same database connection, which preserves transaction state across multiple query executions.

**Example:**
```sql
BEGIN;
INSERT INTO orders VALUES (101, 'item-A');
UPDATE inventory SET qty = qty - 1 WHERE item = 'item-A';
COMMIT;
```

When you run these statements from the same SQL editor tab, Db2 processes them as a single transaction.

> **Note**: Each SQL editor tab maintains its own independent connection and transaction state. Transactions started in one tab do not affect other open SQL editor tabs.
{: .note-right}

## Running Selected SQL statements in SQL Editor
---

To run a single SQL statement, do the following steps: 
1. Write your SQL statements in the editor. 
2. Select the appropriate database connection from the dropdown menu.
3. Right‑click in the editor and select **Run Selected Query**. 


The statement result appears in the **Results** pane.


Click **Save** to save your SQL statements. You can also download the query results in CSV or JSON format for later use. The SQL statements results are also stored in the **QUERY HISTORY** menu in the sidebar.



