---
title: "Analyzing query performance"
---

# {{ page.title }}

The performance analyzer in IBM Db2 Genius Code helps you analyze how a SQL query runs and identify opportunities to optimize it. It brings execution plan details, visual diagrams, statistics, index recommendations, and AI-powered insights together in one place.

## Before you begin

The performance analyzer is part of Genius AI. Log in to Genius Hub and select a database in the **Genius AI** chat panel. For more information, see [Querying data by using Genius AI]({{site.baseurl}}/docs/working-with-sql/querying-data-by-using-natural-language).

## Analyzing a query

You can analyze the performance of a query directly from the **Db2 SQL Editor** or from **QUERY HISTORY**:

- **From the SQL Editor**:
  1. In the **Db2 SQL Editor**, select or right-click the SQL query.
  2. Select **Genius: Analyze Query Performance** from the context menu.

- **From Query History**:
  1. In the **Db2 Connections** pane, locate and expand **QUERY HISTORY**.
  2. Find the query that you want to analyze, and click **Analyse Query Performance** (![Analyze query performance]({{site.baseurl}}/assets/images/analyze-query.png){:width="20" :height="20"}), or right-click the query and select **Genius: Analyse Query Performance**.

Genius AI runs the performance analysis on the selected query in the **Genius AI** chat panel, summarizing the execution plan and identifying potential bottlenecks.

Click **View Performance** in the Genius AI response to open the performance analyzer and explore the results in detail.

**Note:** You can also analyze queries directly in the **Genius AI** chat panel by asking Genius AI or by entering `/` to use slash commands (such as the `performance analyzer` command).

## Exploring the results

![Performance analyzer showing the explain plan and the Genius AI response]({{site.baseurl}}/assets/images/analyze-performance.png)

At the top of the performance analyzer, a summary bar shows the key metrics for the query: estimated runtime, the number of rows scanned compared with the number of rows returned, CPU time, and pages read.

The **Findings** section highlights the most important issues that were detected. For example, a finding can tell you that a table is read in full and how much the estimated cost drops if the recommended indexes are created.

The performance analyzer provides the following tabs:

- **Explain plan**: Shows the execution plan for the query as a table or as a diagram.
- **Statistics**: Shows a `RUNSTATS` command for each table that the query uses. You can apply the command to update the table statistics that the optimizer uses.
- **Indexes**: Shows the index recommendations that might improve the query performance.

### Explain plan

The explain plan generates the execution plan for the query. Use the **Table** and **Diagram** buttons to switch between two views of the same plan.

- **Table view**: Lists each operation in the plan in a row. The columns show the step number (**#**), the **Operation** (for example, a full table scan, a sort, or a return), the **Object** that the operation works on, the number of **Rows**, the **Time**, and the estimated **Cost**. Operations that take a large share of the time, such as full table scans, are highlighted so that you can find them quickly.
- **Diagram view**: Shows the plan as a flow of connected operators, with the cost in timerons on each node. A warning icon marks operators that might cause performance problems, such as a full table scan. Use the zoom in, zoom out, and fit-to-screen controls to navigate larger plans.

Click an operation in the table or a node in the diagram to see its details in the **Details** panel:

- **Time** and **Share**: How long the operation takes and what percentage of the total time it accounts for.
- **Estimated**: The estimated cost of the operation.
- **Pages read**: The number of pages that the operation reads.
- **Rows read → out**: The number of rows that the operation reads and the number of rows that it passes on.

### Improving statistics and indexes

1. Click the **Statistics** tab. For each table that is used by the query, review the generated `RUNSTATS` command, and then click **Apply RUNSTATS** to update the table statistics. Current statistics help the optimizer choose efficient access plans.
2. Click the **Indexes** tab. The tab shows the estimated cost of the query if the recommended indexes are applied (for example, from 145.857 to 6.872 timerons). For each recommendation, review the table, the percentage improvement, the columns in the index, and the `CREATE INDEX` statement.
3. Click **Open in editor** to open the `CREATE INDEX` statement in the **Db2 SQL Editor**, and then run it.
4. Click **Run again** to analyze the query again and see how the change affects the plan and the cost.

### Asking Genius AI about the plan

In the **Details** panel, click **Ask Genius** to ask Genius AI about the selected operation. Genius AI explains what the operation does, why it might be slow, and what you can do to improve it. You can continue the conversation in the **Genius AI** chat panel, for example, to ask Genius AI to suggest changes that improve the plan, such as rewriting the query or creating an index.

## Generating an explain plan

Use **Genius: Generate Explain plan** to have Genius AI generate the execution plan for a query in the **Genius AI** chat panel.

1. In **QUERY HISTORY**, right-click the query.
2. Select **Genius: Generate Explain plan**.
3. In the **Genius AI** chat panel, make sure that a database is selected, and then send the *Explain Plan for:* request that is filled in with your SQL statement.

Genius AI generates the execution plan for the query. The response shows the following information:

- **Estimated cost** and **Estimated cardinality**: The optimizer's estimates for the query, in timerons and rows.
- **Summary**: A short analysis of the plan, such as the access path that the optimizer uses and whether the query requires a sort operation that an index could eliminate.
- **Explain Plan** card: A card for the table that the query uses, with an **Open** link.

To see the full plan, click **Open** on the **Explain Plan** card. The plan opens in a read-only **Explain Plan** editor, as shown in the following figure.

![Explain plan editor and the Genius AI response]({{site.baseurl}}/assets/images/explain-plan.png)

The **Explain Plan** editor shows the following information:

- The SQL statement that the plan is for.
- The estimated cost and estimated cardinality of the query.
- The access plan, which lists each operation in the order that it runs (for example, **Return**, **Table scan**, **Sort rows**, **Filter data**, **Merge Stream**, and **Group by**), with the estimated cost and estimated number of rows for each operation.

Click **Copy** to copy the explain plan to the clipboard.
