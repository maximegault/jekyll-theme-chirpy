---
title: Generic informations
date: 2020-10-29 08:30:00 HH:MM:SS +0100
categories: [Development, T-SQL]
tags: [development, t-sql, sqlserver, database, column]
---

### List tables from the current database

Note that there is a lot of ways to achieve this.

```sql
SELECT * FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_TYPE = 'BASE TABLE'
```
