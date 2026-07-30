---
title: "Creating a Db2 instance by using Community Edition"
---

# {{ page.title }} {#create-db2-instance-id}
---

> **Note**:
> Skip this procedure if you already have a Db2 Community Edition instance.
{: .note-right}

## Overview

The IBM Db2 Developer Extension can automatically provision a fully functional Db2 Community Edition instance on your local machine. The extension installs any required container runtime (if needed), deploys Db2 inside a container, creates the requested databases, and automatically registers database connections in the extension.

No manual container commands or environment configuration are required.

## Prerequisites

Before creating a Db2 instance, ensure the following requirements are met.

#### All platforms

- Visual Studio Code is installed.
- An active internet connection is available to download the Db2 Community Edition container image.
- At least 4 GB of available RAM.
- Sufficient free disk space for the Db2 container image and databases.

#### Windows

- Windows Subsystem for Linux (WSL2) is installed.
- A supported Linux distribution (such as Ubuntu) is configured.
- WSL2 is set as the default version.

> **Note**: The Db2 Developer Extension supports Db2 Community Edition installation only inside WSL2.
>
> If WSL2 or a Linux distribution is not detected, the extension displays a warning with a **View Installation Guide** button that opens the Microsoft WSL2 documentation. The extension does not install WSL2 itself — WSL2 must be set up manually before using the **Create Db2 Instance** feature.
{: .note-right}

