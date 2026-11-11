---
title: "Viewing historical table data by using Db2 Time Machine"
---

# {{ page.title }}

Db2 Time Machine enables you to view how the data in a temporal table looked at a specific point in time. You can select a date and time to retrieve historical data and understand how records have changed over time.

If a table does not track history yet, Db2 Time Machine provides an option to convert it into a temporal table by using Genius AI.

## Before you begin

Db2 Time Machine requires you to log in to Genius Hub. Sign in through the **Account** view in the sidebar before using this feature.

For more information, see [Connecting to Genius Hub]({{site.baseurl}}/docs/working-with-sql/querying-data-by-using-natural-language#connecting-to-genius-hub).

## Viewing the history of a temporal table

A temporal table maintains historical versions of its data, allowing you to retrieve records as they existed at a specific point in time.

1. In the **Db2 Connections** pane, expand the connection, schema, and **Tables** folder.
2. Right-click the temporal table and select **See History**.

   Alternatively, open the table and select the **Time Machine** tab.

3. In the **Time Machine** view, select the date and time for which you want to retrieve historical data. You can use the following options:
   - **Jump to**: Select one of the available year shortcuts to quickly navigate to a historical point in time.
   - **Present time**: Select the current date and time.
   - **Choose a date**: Select a specific date using the date picker.
   - **Choose a time**: Specify the exact time using the time field and AM/PM selector.
   - **Clear**: Reset the selected date and time.

4. Review the generated SQL query. Db2 Time Machine generates a query using the `FOR SYSTEM_TIME AS OF` clause and the selected timestamp. For example:

   ```sql
   SELECT *
   FROM "ALL_OBJECTS_WITH_DATA"."PRICE_HISTORY"
   FOR SYSTEM_TIME AS OF TIMESTAMP('2026-11-09 16:27:26');
   ```

5. Click **Run** to execute the query and retrieve the historical data.

   You can also use **Save** to save the generated SQL for later use.

Each time you execute a Time Machine query, an entry is added to **Query History**, making it easier to revisit previously executed historical queries.

## Enabling history tracking for a table

If the selected table is not temporal, the **Time Machine** tab displays a message indicating that the table does not track history yet.

You can convert the table into a temporal table by using Genius AI.

1. Open the non-temporal table and select the **Time Machine** tab.
2. Click **Convert using Genius AI**.
3. Genius AI generates the required SQL statements to enable temporal history tracking.
4. Review the generated SQL and execute the statements to convert the table.
5. Refresh the table and reopen the **Time Machine** tab to access historical data.

After history tracking is enabled, Db2 automatically maintains historical versions of the table data.

> **Note:** Db2 captures history only from the moment versioning is enabled. Changes made before enabling versioning are not tracked retroactively.
{: .note-right}

To learn more about temporal tables, see the Db2 documentation available from the extension.
