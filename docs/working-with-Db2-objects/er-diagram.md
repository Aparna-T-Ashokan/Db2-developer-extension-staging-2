---
title: "Viewing ER diagrams"
---

# {{ page.title }}


IBM Db2 Genius Code allows you to generate entity-relationship (ER) diagrams directly from your database schemas or individual tables. ER diagrams provide a visual representation of table relationships and schema structures, making it easier to explore databases, understand dependencies, and document designs.

You can generate ER diagrams at two levels:
- **Table level**: Visualize the relationships for a single table.
- **Schema level**: Visualize all tables and their relationships within a schema.

## Generating an ER diagram for a table


1. In the **Db2 Connections** pane, expand the database connection and navigate to the schema that contains the table.
2. Expand the **Tables** section and right-click the table name.
3. Select **View ER Diagram**.

The ER diagram opens in a new editor tab, showing the selected table and its relationships to other tables.

![ER diagram]({{site.baseurl}}/assets/images/ER-diagram.png)

Each table in the diagram displays the column names and their data types. Click **Show all columns** to expand a table and view all of its columns. You can also drag tables to rearrange them in the diagram canvas.

## Generating an ER diagram for a schema


1. In the **Db2 Connections** pane, expand the database connection.
2. Right-click the schema name.
3. Select **View Schema ER Diagram**.

The ER diagram opens in a new editor tab, showing all tables in the schema and the relationships between them.

## Viewing relationships

The diagram displays relationships between tables, including weak relationships where applicable. These visual connections help you understand dependencies between tables without having to inspect every relationship manually.

## Changing the diagram layout

Use the layout control to switch between horizontal and vertical arrangements. Choose the layout that best suits your schema and makes the relationships between tables easier to follow.

## Searching for a table in the diagram

When a schema contains many tables, use the search option to find a particular table.

1. Click the search option in the ER diagram view.
2. Enter the name of the table that you want to find (for example, `Product`).

   The matching table is highlighted in blue in the diagram.

## Modifying a table from the diagram

You can add a column to a table directly from the diagram.

1. In the diagram, use the editing functionality to add a new column to the table.

   The extension generates the SQL statement for the proposed change.
2. Review the generated SQL.
3. Select one of the following options:
   - **Open SQL editor**: Opens the SQL in the SQL editor.
   - **Copy SQL**: Copies the SQL to the clipboard.
   - **Cancel**: Closes the dialog without making the change.
   - **Run** or **Apply**: Runs the SQL to apply the change to the database.

## Exporting an ER diagram


You can export an ER diagram in the following formats:

- **PNG**: Exports the diagram as an image, suitable for documentation and sharing.
- **JSON**: Exports the diagram data as a JSON file, suitable for further processing or reimporting.

To export a diagram, click **Export** in the ER diagram view and select the format you want.

When you export a diagram as a PNG image, a dialog box prompts you for the name of the exported file. Enter the file name and confirm the export.
