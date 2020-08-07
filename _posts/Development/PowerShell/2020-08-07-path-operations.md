---
title: Path operations
date: 2020-08-07 16:00:00 HH:MM:SS +0200
categories: [Development]
tags: [powershell]     # TAG names should always be lowercase
---

## Joining two paths
```powershell
$fullPath = Join-Path $basePath -ChildPath $childPath
$pipedFullPath = Join-Path $basePath -ChildPath $firstChildPath | Join-Path -Child-Path $secondChildPath
```