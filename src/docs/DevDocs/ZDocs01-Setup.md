---
layout: docs
title: Dev Setup
published: 2022-09-19
Author: Kevin Frey
add toc: false
add sidebar: _sidebars\mainSidebar.md
---

# Prerequisites

 - [.NET SDK](https://dotnet.microsoft.com/en-us/download/visual-studio-sdks) of at least the version in [the global.json file](global.json).
 - [Node.js](https://nodejs.org/en/) with npm included.
 - [Docker](https://www.docker.com/products/docker-desktop) with docker-compose.

# Install

To setup Swate you need to use the following commandline commands in the Swate root folder:

1. ```dotnet tool restore```
2. ```dotnet paket restore```
3. ```.\build.cmd setup```
    - This step requires further input from you, see:
        - [certificates-faq](#certificates)

# Run

Use the following fake target to start the application and make sure docker is running 🐳.

`.\build.cmd officedebug (--excel) (--open)`

This will start the Saturn backend server, the fable client, as well as a Neo4j database from the [docker-compose](https://github.com/nfdi4plants/Swate/blob/developer/.db/docker-compose.yml) file. 

You can add one or both option to automatically open the application.
- Use `--excel` to open an Excel application with Swate sideloaded.
- Use `--open` to open a Browser Windows on the Swate Url.

You can change the database setup in `.db/docker-compose.yml` and the related credentials in `src/Server/dev.json`.

Adminer can be accessed at localhost:8085, MySql at localhost:42333, and the app runs on http://localhost:5000 and is proxied to https://localhost:3000 with webpack.

# Debug

To debug add-in instances you can now easily open debug console/inspect for newer Excel versions. For Excel 2019 and earlier you can create a `.cmd` file with `C:\Windows\SysWOW64\F12\IEChooser.exe` to easily open the f12 tools (on windows). 

Alternatively use office online:
 - open Excel online in your favorite browser
 - Go to Insert > Office-Add-Ins and upload the manifest.xml file contained in this repo
 - You will now have the full debug experience in your browser dev tools.

# Contribute

Before you contribute to the project remember to return all placeholders to your project:

-   webpack.config.js    
    ```
    server: {
            type: 'https',
            options: {
                key: "{USERFOLDER}/.office-addin-dev-certs/localhost.key",
                cert: "{USERFOLDER}/.office-addin-dev-certs/localhost.crt",
                ca: "{USERFOLDER}/.office-addin-dev-certs/ca.crt"
            },
        },
    ```

# FAQ

## Certificates
Connections from excel to localhost need to be via https, so you need a certificate and trust it. [office-addin-dev-certs](https://www.npmjs.com/package/office-addin-dev-certs?activeTab=versions) does that for you.

You can also use the fake build target for certificate creation and installation by using `.\build.cmd createdevcerts` in the project root (after restoring tools via `dotnet tool restore`).

This will use office-addin-dev-certs to create the necessary certificates, and open the installation dialogue for you:

<p align="center">
<img src="images/DevDocs/install_certificate_window.jpg?v2022.03.11" height="300">
</p>

installing this ca certificate under your **trusted root certification** authorities will enable you to use https via localhost.

The paths to these certificates are then added to your webpack.config file.

## Loopback Exemption

You may need a loopback exemption for Edge/IE (whatever is run in your excel version): 

`CheckNetIsolation LoopbackExempt -a -n="microsoft.win32webviewhost_cw5n1h2txyewy"`