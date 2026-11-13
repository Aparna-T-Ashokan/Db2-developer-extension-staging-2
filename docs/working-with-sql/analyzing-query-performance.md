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
  1. In the **Db2 SQL Editor**, select the SQL query.
  2. Right-click the selected query, and then select **Genius: Analyze Query Performance** from the context menu.

- **From Query History**:
  1. In the **Db2 Connections** pane, locate and expand **QUERY HISTORY**.
  2. Find the query that you want to analyze, and click **Analyze Query Performance** (![Analyze query performance]({{site.baseurl}}/assets/images/analyze-query.png){:width="20" :height="20"}), or right-click the query and select **Genius: Analyze Query Performance**.

Genius AI runs the performance analysis on the selected query in the **Genius AI** chat panel, summarizing the execution plan and identifying potential bottlenecks.

Click **View Performance** in the Genius AI response to open the performance analyzer and explore the results in detail.

**Note:** You can also analyze queries directly in the **Genius AI** chat panel by asking Genius AI or by entering `/` to use slash commands (such as the `performance analyzer` command).

## Exploring the results

At the top of the performance analyzer, a summary bar shows the key metrics for the query: estimated runtime, the number of rows scanned compared with the number of rows returned, CPU time, and pages read.

The **Finding** section highlights the most important issue that was detected. For example, a finding can tell you that a table is read in full and how much the estimated runtime drops if the recommended indexes are created. In the summary bar, click **View query** to see the SQL statement that is analyzed, or click **Run again** to analyze the query again.

The performance analyzer provides the following tabs:

- **Explain plan**: Shows the execution plan for the query as a table or as a diagram.
- **Statistics**: Shows `RUNSTATS` recommendations for the tables that the query uses. You can apply the recommendations to update the table statistics that the optimizer uses.
- **Indexes**: Shows the index recommendations that might improve the query performance.

### Explain plan

The explain plan generates the execution plan for the query. Use the following icons above the plan to switch between two views of the same plan:

- **Table view** (![Table view]({{site.baseurl}}/assets/images/table-view.png){:width="20" :height="20"}): Shows the plan as a table.
- **Diagram view** (![Diagram view]({{site.baseurl}}/assets/images/diagram-icon.png){:width="20" :height="20"}): Shows the plan as a diagram.

#### Table view

The table view lists each operation in the plan in a row. The columns show the step number (**#**) and the **Operation**. Each operation shows its name (for example, **Full scan**, **Sort**, or **Hash join**) and its operator type (for example, `TBSCAN`, `SORT`, or `HSJOIN`). The operations are indented to show how they are nested in the plan. Use the arrows next to an operation to expand or collapse it.

![Performance analyzer showing the explain plan and the Genius AI response]({{site.baseurl}}/assets/images/analyze-performance.png)

#### Diagram view

The diagram view shows the plan as a flow of connected operators.

![Explain plan diagram view]({{site.baseurl}}/assets/images/diagram-view.png)

In the diagram:

- Each node shows the step number, the operator type (for example, `RETURN`, `TBSCAN`, or `SORT`), and the estimated cost in timerons.
- Arrows connect the operators and show the order in which data flows through the plan.
- A warning icon (⚠) and a yellow outline mark operators that might cause performance problems, such as a full table scan (`TBSCAN`) or a hash join (`HSJOIN`).
- The overview map at the upper right of the diagram shows the whole plan. The operators that are highlighted in yellow are the ones with warnings. The blue box shows the part of the plan that is currently displayed.

Use the controls above the overview map to navigate larger plans:

- **Zoom out** (magnifying glass with a minus sign): Makes the diagram smaller.
- **Zoom in** (magnifying glass with a plus sign): Makes the diagram larger.
- **Fit to screen** (square brackets icon): Resizes the diagram so that the whole plan fits in the view.
- **Overview map** (overlapping squares icon): Shows or hides the overview map.

#### Operation details

Click an operation in the table or a node in the diagram to see its details in the **Details** panel. Click the close icon (**×**) to close the panel. The panel shows the operation number and type, the operation name, and the following information:

- **Time** and **Share of query**: How long the operation takes and what percentage of the total time it accounts for.
- **Estimated rows**: The estimated number of rows that the operation returns.
- **Est. cost**: The estimated cost of the operation.
- **Pages read**: The number of pages that the operation reads.

### Improving statistics and indexes

1. Click the **Statistics** tab. The **RUNSTATS recommendations** list shows the tables that the query uses, with the **TABLE SCHEMA**, **TABLE NAME**, and **CARDINALITY** of each table.

   ![RUNSTATS recommendations on the Statistics tab]({{site.baseurl}}/assets/images/stats.png)

   1. Select the tables that you want to update. To select all tables, select the check box in the header row.
   2. Click **Apply RUNSTATS** to update the statistics for the selected tables. Current statistics help the optimizer choose efficient access plans.

   To review or edit the `RUNSTATS` command before you apply it, click **Open SQL script**, or click the script icon at the end of a table row to open the script for that table only.

2. Click the **Indexes** tab. The **Index recommendations** list shows the estimated cost of the query if the recommended indexes are applied (for example, from 708 to 563.096 timerons). For each recommendation, review the **Index name**, **Schema**, **Table**, **Key columns**, **Contribution**, and **Disk usage**.

   ![Index recommendations on the Indexes tab]({{site.baseurl}}/assets/images/index.png)

   1. Select the indexes that you want to create. To select all indexes, select the check box in the header row.
   2. Click **Apply indexes** to create the selected indexes.

   To review the `CREATE INDEX` statement before you create the index, click **Open SQL script**, or click the script icon at the end of an index row to open the script for that index only. The script opens in the **Db2 SQL Editor**, where you can run it.

3. Click **Run again** to analyze the query again and see how the change affects the plan and the cost.

### Asking Genius AI about the plan

In the **Details** panel, click **Ask Genius** to ask Genius AI about the selected operation. Genius AI explains what the operation does, why it might be slow, and what you can do to improve it. You can continue the conversation in the **Genius AI** chat panel, for example, to ask Genius AI to suggest changes that improve the plan, such as rewriting the query or creating an index.

## Generating an explain plan

Use **Genius: Generate Explain plan** to have Genius AI generate the execution plan for a query in the **Genius AI** chat panel.

1. In **QUERY HISTORY**, right-click the query.
2. Select **Genius: Generate Explain plan**.
3. In the **Genius AI** chat panel, make sure that a database is selected, and then send the *Explain Plan for:* request that is filled in with your SQL statement.

Genius AI generates the execution plan for the query. To see the full plan, click **Open** on the **Explain Plan**. The plan opens in a read-only **Explain Plan** editor, as shown in the following figure:

![Explain plan editor and the Genius AI response]({{site.baseurl}}/assets/images/explain-plan.png)


The **Explain Plan** editor shows the following information:

- The SQL statement that the plan is for.
- The estimated cost and estimated cardinality of the query.
- The access plan, which lists each operation in the order that it runs (for example, **Return**, **Table scan**, **Sort rows**, **Filter data**, **Merge Stream**, and **Group by**), with the estimated cost and estimated number of rows for each operation.

Click **Copy** to copy the explain plan to the clipboard.
