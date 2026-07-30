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

## Viewing LOB data

When a result cell contains a large-object (LOB) data type such as CLOB, BLOB, DBCLOB, XML, or BINARY, click the cell to open the **LOB Viewer**. The LOB Viewer displays the column name, data type, character count, and the full captured content. Click **Copy** to copy the content to the clipboard.

You can open multiple columns in the LOB Viewer simultaneously — each opens in its own tab. Clicking the same cell a second time focuses the existing tab rather than opening a duplicate.

> **Note**: A zero-byte BLOB value is rendered as `NULL` in the viewer.
{: .note-right}

## Running transactions

Each SQL editor tab maintains a dedicated database connection. Because the same connection is used for all query executions within a tab, transaction state and session state are preserved across multiple query executions.

You can execute transaction statements such as `Begin Transaction`, `ROLLBACK`, `COMMIT`, and `End Transaction` from a SQL editor. These statements run on the same database connection, allowing Db2 to maintain the transaction context until the transaction is committed or rolled back.

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

Because the connection remains associated with the SQL editor tab, session-specific objects and settings, such as temporary tables and session variables, remain available across query executions while the dedicated connection is active.

> **Note:** Each SQL editor tab maintains its own dedicated connection and transaction state. Transactions, temporary tables, session variables, and other session-specific settings created in one SQL editor tab are isolated from other open SQL editor tabs.
{: .note-right}

## Running Selected SQL statements in SQL Editor
---

To run a single SQL statement, do the following steps: 
1. Write your SQL statements in the editor. 
2. Select the appropriate database connection from the dropdown menu.
3. Right‑click in the editor and select **Run Selected Query**. 


The statement result appears in the **Results** pane.


Click **Save** to save your SQL statements. You can also download the query results in CSV or JSON format for later use. The SQL statements results are also stored in the **QUERY HISTORY** menu in the sidebar.



