# Using Genius AI

You can use Genius AI in Db2 Genius Code to ask questions about your data in plain English. Genius AI converts your request to SQL, runs the generated query against the selected database connection, and displays the results.

For example, instead of writing a SQL statement, you can enter:

```
Generate SQL Query for @ADNAAN.ACT

```

The Genius AI generates the SQL query, runs it against the selected database, and displays the results in the terminal.

## Before you begin

To use Genius AI, ensure that:

- Genius Hub is installed and configured.
- At least one connected database is entitled to Genius Hub.
- The database that you want to query is registered in Genius Hub.
- A database connection profile exists in Db2 Genius Code.

## Connecting to Genius Hub

To connect your workspace and enable Genius AI code assistance, log in to Genius Hub:

1. Open Db2 Genius Code.
2. In the **Account** section, enter the following information:
   - Genius Hub URL
   - Username
   - Password
3. Optional: Keep **Stay logged in** selected if you want to remain logged in.
4. Click **Log in**.

   After you log in, the **Account** section shows that you are logged in, with an **Open Genius Hub** button and a **Log out** link.

## Querying data

1. In the **Db2 Connections** pane, connect to the database that you want to query.

   When a database is selected, the **Toggle Genius AI** button (![Toggle Genius AI]({{site.baseurl}}/assets/images/Toggle-db2-ai-assistant.png){:width="25" :height="25"}) is displayed.

2. Click **Toggle Genius AI** to open the **Genius AI** chat panel. The database is not selected automatically when you log in. At the bottom of the panel, use the **Choose Database** dropdown to select the database that you want to query.

   ![Genius AI chat interface]({{site.baseurl}}/assets/images/genius-ai-chat.png){:width="300" :height="400"}

3. Enter your question in natural language. For example:

   ```
   Generate SQL Query for @ADNAAN.ACT

   ```

   **Note:** To generate a SQL query, you need to enable **Generate SQL** mode. At the bottom of the **Genius AI** chat panel, click the icon next to the database name, and then select **Generate SQL**. If the mode is not enabled, Genius AI asks you to enable it.

4. Click **Send**.

   The extension:

   - Sends the request to Genius Hub.
   - Converts the natural language request into SQL.
   - Displays the **Generated SQL Query** in the **Genius AI** chat.
   - Populates the generated SQL into the **Db2 SQL Editor** and runs it.
   - Displays the results in the terminal.
   - Saves the generated SQL query to **QUERY HISTORY**.

## Starting a new chat

The database that you select with **Choose Database** stays the same for the whole chat. To run queries against a different database, click the **New chat** icon (![new chat]({{site.baseurl}}/assets/images/new-chat.png){:width="25" :height="25"}) at the top of the **Genius AI** chat panel. Then, in the new chat, select the database that you want to query.


## Searching the Db2 documentation

By default, Doc Search mode is enabled in the **Genius AI** chat panel. You can ask questions about Db2, for example, `What is a buffer pool?`. Genius AI provides an explanation along with supporting documentation sources, so you can find trusted information without leaving VS Code.


## Resolving SQL errors

If a SQL statement returns an error, click **Resolve with Genius AI**. Genius AI explains the error, identifies the possible cause, and suggests ways to resolve it.


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
- If you are not logged in, DDL generation uses the Db2LOOK workflow described in [Generating DDL for a Db2 object]({{site.baseurl}}/docs/the-basics/generating-ddl).

In both cases, DDL generation continues to work. For more information, see [Generating DDL for a Db2 object]({{site.baseurl}}/docs/the-basics/generating-ddl).

## Viewing chat history

Click Chat History (![history]({{site.baseurl}}/assets/images/history-icon.png){:width="25" :height="25"}) in the **Genius AI** chat panel to see the **Chat History**. It lists your previously asked questions.

![Toggle Genius AI]({{site.baseurl}}/assets/images/conv-history.png){:width="400" :height="600"}

The following actions are available for managing your chats:

   - **Search**: Use the search bar at the top of the **Chat History** panel to find a specific chat by keyword.

   - **Archive** (![Archive]({{site.baseurl}}/assets/images/archive.png){:width="20" :height="20"}): Archive a chat to remove it from your active list. Click the archive icon to add the chat to the archive history. Click **Archived chats** to see all archived chats.

   - **Unarchive** (![Reload]({{site.baseurl}}/assets/images/reload.png){:width="20" :height="20"}): To restore an archived chat, click **Archived chats**, and then click the reload icon next to the chat to unarchive it. The chat returns to your active list in **Chat History**.

   Click any chat entry to reload it.

## Adding context with the @ Context Manager

Use the @ Context Manager to add database objects as context to your chat, so that Genius AI uses them in its responses.

1. In the chat input box, type `@`. The **Add context** list opens.
2. Browse the list, or type to search. The list contains a **Recent** section and the following database object categories, for example:
   - **Procedures**
   - **Functions**
   - **Aliases**
   - **Audit policies**
   - **Buffer pools**
   - **Check constraints**
   - **Indexes**
3. Expand a category, and then select the object that you want to add. To move through the list, use the up and down arrow keys. To select the highlighted item, press **Tab**.

The **Recent** section lists the items that you added as context before, so that you can add them again quickly.

For example, in the request `Generate SQL Query for @ADNAAN.ACT`, `@ADNAAN.ACT` adds the `ACT` table in the `ADNAAN` schema as context.


## Providing feedback

Use the feedback options in the **Genius AI** chat panel to provide feedback on Genius AI responses.

