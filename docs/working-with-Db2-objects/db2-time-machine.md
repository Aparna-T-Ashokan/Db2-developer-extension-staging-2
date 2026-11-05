---
title: "Viewing historical table data by using Db2 Time Machine"
---

# {{ page.title }}

Db2 Time Machine lets you view how the data in a temporal table looked on a specific date. You can compare the contents of a table at different points in time to understand how its data has changed.

## Before you begin

Db2 Time Machine is locked until you log in to Genius Hub. Log in to Genius Hub before you use the feature. For more information, see [Connecting to Genius Hub]({{site.baseurl}}/docs/working-with-sql/querying-data-by-using-natural-language#connecting-to-genius-hub).

## Viewing the history of a temporal table

1. Open **Db2 Time Machine**.

   If you are not logged in to Genius Hub, the feature is locked.
2. Log in to Genius Hub.

   After you log in, Db2 Time Machine is unlocked.
3. Select a date.
4. Click **View history**.

   The extension shows the data in the table as it was on the selected date, including the number of rows.

To compare the table at another point in time, select a different date and click **View history** again.

For example, if the table has 12 rows on October 16, 2026 and 24 rows on October 21, 2026, you can see that the table gained 12 rows between those dates.

## Working with tables that are not temporal tables

If the table that you select is not a temporal table, Db2 Time Machine guides you through the steps that are required to enable temporal history tracking for that table.

## Logging out of Genius Hub

When you log out of Genius Hub, Db2 Time Machine is locked again. Log in again to continue to use the feature.
