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

   The table details open on the **Time Machine** tab. You can also open the table and click the **Time Machine** tab.

3. In the **View data as of** field, select the date and time that you want to view. To select the date and time, use one of the following methods:
   - In the **Timeline navigator**, drag the slider to a year between 2000 and the current year, or click one of the **Jump to** buttons.
   - Use the **Month**, **Day**, **Hour**, **Min**, and **Sec** lists to set the exact time.
   - Click **Use current time** to select the current date and time.

   The **Selected** label under the lists shows the date and time that you chose.

4. Click **View history**.

   

To compare the table at another point in time, select a different date and time, and then click **View history** again.

Each time you view the history of a table, IBM Db2 Genius Code saves an entry to **Query History** that starts with `Time Machine:` followed by the table name.

## Enabling history tracking for a table

If the table that you select is not a temporal table, the **Time Machine** tab shows the message **You can time travel through _table name_ soon** and indicates that the table does not yet track history.

### Converting a table to a temporal table by using Genius AI

1. On the **Time Machine** tab, click **Convert using Genius AI**.

   Genius AI generates the SQL statements needed to convert the table to a temporal table and displays them in the **Genius AI** panel.

2. Click **Open** (↗) to open the generated statements in the **Db2 SQL Editor**.
3. Run the statements one by one in the order they are shown:
   - **Step 1**: Add the system-period columns `SYS_START`, `SYS_END`, and `TRANS_ID` to the table.
   - **Step 2**: Create a history table that has the same structure as the table. The history table name is the table name followed by `_HISTORY`.
   - **Step 3**: Enable versioning by linking the base table to the history table.
4. Refresh the table, and then open the **Time Machine** tab again.

To learn more about temporal tables, click **Db2 docs** on the **Time Machine** tab.

**Note:** Db2 captures history from the moment that versioning is enabled. Earlier changes are not tracked retroactively.


