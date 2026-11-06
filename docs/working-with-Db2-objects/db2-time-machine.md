---
title: "Viewing historical table data by using Db2 Time Machine"
---

# {{ page.title }}

Db2 Time Machine lets you view how the data in a temporal table looked at a specific point in time. You can compare the contents of a table at different times to understand how its data has changed. If a table doesn't track history yet, Db2 Time Machine shows the SQL statements that you need to run to enable it.

## Before you begin

Db2 Time Machine is locked until you log in to Genius Hub. Log in to Genius Hub before you use the feature. For more information, see [Connecting to Genius Hub]({{site.baseurl}}/docs/working-with-sql/querying-data-by-using-natural-language#connecting-to-genius-hub).

## Viewing the history of a temporal table

A temporal table records every change (INSERT, UPDATE, and DELETE) so that you can query the data as it looked at any past moment.

1. In the **Db2 Connections** pane, expand the connection, schema, and **Tables** folder.
2. Right-click the table, and then click **See History**.

   The table details open on the **History** tab. You can also open the table and click the **History** tab.

3. In the **View data as of** field, select the date and time that you want to view. To select the date and time, use one of the following methods:
   - In the **Timeline navigator**, drag the slider to a year between 2000 and the current year, or click one of the **Jump to** buttons.
   - Use the **Month**, **Day**, **Hour**, **Min**, and **Sec** lists to set the exact time.
   - Click **Use current time** to select the current date and time.

   The **Selected** label under the lists shows the date and time that you chose.

4. Click **View history**.

   

To compare the table at another point in time, select a different date and time, and then click **View history** again.

Each time you view the history of a table, the extension saves an entry to **Query History** that starts with `Time Machine:` followed by the table name.

## Enabling history tracking for a table

If the table that you select is not a temporal table, the **History** tab shows the message **This table doesn't track history yet**. The tab also shows the SQL statements that you need to run to add history tracking to the table.

1. Click **Copy SQL**.
2. Open a **Db2 SQL Editor** that is connected to the same database, and paste the statements.
3. Run the statements in the order they are shown.

   The statements do the following:

   | Step | What the statements do |
   |------|------------------------|
   | 1 | Add the system-period columns `SYS_START`, `SYS_END`, and `TS_ID` to the table. |
   | 2 | Define the `SYSTEM_TIME` period by using `SYS_START` and `SYS_END`. |
   | 3 | Create a history table that has the same structure as the table. The history table name is the table name followed by `_HISTORY`. |
   | 4 | Enable versioning by associating the history table with the table. |

4. Refresh the table, and then open the **History** tab again.

To learn more about temporal tables, click **Db2 docs** on the **History** tab.

**Note:** Db2 captures history from the moment that versioning is enabled. Earlier changes are not tracked retroactively.


