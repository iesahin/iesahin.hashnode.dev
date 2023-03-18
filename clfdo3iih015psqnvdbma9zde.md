---
title: "bits 1"
datePublished: Tue Mar 14 2023 10:39:00 GMT+0000 (Coordinated Universal Time)
cuid: clfdo3iih015psqnvdbma9zde
slug: bits-1
canonical: https://emresahin.net/bits-1/

---

I began to explore the terrain for a Word plugin for the company I'm working.

*   Although there is a common format for the [manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/add-in-manifests?tabs=tabid-1) file, Outlook and Word addins seems to be required to have it separate. I didn't see any addin in [AppSource](https://appsource.microsoft.com/en-US/home?exp=ubp8) that's _both_ Word and _Excel_ addins.
*   There is a tool from Microsoft called [Script Lab](https://appsource.microsoft.com/en-us/product/office/WA104380862?corrid=94e8a3b6-7b45-7d61-7efa-2b5fb01abb83&src=office&exp=ubp8) that allows to run arbitrary scripts and testAPIs in Office.
*   For authentication, it's better to open a browser window to your web app via [Dialog API](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/dialog-api-in-office-add-ins)
*   It's usually not possible to use iframes to get authentication tokens from the taskbar/sidebar itself. See [this](https://stackoverflow.com/questions/67802639/outlook-web-addin-iframe-adfs-sites) answer.
*   It's possible to add elements to [right click menu](https://stackoverflow.com/questions/53844320/microsoft-word-add-in-add-to-contextual-menu) in Word for add-in commands.