If WSL2 is not already configured, see [Setting up WSL2 (Windows only)](#setting-up-wsl2-windows-only) below.

#### macOS

No additional software is required before starting. If Homebrew is not installed, the extension installs it automatically after requesting your permission.

#### Setting up WSL2 (Windows only)

If WSL2 is not already configured on your system, complete the following steps before creating a Db2 Community Edition instance.

**System requirements**

Ensure that your Windows system meets the following requirements:

- Windows 10 or Windows 11 with administrator privileges.
- Virtualization enabled in the BIOS.
- Visual Studio Code installed.

**1. Enable and update WSL2**

a. Open Windows PowerShell as an administrator.

b. (Optional) If WSL is not already installed, install the WSL2 kernel update:

```
curl.exe -L -o wsl_update_x64.msi https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
msiexec /i wsl_update_x64.msi /quiet /norestart
```

c. Set WSL2 as the default version:

```
wsl --set-default-version 2
```

d. Update WSL:
{: #step-1d}

```
wsl --update
```

**2. Install Ubuntu**

> **Note**: The `wsl --install Ubuntu` command might fail if WSL has not been updated. Complete [Step 1d](#step-1d) before continuing.
{: .note-right}

a. Install Ubuntu:

```
wsl --install Ubuntu
```

b. When Ubuntu starts for the first time, create your Linux user account and password.

**3. Configure Ubuntu as the default distribution**

a. Set Ubuntu as the default WSL distribution (replace `Ubuntu` with your installed distribution name if different):

```
wsl --set-default Ubuntu
```

b. Restart your system.

c. Launch WSL:

```
wsl
```

d. Verify that you are in your Ubuntu home directory:

```
pwd
```

Expected output: `/home/<username>`

After WSL2 is configured, return to Visual Studio Code and use the **Create Db2 Instance** option in the **DB2 CONNECTIONS** view. The Db2 Developer Extension automatically detects the WSL2 environment and performs the remaining installation and configuration steps, including installing the container runtime (Podman or Docker) inside WSL2.

## Required permissions

Some installation steps may require administrator (`sudo`) privileges depending on your operating system and environment.

Whenever elevated permissions are required, the extension uses one of two mechanisms:

- **VS Code modal dialog**: Shown for decisions such as approving corrupted-runtime cleanup or selecting an alternative port. You confirm or cancel directly inside VS Code before the operation proceeds.
- **Terminal (sudo) prompt**: Shown inside the Db2 Community terminal panel when a shell script requires elevated privileges (for example, during container runtime installation on Linux/WSL2). You enter your system password in the terminal when prompted.

No privileged operations are performed without user consent.

## Supported container runtimes

The extension automatically detects and selects the most suitable container runtime in the following order:

1. Podman (preferred)
2. Docker
3. Colima (macOS only)

If none of the supported runtimes are available, the extension automatically installs one.

## Procedure

To create a Db2 instance by using IBM Db2 Community Edition, complete the following steps:

1. In the **DB2 CONNECTIONS** view, click the **Create Db2 instance** button or the **Create Db2 Instance** icon ![Creating new Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance.png){:width="25" :height="25"}.

   - If an existing Db2 Community Edition instance is detected, the **Update Db2 Instance** page opens.
   - Otherwise, the **Create Db2 Instance** page opens.

2. Enter the required information:

   ![Creating Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance-window.png)

   - **Host**: Hostname or IP address that hosts the instance.
   - **Port**: Internal Docker port number (between 1 and 65535) for the instance.
   - **Username**: Username for accessing the instance. The username is automatically converted to lowercase.
   - **Password**: Password for accessing the instance.
   - **Database Name**: Name of the database that you want to create. By default, the database name is set to `TESTDB`.

3. Click **Create Db2 instance**.

   If the port you specified is already in use on your machine, a dialog appears offering an alternative available port. You can accept the suggested port or cancel to enter a different one manually.

4. The extension automatically performs the following setup process. Progress is displayed in real time through the setup progress panel.

   a. Detects the operating system and architecture.

   b. Detects available container runtimes.

   c. Starts and validates the selected runtime. (Skipped if no runtime is found — see step e.)

   d. Checks for an existing Db2 Community Edition instance. (Only runs if a healthy runtime exists.)

   e. Installs a supported container runtime if one is not available. (Skipped if a healthy runtime was already found in step b.)

   f. Downloads and installs Db2 Community Edition.

   g. Creates the requested database.

   h. Creates the `SAMPLE` database.

   i. Verifies database connectivity.

   j. Registers database connection profiles in the extension.

5. When setup completes successfully:

   - The requested database and `SAMPLE` database are available.
   - Connection profiles are created automatically and displayed in the **DB2 CONNECTIONS** view.
   - The **Update Db2 Instance** page opens.

   > **Note**: If you prefer to install Db2 Community Edition manually, see [Installing Db2 Community Edition manually]({{site.baseurl}}/docs/tips-and-tricks/manual-db2-installation).
   {: .note-right}

## Automatic runtime installation

If no supported container runtime is detected, the extension installs one automatically. Depending on the operating system, the extension may install:

| Platform | Automatically installed |
|----------|------------------------|
| macOS | Homebrew (if required), then Podman, Docker, or Colima |
| Linux | Podman or Docker |
| WSL2 | Podman or Docker inside WSL2 |

Administrator privileges may be required during installation.

## Databases created

During setup, the extension creates:

- Your specified database (default: `TESTDB`)
- `SAMPLE` database

Connection profiles for both databases are automatically created and displayed in the **DB2 CONNECTIONS** view.

## Installation time

Installation time depends on your internet connection and system performance. Typical installation times are:

| Platform | Estimated time |
|----------|---------------|
| macOS | 15–20 minutes |
| Linux / WSL2 | 10–15 minutes |

## Notes

- Installation requires an internet connection to download the Db2 Community Edition container image.
- The extension displays installation progress throughout the setup process.
- You may be prompted for administrator (`sudo`) privileges when required — either via a VS Code dialog or directly in the terminal.
- Existing Db2 Community Edition instances are detected automatically and reused whenever possible.
- **Windows only**: WSL2 must be installed and configured before using this feature. The extension detects missing WSL2 and provides a link to the Microsoft installation guide, but does not install WSL2 itself.


## What's next
---

After successfully creating your Db2 instance, you can:

- **[Create a database connection]({{site.baseurl}}/docs/the-basics/creating-a-database-connection#create-db-connection)**

- **[Manage your Db2 instance]({{site.baseurl}}/docs/the-basics/creating-a-database-connection#managing-db2-instance)**

- **[Explore Db2 objects]({{site.baseurl}}/docs/the-basics/Exploring-Db2-objects)**


For troubleshooting assistance, see [Db2 instance creation errors]({{site.baseurl}}/docs/troubleshooting/db2-instance-creation-errors).
