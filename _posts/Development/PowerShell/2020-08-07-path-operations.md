---
title: Path operations
date: 2020-08-07 16:00:00 HH:MM:SS +0200
categories: [Development, PowerShell]
tags: [development, powershell]     # TAG names should always be lowercase
---

### Joining two paths

```powershell
$basePath = 'C:\foo'
$firstChildPath = 'bar'
$secondChildPath = 'baz'
$fullPath = Join-Path $basePath -ChildPath $firstChildPath
$pipedFullPath = Join-Path $basePath -ChildPath $firstChildPath | Join-Path -Child-Path $secondChildPath
# fullPath is 'C:\foo\bar'
# pipedFullPath is 'C:\foo\bar\baz'
```

### Get parent path

```powershell
$fullPath = 'C:\foo\bar\baz'
$parentPath = Split-Path $fullPath -Parent
$pipedParentPath = Split-Path $fullPath -Parent | Split-Path -Parent
# parentPath is 'C:\foo\bar'
# pipedParentPath is 'C:\foo'
```

### Get leaf

```powershell
$fullPath = 'C:\foo\bar\baz'
$leaf = Split-Path $fullPath -Leaf
# leaf is 'baz'
```

### Mix everything

```powershell
$fullPath = 'C:\foo\bar\baz'
$anotherLeaf = 'qux'
$mixedPipedPath = Split-Path $fullPath -Parent | Join-Path -Child-Path $anotherLeaf
# mixedPipedPath is 'C:\foo\bar\qux'
```
