---
title: "Running SQL statements"
---

# {{ page.title }}

IBM Db2 Genius Code supports running SQL statements within the SQL editor. You can run individual statements using inline run buttons or execute multiple statements at once using the main run button. Each executed statement generates its own tab in the results panel, making it easy to review and compare output.

Each SQL file editor uses a dedicated database connection. The connection remains associated with the editor while it is active, which allows transaction state, temporary tables, and session variables to persist across query executions.

## Running queries in Db2 SQL Editor
---

1. Click **Open SQL Editor** (![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"}) in the **Db2 Connections** pane.
2. Select the database connection from the dropdown menu at the top of the editor.
3. Enter your SQL statements in the editor.
4. Choose how to run or analyze your queries:
   - **Run a single statement or selected query**: Click the inline **▶ Run** button directly above the statement, or highlight a statement, right-click, and select **Run Selected Query**.
   - **Run multiple statements**: Click the **Run ▶** button in the top toolbar to execute all statements in the editor, or right-click anywhere in the editor and select **Run All Queries**.
   - **Analyze query performance**: Right-click a statement and select **Genius: Analyze Query Performance**. For more information, see [Analyzing query performance]({{site.baseurl}}/docs/working-with-sql/analyzing-query-performance).

The results appear in the **DB2 GENIUS CODE** panel in the terminal area. Each executed query produces its own tab (for example, **Query 1**, **Query 2**).

### Query Results features

The **Query Results** panel provides several interactive tools:

- **View modes**: Toggle between **Table view** (grid) and **Chart mode** (graph) using the view icons.
- **Search results**: Use the **Search results** search bar to search for specific text across returned rows.
- **Filter** (![Filter]({{site.baseurl}}/assets/images/filter.png){:width="20" :height="20"}): Click the filter icon to apply filters to result columns.
- **Export**: Click the download/export icon (**⤓**) to export query results in **CSV** or **JSON** format.
- **Open in Db2 SQL Editor**: Click the open icon (![Open]({{site.baseurl}}/assets/images/open-icon.png){:width="20" :height="20"}) to open the query results in a full editor tab (**Results: Db2 SQL Editor**).
- **Drag and drop columns**: Drag and drop column headers to rearrange column positions.
- **Sort columns**: Click the three dots icon (**⋮**) in a column header, and then select **Sort ascending** or **Sort descending**.

## Viewing LOB and complex data in Data Viewer

When a result cell contains large-object (LOB) or complex data types—such as BINARY, VARBINARY, BLOB, CLOB, DBCLOB, XML, Spatial, Vector Embeddings, or Metadata—click the cell to open it in the **Data Viewer** pane. The Data Viewer displays:

- The **Column name**, **Data type**, formatted **Size** (e.g., in bytes), and the **Row** and **Col** numbers.
- The formatted or captured cell content.
- A copy icon (![Copy]({{site.baseurl}}/assets/images/copy.png){:width="20" :height="20"}) in the upper-right corner to copy the full content to the clipboard.

You can open multiple cells simultaneously—each opens in its own tab. Clicking an already opened cell switches focus to its existing tab rather than opening a duplicate.

> **Note**: A zero-byte or null value is rendered as `NULL` in the viewer regardless of the data type.
{: .note-right}

## Running a statement from the SQL editor

You can run SQL statements directly from the SQL editor without interrupting your workflow. Select the appropriate run option to run your statement.

## Setting the statement terminator {#setting-the-sql-statement-terminator}

By default, the extension uses a semicolon (`;`) to separate SQL statements. You can set a different default terminator in the VS Code settings instead of specifying it repeatedly in each SQL file.

1. Open Visual Studio Code and click the gear icon (![Db2 developer settings]({{site.baseurl}}/assets/images/gear-icon.png){:width="25" :height="25"}) and then **Settings**.
2. Search for `Db2` or go to **Extensions** and select **IBM Db2 Genius Code Settings**.
3. In the **Db2service: Statement Terminator** field, enter the terminator that you want to use, for example, `@`.

To use a different terminator in a single file, add `--#SET TERMINATOR <char>` to that file. This overrides the **Db2service: Statement Terminator** setting for that file only.

If your SQL file contains statements that end with a different terminator than the one that is configured, only the statements that match the configured terminator run successfully. For example, if the terminator is set to `@` and only the first query in a file ends with `@`, only the first query runs successfully. Change the terminator to match your statements, and then run the queries again to run all of them.

## Running transactions

Each SQL editor tab maintains a dedicated database connection. Because the same connection is used for all query executions within a tab, transaction state and session state are preserved across multiple query executions.

You can start a transaction by using either `Start Transaction` or `Begin Transaction`. Both statements are supported. You can then run `ROLLBACK`, `COMMIT`, and `End Transaction` from a SQL editor. These statements run on the same database connection, allowing Db2 to maintain the transaction context until the transaction is committed or rolled back.

**Example:**

```sql
Begin Transaction;

INSERT INTO ADNAAN.ACT (ACTNO, ACTKWD, ACTDESC)
VALUES (5463, 'lkol', 'ibml');

select * from ADNAAN.ACT ;

rollback;

commit;
End Transaction
```

This example demonstrates the following workflow:

1. `Begin Transaction` starts the transaction and establishes the transaction boundary.
2. The `INSERT` statement adds a new row to the `ADNAAN.ACT` table.
3. The `SELECT` statement queries the table so you can verify the inserted row within the current transaction context. The new row is visible at this point because the transaction has not yet been committed or rolled back.
4. `rollback` undoes the `INSERT`, reverting the table to its state before the transaction began. If you were to run another `SELECT` here, the inserted row would no longer appear.
5. `commit` finalizes any remaining changes and makes them permanent in the database.
6. `End Transaction` closes the transaction boundary.

After you commit a transaction, you cannot roll it back. If you run `ROLLBACK` after `COMMIT`, the statement fails because the transaction was already committed.

Whenever the extension detects a transaction identifier, it maintains a dedicated connection to the Db2 server.

Because the connection remains associated with the SQL editor tab, session-specific objects and settings, such as temporary tables and session variables, remain available across query executions while the dedicated connection is active.

Transactional query support is available in the SQL file Editor. The result set is limited to 100 rows. To retrieve the complete result set, run the query directly in the SQL file Editor.

> **Note:** Each SQL editor tab maintains its own dedicated connection and transaction state. Transactions, temporary tables, session variables, and other session-specific settings created in one SQL editor tab are isolated from other open SQL editor tabs.
{: .note-right}

## Running Selected SQL statements in SQL Editor
---

To run a single SQL statement, do the following steps: 
1. Write your SQL statements in the editor. 
2. Select the appropriate database connection from the dropdown menu.
3. Right‑click in the editor and select **Run Selected Query**. 


The query results appear in the terminal.


Click **Save** to save your SQL statements. You can also download the query results in CSV or JSON format for later use. The SQL statements results are also stored in the **QUERY HISTORY** menu in the sidebar.



