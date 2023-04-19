---
title: "Is it possible to combine Word and Outlook add-ins?"
datePublished: Tue Mar 21 2023 21:04:00 GMT+0000 (Coordinated Universal Time)
cuid: clgngomjh00qu36nvgvtq163d
slug: is-it-possible-to-combine-word-and-outlook-add-ins
canonical: https://emresahin.net/is-it-possible-to-combine-word-and-outlook-add-ins/

---

We're currently working on a Microsoft Word add-in in my day job. The company already has an Outlook add-in and they wanted to use the same manifest file for the Word add-in. [The manifest files](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/add-in-manifests?tabs=tabid-1#required-elements-by-office-add-in-type) have some keys that look similar. Actually, most of the content seems similar, but it's not possible to merge these two.

There are three types of Office add-ins: Task pane, Content and Mail. These have different schema definitions at the top of the file. So it's not possible to combine these three different types of Office add-ins. If an add-in needs mail permissions, it cannot work in Word, and if it requires document permissions, it cannot work in Outlook.