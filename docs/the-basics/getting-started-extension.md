

# Getting started 
---
This topic guides you through the initial setup, configuration, and basic usage of IBM Db2 Genius Code.

## Prerequisites
---
Before you begin, ensure that the following software is installed:

- Visual Studio Code version `1.103.0` or later
- Java Runtime Environment (JRE) version `17` or later


## Installing the Extension
---
1. Open **Visual Studio Code**.
2. Click **Extensions**.
3. Search for **IBM Db2 Genius Code**.
4. Select the extension and click **Install**.


The IBM Db2 Genius Code icon (![Db2 developer icon]({{site.baseurl}}/assets/images/genius-code.png){:width="25" :height="25"}) appears in the Activity Bar.


## Configuring IBM Db2 Genius Code
---
1. Open Visual Studio Code and click the gear icon (![gear icon]({{site.baseurl}}/assets/images/gear-icon.png){:width="25" :height="25"}) and then **Settings**.
2. Go to **Extensions** in the left sidebar and select **IBM Db2 Genius Code Settings**.
3. Configure the following settings as required:


   - **Db2 › Java: Home** (applies to all profiles)
     Path to the Java installation for the Db2 extension. This setting is optional. If not set, the extension uses the `JAVA_HOME` environment variable or the system PATH to locate Java. Set this if you have multiple JDKs installed and the extension is picking up the wrong version. Because this setting is independent of the system Java path, you can use a dedicated Java installation for the extension without changing your existing system configuration.
   - **Db2service: Max Rows**
     Set the maximum number of rows to fetch in query results (default is 1000).
   - **Db2service: Service Port**
     Enter the port number for the Db2 service (default is 9000).
   - **Db2service: Statement Terminator**
     Set the default statement terminator that is used to split SQL statements (default is a semicolon, `;`). You can override this setting for an individual file by adding `--#SET TERMINATOR <char>` to the file. For more information, see [Setting the statement terminator]({{site.baseurl}}/docs/working-with-sql/running-multiple-sql-statements#setting-the-sql-statement-terminator).
   - **Genius Hub: Allow Self Signed Certificate** (applies to all profiles)
     Allow self-signed TLS certificates when you connect to IBM Db2 Genius Hub. The extension automatically detects whether to allow self-signed certificates when you log in. Change this setting manually only if needed, for example, if your Genius Hub server uses a self-signed certificate.

## Using the onboarding experience
---

When you first open IBM Db2 Genius Code, the onboarding interface brings the important setup actions together in one place. Use it to explore the available setup options and to configure the extension for your requirements.

## Using the IBM Db2 Genius Code
---
When you open the Db2 Genius Code, you can see the **Db2 Connections** pane. 


**If you already have a Db2 instance**: 

Click **Add connection** button or **Add connection** icon (![Adding a database connection]({{site.baseurl}}/assets/images/add-database-connection.png){:width="25" :height="25"}) in the Db2 Connections pane and follow the steps [here](creating-a-database-connection.md#create-db-connection) to create a database connection.


**If you do not have a Db2 instance**: 

Click **Create Db2 instance** button or **Create Db2 instance** icon (![Creating new Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance.png){:width="25" :height="25"}) in the Db2 Connections pane and follow the steps [here]({{site.baseurl}}/docs/the-basics/creating-db2-instance) to create one.

   
   
   ![Creating Db2 instance]({{site.baseurl}}/assets/images/db2-developer-initial-screen.png){:width="300" :height="350"}

## Db2 Connections pane  
---

You can see the following icons on the **Db2 Connections** pane. 



| **Icon** | **Icon name** | **Description** |
|----------|------------|------------------|
|  ![Adding a database connection]({{site.baseurl}}/assets/images/add-database-connection.png){:width="25" :height="25"}| **Add connection** | Add a database connection. |
| ![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"} | **Open SQL Editor** | Open a new SQL Editor to write and run queries. |
| ![Refresh schema]({{site.baseurl}}/assets/images/refresh.png){:width="25" :height="25"} | **Refresh Db2 explorer** | Reload schemas and objects to reflect the latest changes. |
| ![Creating new SQL file]({{site.baseurl}}/assets/images/create-new-sql-file.png){:width="25" :height="25"} | **Create new SQL file** | Open a new editor tab where you can write and run SQL queries. |
| ![Creating new Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance.png){:width="25" :height="25"} | **Create Db2 instance** | Create a new Db2 instance by using the Community Edition license. After you create a new Db2 instance, the icon label automatically changes from **Create Db2 instance** to **Update Db2 instance**. |
| ![Collapse]({{site.baseurl}}/assets/images/collapse-all.png){:width="25" :height="25"} | **Collapse All** | Collapse all objects to return to a compact view. |

You can see the following icons on each database connection:


![connection toolbar]({{site.baseurl}}/assets/images/dbconnection-toolbar.png){:width="300" :height="200"}

| **Icon** | **Icon name** | **Description** |
|----------|------------|------------------|
|  ![Connecting to database]({{site.baseurl}}/assets/images/connect-database.png){:width="25" :height="25"}| **Connect** | Connect to a database. |
| ![Editing connection]({{site.baseurl}}/assets/images/edit-connection.png){:width="25" :height="25"} | **Edit connection** | Edit a database connection. |
| ![Delete connection]({{site.baseurl}}/assets/images/delete-connection.png){:width="25" :height="25"} | **Delete connection** | Delete a database connection. |
| ![Disconnect connection]({{site.baseurl}}/assets/images/disconnect.png){:width="25" :height="25"} | **Disconnect** | Disconnect a database connection. This icon will be visible only after connecting to the database. |





