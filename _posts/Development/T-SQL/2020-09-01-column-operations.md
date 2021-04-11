---
title: Column operations
date: 2020-09-01 09:00:00 HH:MM:SS +0200
categories: [Development, T-SQL]
tags: [development, t-sql, sqlserver, database, column]
---

### Add a column to an existing table

```sql
ALTER TABLE [MySchema].[MyTable]
ADD [MyColumn] [bit] NULL
GO
```

### Drop a column from an existing table

```sql
-- Don't forget to drop constraints first if needed
ALTER TABLE [MySchema].[MyTable]
DROP COLUMN [MyColumn]
GO
```

### Example: create a bit column that needs to be non nullable and to have a default 0 value

```sql
-- The column needs to be nullable first
ALTER TABLE [MySchema].[MyTable]
ADD [MyColumn] [bit] NULL
GO

ALTER TABLE [MySchema].[MyTable] ADD CONSTRAINT [DF_MyTable_MyColumn] DEFAULT ((0)) FOR [MyColumn]
GO

-- We set a default value for the existing rows
UPDATE [MySchema].[MyTable]
   SET [MyColumn] = 0
GO

-- And finally set the column non nullable
ALTER TABLE [MySchema].[MyTable]
ALTER COLUMN [MyColumn] [bit] NOT NULL
GO
```
