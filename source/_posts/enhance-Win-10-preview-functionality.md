---
title: enhance Win 10 preview functionality
date: 2020-02-05 10:27:18
tags: Win, IT
---

To facilitate document content review, I opened Preview Pane in file explorer, but unfortuately, some regular document types for me cannot be recognized by Window. E.g. some source code files, such as `json`, `py`,etc. will get a blank preview window. 

To solve this problem, we should understand the concept: <a href="https://docs.microsoft.com/en-us/previous-versions/windows/desktop/legacy/cc144150(v=vs.85)">PerceivedType</a>, and then we can solve this issue manually.

So far, Windows support below PerceivedType:

* Folder
* Text
* Image
* Audio
* Video
* Compressed
* Document
* System
* Application
* Gamemedia
* Contacts

1. Open regeditor and open the root element: `HKEY_CLASSES_ROOT`. You can find the file extension name as a "folder" icon.
2. find the extension name you want to change, such as `.json`, and open it.
3. Add a new string key under it. The key name must be "PerceivedType" and the value can be any value in above enumeration. To preview the file as text, you can use "Text".

Then you can preview your plain text file in Preview pane. 
