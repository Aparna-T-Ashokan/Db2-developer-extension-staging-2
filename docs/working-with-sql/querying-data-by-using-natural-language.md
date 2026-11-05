# Querying data by using Genius AI

You can use Genius AI in Db2 Genius Code to ask questions about your data in plain English. The extension converts your request to SQL, runs the generated query against the selected database connection, and displays the results.

For example, instead of writing a SQL statement, you can enter:

```
Show all customers who placed orders in the last 30 days
```

The extension generates the SQL query, runs it against the selected database, and displays the results in the **Results** tab.

## Before you begin

To use Genius AI, ensure that:

- Genius Hub is installed and configured.
- At least one connected database is entitled to Genius Hub or Db2 AI Edition.
- The database that you want to query is registered in Genius Hub.
- A database connection profile exists in Db2 Genius Code.

**Important:** Genius AI is unavailable if Genius Hub is not installed or no eligible database connection exists.

## Connecting to Genius Hub

1. Open Db2 Genius Code.
2. Click **Toggle Genius AI** (![Toggle Genius AI]({{site.baseurl}}/assets/images/Toggle-db2-ai-assistant.png){:width="25" :height="25"}) to open the **Genius AI** panel.
3. Enter the following information:
   - **Genius Hub URL**
   - **Username**
   - **Password**
4. Click **Log in**.

   After the connection is established, the **Genius AI** chat interface is displayed with an **Open Genius Hub** button and a **Log out** link.

   ![Genius AI chat interface]({{site.baseurl}}/assets/images/chat-window.png){:width="400" :height="800"}

## Querying data

1. In the **Genius AI** chat interface, click the **Choose Database** dropdown at the bottom and select the database.
2. Enter your question in natural language. For example:

   ```
   List the top 10 customers by total sales in 2025
   ```

3. Press **Send**.

   The extension:

   - Sends the request to Genius Hub.
   - Converts the natural language request into SQL.
   - Displays the **Generated SQL Query** in the **Genius AI** panel.
   - Automatically populates the generated SQL into the **Db2 SQL Editor** and runs it.
   - Displays the results in the **Results** pane below the editor.
   - Saves the generated SQL query to **QUERY HISTORY**.

## Managing conversations

Click Conversation History icon (![Open SQL Editor]({{site.baseurl}}/assets/images/conversation-history.png){:width="25" :height="25"}) to see the **Conversation History** panel. It lists your previously asked questions.

The following actions are available for managing your conversations:

   - **Search**: Use the search bar at the top of the **Conversation History** panel to find a specific conversation by keyword.
   - **Rename**: Click rename (![Rename]({{site.baseurl}}/assets/images/rename.png){:width="25" :height="25"}) next to a conversation entry to give it a custom name. In the **Rename Conversation** dialog, enter the new name and click **Rename**.
   - **Bookmark**: Click bookmark (![Bookmark]({{site.baseurl}}/assets/images/bookmark.png){:width="25" :height="25"}) next to a conversation to mark it for quick access later.
   - **Filter**: Click filter (![Filter]({{site.baseurl}}/assets/images/filter.png){:width="25" :height="25"}) to narrow down the conversation list by database. Select a database from the **Choose Database** dropdown to show only conversations that were run against that database.

   Click any conversation entry to reload it.

## Searching the Db2 documentation

By default, deep search mode is enabled in the **Genius AI** chat panel. You can ask questions about Db2, for example, `What is a buffer pool?`. Genius AI provides an explanation along with supporting documentation sources, so you can find trusted information without leaving VS Code.

## Generating SQL from plain English

1. In the **Genius AI** chat panel, select a database.
2. Describe what you need in plain English. You can also enable **Generate SQL** mode or paste your query into the chat.

   Genius AI generates the SQL query and explains what it does.
3. Open the generated SQL in the editor, run it against your connected Db2 database, and view the results in VS Code.

## Resolving SQL errors

If a SQL statement returns an error, use **Resolve with Genius AI**. Genius AI explains the error, identifies the possible cause, and suggests ways to resolve it.

## Providing feedback

Use the feedback options in the **Genius AI** chat panel to provide feedback on Genius AI responses.

## Using slash commands

The slash commands menu provides quick access to Genius AI capabilities. The menu includes commands for the following tasks:

- Explain plan
- Optimize a slow query
- Compare schemas
- Investigate an error
- Performance analyzer
- DDL generation

## Explaining query plans

Genius AI can generate the execution plan for a query and show details such as the estimated cost and cardinality. It also explains potential performance issues, such as full table scans, and suggests areas for optimization.

For more detailed analysis, see [Analyzing query performance]({{site.baseurl}}/docs/working-with-sql/analyzing-query-performance).

## Generating DDL

How DDL generation works depends on whether you are logged in to Genius Hub:

- If you are logged in, Genius AI handles the DDL generation request and generates the DDL for the selected database object.
- If you are not logged in, DDL generation uses the previous workflow described in [Generating DDL for a Db2 object]({{site.baseurl}}/docs/the-basics/generating-ddl).

In both cases, DDL generation continues to work. For more information, see [Generating DDL for a Db2 object]({{site.baseurl}}/docs/the-basics/generating-ddl).

## Working with chat history

The selected database is fixed for each chat, so a conversation stays associated with the same database. To work with a different database, start a new chat and select that database.

To revisit earlier conversations, use the chat history. See [Managing conversations](#managing-conversations).

### Archiving and unarchiving conversations

You can archive conversations that you no longer need so that they do not appear in your active chat list.

- To view archived conversations, open the archived chat section.
- To continue an archived conversation, or to return it to your active chat list, use the **Unarchive** option.
