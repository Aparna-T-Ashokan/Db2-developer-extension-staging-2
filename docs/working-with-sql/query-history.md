---
title: "Query History"
---

# {{ page.title }}
---

The **QUERY HISTORY** view lists previously run SQL statements. Run at least one SQL statement from the Db2 SQL Editor for history entries to appear. You can open a history entry to view status details and results.

Query history is persistent — your previously run queries are retained even after you close and reopen VS Code, so you can always refer back to earlier work.

## Viewing queries in Query History
---

1. On the **Db2 Connections** pane, locate **QUERY HISTORY** and expand it.


   This section lists all previously run queries, which are grouped by timestamp and sorted in reverse chronological order, by default.


2. Find the timestamped query record that you want to inspect and click it to show the **Statement summary**.

   Statement summary shows the following details:


   ![Run multiple queries]({{site.baseurl}}/assets/images/history-execution-summary.png)


   - File: Indicates the source of the statements that were run. For example, Db2 SQL Editor means that the statements were run from the SQL editor in the extension.
   - Statement date: Timestamp when the query was run.
   - Connection: Shows the database connection details used for running the query.
   - Metric:
      - Total statements run: Total count of SQL statements that were run together.
      - Success: Number of statements that ran successfully without errors.
      - Failure: Number of statements that failed during execution.
      - Warning: Number of statements that completed with warnings.
      - Total elapsed time (ms): The cumulative time taken to run all the statements in the group, in milliseconds.

3. Expand a timestamped query group to display the individual SQL statements executed during that session. Click a statement to open its **Query Detail** view.

   The **Query Detail** view opens in a new window and provides the following information and actions:

   ![Query Detail view]({{site.baseurl}}/assets/images/query-details.png)

   - **SQL Statement panel**:
     - Shows the full SQL query text.
     - **Copy icon**: Copies the SQL statement to your clipboard.
     - **Run icon** (▶): Runs the query directly from the Query Detail view. A prompt appears to select the database connection, and the results are displayed in the results window.
     - **Open button** (**Open ↗**): Opens the query in the **Db2 SQL Editor**, where you can modify and run the SQL statement.
   - **Status panel**:
     - **Message**: Status text describing the execution result (for example, *Query processed successfully*).
     - **Return code**: Return code indicating the outcome (for example, *0* for success).
     - **SQL code**: Db2-specific SQLCODE returned after processing the statement.
     - **SQL state**: Standard SQLSTATE code for error reporting.
   - **Execution details**:
     - **File**: Source file or editor from which the query was executed (for example, *Db2 SQL Editor*).
     - **Executed**: Date and time when the query was run.
     - **Connection**: Database connection profile used (for example, *SAMPLE@localhost*).
     - **Elapsed time (ms)**: Total execution duration in milliseconds.
   - **Past results**:
     - Expand the **Past results** section to view the query output in a table. You can sort any column in ascending or descending order by clicking the column header.

## Using Genius AI options with Query History
---

You can interact with queries in **QUERY HISTORY** using Genius AI:

- **Chat with AI**: Hover over or right-click a query in **QUERY HISTORY** and select **Chat with AI**. The SQL statement is automatically populated in the **Genius AI** chat input box, where you can modify or send it to ask questions or get assistance.
- **Analyse Query Performance**: Click the **Analyse Query Performance** option on a query in **QUERY HISTORY**, or right-click the query and select **Genius: Analyse Query Performance**. Genius AI analyzes the query execution plan and performance. Click **View Performance** to inspect the execution plan, visual diagram, statistics, and index recommendations.



