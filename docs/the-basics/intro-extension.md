
# Introduction

<!--Bringing database development into the modern era
---The **Db2 Genius Code** is a comprehensive, feature-rich development tool designed to enable seamless interaction with IBM Db2 databases running on Linux, Unix, and Windows systems. Built for developers and database administrators, this extension integrates the power of Db2 directly into the Visual Studio Code environment, streamlining database operations, improving query development efficiency, and enhancing overall productivity.

With intuitive tools for managing connections, exploring schemas, executing SQL queries, and generating code, it simplifies the entire workflow of working with Db2 databases.
Db2 Genius Code: The Future of Database Development
The Db2 Genius Code transforms the way you work with IBM Db2 by bringing the entire database development experience into Visual Studio Code. No more juggling multiple tools, struggling with SSL configurations, or losing time to fragmented workflows. This extension delivers a unified, intuitive environment where you can manage connections, explore schemas, write and execute SQL, and debug procedures—all without leaving your editor.
Built for developers and database administrators, it combines speed, simplicity, and enterprise-grade security. With guided setup, smart code suggestions, persistent query history, and powerful visualization tools, you can resolve issues faster, optimize performance, and collaborate seamlessly across teams. Unlike generic database tools, the Db2 Genius Code is purpose-built for Db2, ensuring deep integration, advanced features, and future-ready capabilities like AI-driven query optimization.
If you want to save hours every week, eliminate complexity, and modernize your workflow, the Db2 Genius Code is the tool that makes database development effortless, efficient, and intelligent.-->

IBM Db2 Genius Code integrates Db2 database development directly into Visual Studio Code (VS Code), enabling developers to do a wide range of tasks without switching tools.

Designed for developers, this extension delivers a unified, intuitive environment where you can manage database connections, explore schemas, and write and run SQL. 


## Key features

### Db2 Community Edition

- Supports multiple container runtimes: Docker, Podman, and Colima, giving you flexibility to use whichever runtime is available on your system.

### Genius AI
- Ask Db2 questions and get answers with supporting documentation sources, without leaving VS Code.
- Generate SQL from plain English, open it in the editor, and run it against your connected database.
- Resolve SQL errors with explanations, possible causes, and suggested fixes.
- Analyze query performance with explain plans, execution diagrams, statistics, and index recommendations.
- Use slash commands for quick access to capabilities such as explain plan, query optimization, schema comparison, and error investigation.
- Revisit, archive, and unarchive previous chats.
- View historical table data by using Db2 Time Machine.

### Database connection management
- Create, edit, and delete secure connection profiles.
- Maintain multiple active database connections simultaneously.
- Store credentials securely using VS Code's SecretStorage API.
- Bidirectional JDBC URL parsing: auto-generates the connection URL from individual fields and populates fields from a pasted JDBC URL.
- Add custom JDBC connection properties to fine-tune your connections.

### Powerful unified SQL editor
- Run queries in dedicated transactional sessions, ensuring isolation between SQL editor tabs and connections.
- Transactional query support: execute `BEGIN TRANSACTION`, `ROLLBACK`, `COMMIT`, and `END TRANSACTION` statements within a single editor session.
- Write and run multiple queries simultaneously.
- Keyword and template suggestions for faster query authoring.
- Consistent SQL syntax highlighting: keywords, data types, strings, and comments are rendered in the same colors across all SQL file types.
- Signature help for correct parameter usage.
- Cancel long-running queries without closing the connection.
- Set your default statement terminator in the VS Code settings, and override it for individual files.

### Query running and visualization
- Run queries directly within VS Code.
- View results instantly in tabular format with streaming support for large result sets.
- Open results in the data viewer, copy data, and visualize results as bar, line, area, pie, or scatter charts.
- Rearrange and sort columns in the results table.

- Export results to CSV and JSON with one click.
- Export table and schema data directly from the extension.
- Replicate data between schemas without leaving VS Code.
- Query history with timestamps, preserved across VS Code sessions even after you close and reopen VS Code.

### Database explorer with tree view
- Browse schemas, tables, views, procedures, and other objects in a clean tree structure.
- View check constraints on table objects.
- Support for table and object names that contain special characters.
- View LOB data (CLOB, BLOB, DBCLOB, XML, Binary, Spatial, Vector Embeddings, Metadata, and more) directly in the LOB Viewer.
- Filter database objects to find the items you need quickly.
- View ER diagrams, search for tables, change the layout, add columns from the diagram, and export diagrams as PNG images.
- Right-click objects for instant access to common operations.

<!--
Code generation and snippets
- Generate embedded SQL code for applications.
- Access ready-made templates for common Db2 tasks.
- Intelligent snippet suggestions for faster coding.-->

