---
title: "Open Windows Terminal here"
date: 2020-08-07T22:39:00+01:00
# post thumb
images:
  - "images/post/wt_context_menu/thumb.webp"
author: "Hauke Jung"
description: "Learn how to open Windows Terminal with right click context menu."
categories: ["open source", "windows"]
tags: ["windows terminal"]
draft: false
---

The new Windows terminal (wt.exe) is very useful. At the moment i use it as my default terminal. It annoys me that there is currently no official way to start it directly from the right click context menu. So I want to show you how I solved this problem for me.

### Adding Windows Terminal to the context menu

1. Download the offical terminal icon from [https://raw.githubusercontent.com/microsoft/terminal/master/res/](https://raw.githubusercontent.com/microsoft/terminal/master/res/)
1. Save the icon at "%USERPROFILE%\\AppData\\Local\\wt\\terminal.ico"
1. Create a wt.reg file with the following content.
    ```reg
    Windows Registry Editor Version 5.00

    [HKEY_CLASSES_ROOT\Directory\Background\shell\wt]
    @="Open Windows terminal here"
    "Icon"="%USERPROFILE%\\AppData\\Local\\wt\\terminal.ico"

    [HKEY_CLASSES_ROOT\Directory\Background\shell\wt\command]
    @="wt.exe -d ."
    ```
1. Execute the file with **Right-Click->Merge**.
1. Finally, your context menu should look like this.

    <img src="../../images/post/wt_context_menu/open_wt_here.webp" title="Open Windows terminal here" alt="Open Windows terminal here" width="250"/>

{{< notice "info" >}}
  Tested with Windows Terminal Preview 1.2022.0
{{< /notice >}}

#### Exception handling

1. If the following error occurs it might help if you switch to the preview version.

    ![Access error](../../images/post/wt_context_menu/access_error.webp "Access error")

1. Once windows terminal preview is installed, you can open the **Manage app execution aliases** settings and switch to the preview version.

    ![App execution alias](../../images/post/wt_context_menu/app_execution_alias.webp "App execution alias")


