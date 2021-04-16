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

`profile.ps1` is a pseudo equivalent of Linux's `.bashrc`, it's user's specific configuration. It has different levels: to see all files:

```powershell
$PROFILE | Get-Member -MemberType noteproperty | Format-List
```

Output example:

```text
TypeName   : System.String
Name       : AllUsersAllHosts
MemberType : NoteProperty
Definition : string AllUsersAllHosts=C:\Windows\System32\WindowsPowerShell\v1.0\profile.ps1

TypeName   : System.String
Name       : AllUsersCurrentHost
MemberType : NoteProperty
Definition : string AllUsersCurrentHost=C:\Windows\System32\WindowsPowerShell\v1.0\Microsoft.PowerShell_profile.ps1

TypeName   : System.String
Name       : CurrentUserAllHosts
MemberType : NoteProperty
Definition : string CurrentUserAllHosts=C:\Users\myUser\Documents\WindowsPowerShell\profile.ps1

TypeName   : System.String
Name       : CurrentUserCurrentHost
MemberType : NoteProperty
Definition : string CurrentUserCurrentHost=C:\Users\myUser\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```

### Add a permanent alias

Through the `profile.ps1`, example:

```powershell
Set-Alias ll Get-ChildItem
```
