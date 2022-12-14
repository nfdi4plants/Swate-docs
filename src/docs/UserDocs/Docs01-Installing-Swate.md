---
layout: docs
title: Installing Swate
published: 2022-09-19
Author: Kevin Frey
add toc: false
add sidebar: _sidebars\mainSidebar.md
---

1. [Quickstart in Browser](#quickstart)
2. [Desktop Installation](#desktop-installation)
4. [Manual Installation](#manual-installation)
3. [Using a shared folder as system admin](#using-a-shared-folder-as-system-admin)

## Quickstart

If you want to jump right into Swate and start testing the environment and features without much fuzz, we recommend using Swate in the Browser. This method uses the web version of Microsoft Excel which can be used for free with an free Microsoft account.

1. Download the latest [swate-b-quickstart.zip](https://github.com/nfdi4plants/Swate/releases)
2. Unzip (`Right click` â `Extract All..`)
3. Navigate to the web version of [Excel](https://office.live.com/start/excel.aspx) and log in. Starting this up for the first time might take a minute.
4. Open a (new) workbook, click `Insert` â `Office Add-ins`/`Add-ins` â `Upload My Add-in` and upload the `core_manifest.xml` from `swate-b-quickstart.zip`. 
5. Go to `Data` and you should see the Swate.Core add-in. If not you might need to click on the three dots on the right side to expand your available options. 
   
![Swate.Core Icon](https://raw.githubusercontent.com/nfdi4plants/Branding/master/icons/Swate/Excel/Core/swate_c_48x48.png)

6. Done! ð


## Desktop Installation

If you want to use Swate in your Excel desktop application, you can use the options below. If the provided installer does not work for you please try to use the [manual installation](#manual-installation).

â ï¸ **If you have an older Swate version installed already, it <u>might</u> be necessary to [clear the cache](https://docs.microsoft.com/de-de/office/dev/add-ins/testing/clear-cache#manually-clear-the-cache-in-excel-word-and-powerpoint) to apply the changes to Swate.**

- Download the [Windows Installer](https://github.com/nfdi4plants/Swate/blob/developer/.assets/swate-win.zip?raw=true). (MacOS-Installer coming soonâ¢)
- Close all Office instances (Excel, Powerpoint, Word, ...)
- Unzip (`Right click` â `Extract All..`)
- Double click the `install.cmd`. You will be asked to give administrative permissions and in the end to allow changes to the registry. Allow both and you are good to go!
- Open Excel, go to `Insert` â `My Add-ins` â `Shared Folder`. There you should see both `Swate` and `Swate.Experts`.

<details><summary>Alternative | Using the previous Swate installer</summary>
<p>

[Swate installer](https://github.com/omaus/Swate_Install#swate-installer)

</p>
</details>

<details><summary>Alternative | Using the release archive</summary>
<p>
    
â ï¸ This method might not be accessible anymore.

Using the release archive

- Install [node.js LTS](https://nodejs.org/en/) (needed for office addin related tooling)
- Download the [latest test release archive](https://github.com/nfdi4plants/Swate/releases) and extract it
- Execute the test.cmd (windows, as administrator) or test.sh (macOS, you will need to make it executable via chmod 
a+x) script.
  
</p>
</details>

## Manual Installation

Because of some legal roadblocks, we encountered as university trying to publish to the Excel add-in store, the current installer is far from perfect. Please use the below instructions to enable Swate for your Excel instance step-by-step.

1. Download the latest [Swate manifests](https://github.com/nfdi4plants/Swate/blob/developer/.assets/swate-win.zip?raw=true)
2. Follow the official microsoft docs to [sideload Swate in Excel](https://learn.microsoft.com/de-de/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins).
3. You will need to add the `core_manifest.xml` (and optionally the `experts_manifest.xml`) to your shared folder.

## Using a shared folder as system admin

If you have administrative access in your organization, you can create a network share folder and follow [this guide](https://github.com/OfficeDev/office-js-docs-pr/blob/master/docs/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins.md#:~:text=Sideload%20your%20add%2Din,-Put%20the%20manifest&text=Be%20sure%20to%20specify%20the,element%20of%20the%20manifest%20file.&text=In%20Excel%2C%20Word%2C%20or%20PowerPoint,Office%20Add%2Dins%20dialog%20box.) to make the addin available without any further downloads from your users.