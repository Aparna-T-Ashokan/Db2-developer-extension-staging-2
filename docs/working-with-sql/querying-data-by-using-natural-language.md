# Querying data by using natural language

You can use natural language queries in Db2 Developer Extension to ask questions about your data in plain English. The extension converts your request to SQL, runs the generated query against the selected database connection, and displays the results.

For example, instead of writing a SQL statement, you can enter:

```
Show all customers who placed orders in the last 30 days
```

The extension generates the SQL query, runs it against the selected database, and displays the results in the **Results** tab.

## Before you begin

To use natural language queries, ensure that:

- Genius Hub is installed and configured.
- At least one connected database is entitled to Genius Hub or Db2 AI Edition.
- The database that you want to query is registered in Genius Hub.
- A database connection profile exists in Db2 Developer Extension.

**Important:** Natural language queries are unavailable if Genius Hub is not installed or no eligible database connection exists.

## Connecting to Genius Hub

1. Open Db2 Developer Extension.
2. Click **Toggle Db2 AI Assistant** to open the **Db2 AI Assistant** view.
4. Enter the following information:
   - **Genius Hub URL**
   - **User ID**
   - **Password**
5. Click **Login to Genius Hub**.

   After the connection is established, the **Db2 AI Assistant** chat interface is displayed.

6. Ensure you have selected a database connection profile.
7. Enter your question in natural language. For example:

   ```
   List the top 10 customers by total sales in 2025
   ```

4. Press **Enter**.

   The extension:

   - Sends the request to Genius Hub.
   - Converts the natural language request into SQL.
   - Runs the generated SQL against the selected database.
   - Displays the results in the **Results** tab along with the SQL query.

