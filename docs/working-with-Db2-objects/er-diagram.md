---
title: "Generating ER diagrams"
---

# {{ page.title }}


IBM Db2 Developer Extension allows you to generate entity-relationship (ER) diagrams directly from your database schemas or individual tables. ER diagrams provide a visual representation of table relationships and schema structures, making it easier to explore databases, understand dependencies, and document designs.

You can generate ER diagrams at two levels:
- **Table level**: Visualize the relationships for a single table.
- **Schema level**: Visualize all tables and their relationships within a schema.

## Generating an ER diagram for a table


1. In the **DB2 CONNECTIONS** pane, expand the database connection and navigate to the schema that contains the table.
2. Expand the **Tables** section and right-click the table name.
3. Select **View ER Diagram**.

The ER diagram opens in a new editor tab, showing the selected table and its relationships to other tables.

## Generating an ER diagram for a schema


1. In the **DB2 CONNECTIONS** pane, expand the database connection.
2. Right-click the schema name.
3. Select **View Schema ER Diagram**.

The ER diagram opens in a new editor tab, showing all tables in the schema and the relationships between them.

## Exporting an ER diagram


You can export an ER diagram in the following formats:

- **PNG**: Exports the diagram as an image, suitable for documentation and sharing.
- **JSON**: Exports the diagram data as a JSON file, suitable for further processing or reimporting.

To export a diagram, click **Export** in the ER diagram view and select the format you want.
