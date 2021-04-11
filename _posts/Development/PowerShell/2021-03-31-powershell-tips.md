---
title: Powershell tips
date: 2020-10-29 11:30:00 HH:MM:SS +0100
categories: [Development, PowerShell]
tags: [development, powershell, tips]
---

### Change the console title

Very useful when there are many windows opened (or in a script):

```powershell
$title = "My new awesome title"
$host.UI.RawUI.WindowTitle = $title
```

### List profile files

`profile.ps1` is a pseudo equivalent of Linux's `.bashrc`.

### Add a permanent alias

Through the `profile.ps1`, example:

```powershell
Set-Alias ll Get-ChildItem
```
