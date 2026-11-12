---
title: "Generating and running SQL statements"
---

# {{ page.title }}
---

You can generate SQL statements by multiple methods:
- Using the **Open SQL Editor** icon (![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"}) in the Db2 Connections pane.
- Using the **Create new SQL file** icon (![Creating new SQL file]({{site.baseurl}}/assets/images/create-new-sql-file.png){:width="25" :height="25"}) in the Db2 Connections pane.
- Right-clicking the object in a schema and selecting an option to generate the SQL statements.

Each SQL file editor uses a dedicated database connection. The connection remains associated with the editor while it is active, which allows transaction state, temporary tables, and session variables to persist across query executions.

## Generating and running SQL statements by using the open SQL Editor icon
---

1. Click **Open SQL Editor** (![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"}) in the Db2 Connections pane. **Db2 SQL Editor** opens.
2. Select the connection from the dropdown menu.
3. Enter your SQL statements in the editor.
4. Choose how to run or analyze your queries:
   - **Run a single statement or selected query**: Click the inline **▶ Run** button directly above the statement, or highlight a statement, right-click, and select **Run Selected Query**.
   - **Run multiple statements**: Click the **Run ▶** button in the top toolbar to execute all statements in the editor, or right-click anywhere in the editor and select **Run All Queries**.
   - **Analyze query performance**: Right-click a statement and select **Genius: Analyze Query Performance**. For more information, see [Analyzing query performance]({{site.baseurl}}/docs/working-with-sql/analyzing-query-performance).
5. The query results appear in the terminal. For more information, see [Viewing and visualizing query results]({{site.baseurl}}/docs/working-with-sql/viewing-and-visualizing-query-results).

   ![Query results window]({{site.baseurl}}/assets/images/results-window.png)

## Generating SQL statements by using the Create new SQL file icon
---

1. Click **Create new SQL file** (![Creating new SQL file]({{site.baseurl}}/assets/images/create-new-sql-file.png){:width="25" :height="25"}) in the Db2 Connections pane.
2. A new editor tab opens with the name Untitled. The extension prompts you to select the database connection to run your query. Select the required connection.

3. In the editor, type your SQL statement. For example, type the first letters of SELECT. The SELECT statement appears in the list of available SQL elements. Click SELECT statement to insert a code snippet with the basic structure.
    ![Creating new SQL file]({{site.baseurl}}/assets/images/file-new-sql-ceate.png)

4. Click **Check SQL Syntax** to validate the syntax of the SQL statement without running the statement.
5. Click **Format SQL** to reformat your SQL code to make it more readable and consistent.
6. Click **Show SQL Snippet** to see predefined SQL templates or code snippets you can insert into the editor.
    Common snippets include:
    - SELECT TOP N – Select the top N rows from a table
    - GROUP BY with HAVING
    - CREATE TABLE
    - INSERT statement
    - JOIN examples
    - MERGE statement

    When you select a snippet, the editor inserts the corresponding SQL template into your current SQL editor.

7. Click **Run SQL** to run the queries. The query results appear in the terminal.
8. Save the file with a .sql extension.

    > **Note**:
    You can also create a new SQL file by clicking File > New File and then save it as anyname.sql to enable SQL editing features.
    {: .note-right}


## Generating and running SQL statements for a table
To generate SQL statements for a table, do the following steps:
1. On the Db2 Connections pane, click the database connection and then the schema that you want. Expand the **Tables** section. Right-click the required table that you want.
2. From the menu, select the object-specific actions such as:
   - Generate DDL: Generates the Data Definition Language (DDL) to re-create that table's structure, including columns and constraints.
   - Generate DELETE: Generates a template for deleting the rows from the table.
   - Generate INSERT: Generates a template for inserting the rows into the table.
   - Generate SELECT: Generates a template for retrieving the data from the table.
   - Generate UPDATE: Generates a template for updating the rows in the table.

   The DELETE, SELECT, INSERT, and UPDATE statements open in a new **Db2 SQL Editor** tab.

   The DDL script opens in a read-only editor tab. You can copy the script, not run it directly in the editor. For more information, see [Generating DDL for a Db2 object](../the-basics/generating-ddl.md).
3. Run your SQL statements by clicking **Run**.
4. The query results appear in the terminal.


You can follow the same steps to generate SQL statements for other object types, such as views.

> **Note**: If you get errors while writing SQL statements, see [Db2-specific commands](https://www.ibm.com/docs/en/db2/12.1.x?topic=started-sql).
{: .note-right}

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
