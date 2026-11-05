---
title: "Analyzing query performance"
---

# {{ page.title }}

The performance analyzer in IBM Db2 Genius Code helps you analyze how a SQL query runs and identify opportunities to optimize it. It brings execution plan details, visual diagrams, statistics, index recommendations, and AI-powered insights together in one place.

## Before you begin

The performance analyzer is part of Genius AI. Log in to Genius Hub and select a database in the **Genius AI** chat panel. For more information, see [Querying data by using Genius AI]({{site.baseurl}}/docs/working-with-sql/querying-data-by-using-natural-language).

## Analyzing a query

1. In the **Genius AI** chat panel, ask Genius AI to analyze the performance of a SQL query.

   You can also use the `performance analyzer` slash command.
2. Wait for the analysis to complete.

   Genius AI summarizes the execution plan, highlights potential performance bottlenecks, and lets you explore the results in more detail.

## Exploring the results

The performance analyzer provides the following views:

- **Explain plan**: Shows the operations that are involved in running the query.
- **Diagram**: Shows the execution plan as a diagram. The diagram helps you understand the flow of operations, see how they are connected, and identify potential performance bottlenecks.
- **Statistics**: Includes a section for generating the `RUNSTATS` command and a section for index recommendations.

### Asking Genius AI about the plan

Click **Ask Genius AI** to ask questions about the execution plan and get more insight into specific operations. This helps you understand potential issues and explore possible improvements.

### Improving statistics and indexes

1. In the **Statistics** section, generate the `RUNSTATS` command.
2. In the **Indexes** section, review the index recommendations that might improve the query performance.
3. Apply a suitable index.
4. Run the query again and analyze its performance to see how the change affects query execution.
