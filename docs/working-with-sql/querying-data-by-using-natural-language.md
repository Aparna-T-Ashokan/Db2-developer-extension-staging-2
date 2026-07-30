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
2. Click **Toggle Db2 AI Assistant** icon ![Toggle Db2 AI Assistant]({{site.baseurl}}/assets/images/Toggle-db2-ai-assistant.png){:width="25" :height="25"} to open the **Db2 AI Assistant** view.
3. Enter the following information:
   - **Genius Hub URL**
   - **User ID**
   - **Password**
4. Click **Login to Genius Hub**.

   After the connection is established, the **Db2 AI Assistant** chat interface is displayed.

   ![Db2 AI Assistant chat interface]({{site.baseurl}}/assets/images/chat-window.png)

## Querying data

1. In the **Db2 AI Assistant** chat interface, click the **Choose Database** dropdown at the bottom and select the database.
2. Enter your question in natural language in the chat input. For example:

   ```
   List the top 10 customers by total sales in 2025
   ```

3. Press **Enter**.

   The extension:

   - Sends the request to Genius Hub.
   - Converts the natural language request into SQL.
   - Displays the **Generated SQL Query** in the **Db2 AI Assistant** panel.
   - Automatically populates the generated SQL into the **Db2 SQL Editor** and runs it.
   - Displays the results in the **Results** pane below the editor.
   - Saves the generated SQL query to **QUERY HISTORY**.


Click the **Conversation History** icon ![Open SQL Editor]({{site.baseurl}}/assets/images/conversation-history.png){:width="25" :height="25"} to see the **Conversation History** panel. It lists your previously asked questions.

The following actions are available for managing your conversations:

- **Search**: Use the search bar at the top of the **Conversation History** panel to find a specific conversation by keyword.
- **Rename**: Click rename ![Rename]({{site.baseurl}}/assets/images/rename.png){:width="25" :height="25"} next to a conversation entry to give it a custom name. In the **Rename Conversation** dialog, enter the new name and click **Rename**.
- **Bookmark**: Click bookmark ![Bookmark]({{site.baseurl}}/assets/images/bookmark.png){:width="25" :height="25"} next to a conversation to mark it for quick access later.
- **Filter**: Click filter ![Filter]({{site.baseurl}}/assets/images/filter.png){:width="25" :height="25"} to narrow down the conversation list by database. Select a database from the **Database** dropdown to show only conversations that were run against that database.

Click any conversation entry to reload it.

