---
title: "Поддержка управляющих объектов SQL Server для выполняющейся в памяти OLTP | Документация Майкрософт"
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b67292d-6d8e-4016-9063-a97461ffe57a
caps.latest.revision: 28
author: JennieHubbard
ms.author: genemi
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: f97c2335abf293f70fad454ac9f181a3cb3e439c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/17/2017

---
# <a name="sql-server-management-objects-support-for-in-memory-oltp"></a>Поддержка управляющих объектов SQL Server SMO для In-Memory OLTP

В этом разделе описаны изменения управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SMO) для OLTP в памяти.  
  
Следующие типы и члены поддерживают OLTP в памяти.  
  
- Microsoft.SqlServer.Management.Smo.**<xref:Microsoft.SqlServer.Management.Smo.DurabilityType>** (перечисление)

- Microsoft.SqlServer.Management.Smo.FileGroup.**<xref:Microsoft.SqlServer.Management.Smo.FileGroup.FileGroupType%2A>** (свойство)

- Microsoft.SqlServer.Management.Smo.FileGroup.**<xref:Microsoft.SqlServer.Management.Smo.FileGroup.%23ctor%2A>** (конструктор)

- Microsoft.SqlServer.Management.Smo.**<xref:Microsoft.SqlServer.Management.Smo.FileGroupType>** (перечисление)

- Microsoft.SqlServer.Management.Smo.Index.**<xref:Microsoft.SqlServer.Management.Smo.Index.BucketCount%2A>** (свойство)

- Microsoft.SqlServer.Management.Smo.IndexType.**<xref:Microsoft.SqlServer.Management.Smo.IndexType.NonClusteredHashIndex>** (номер перечисления)

- Microsoft.SqlServer.Management.Smo.Index.**<xref:Microsoft.SqlServer.Management.Smo.Index.IsMemoryOptimized%2A>** (свойство)

- Microsoft.SqlServer.Management.Smo.Server.**<xref:Microsoft.SqlServer.Management.Smo.Server.IsXTPSupported%2A>** (свойство)

- Microsoft.SqlServer.Management.Smo.StoredProcedure.**<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.IsNativelyCompiled%2A>** (свойство)

- Microsoft.SqlServer.Management.Smo.StoredProcedure.**<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.IsSchemaBound%2A>** (свойство)

- Microsoft.SqlServer.Management.Smo.Table.**<xref:Microsoft.SqlServer.Management.Smo.Table.Durability%2A>** (свойство)

- Microsoft.SqlServer.Management.Smo.Table.**<xref:Microsoft.SqlServer.Management.Smo.Table.IsMemoryOptimized%2A>** (свойство)

- Microsoft.SqlServer.Management.Smo.UserDefinedTableType.**<xref:Microsoft.SqlServer.Management.Smo.UserDefinedTableType.IsMemoryOptimized%2A>** (свойство)

## <a name="code-sample"></a>Образец кода

#### <a name="actions-taken-in-the-code-example"></a>Действия, выполняемые в примере кода
  
-   Создание базы данных с оптимизированной для памяти файловой группой и оптимизированным для памяти файлом.  
  
-   Создание оптимизированной для памяти таблицу с первичным ключом, некластеризованным индексом и некластеризованным хэш-индексом.  
  
-   Создание столбцов и индексов.  
  
-   Создание оптимизированного для памяти пользовательского табличного типа.  
  
-   Создание скомпилированной в собственном коде хранимой процедуры.

#### <a name="assemblies-referenced-by-the-compiled-code-example"></a>Сборки, на которые указывают ссылки в примере скомпилированного кода

- Microsoft.SqlServer.ConnectionInfo.dll
- Microsoft.SqlServer.Management.Sdk.Sfc.dll
- Microsoft.SqlServer.Smo.dll
- Microsoft.SqlServer.SqlEnum.dll

#### <a name="source-code"></a>Исходный код
  
```csharp
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
public class A {  
   static void Main(string[] args) {  
      Server server = new Server("(local)");  
  
      // Create a database with memory-optimized filegroup and memory-optimized file.
      Database db = new Database(server, "MemoryOptimizedDatabase");  
      db.Create();  
      FileGroup fg = new FileGroup(
         db,
         "memOptFilegroup",
         FileGroupType.MemoryOptimizedDataFileGroup);  
      db.FileGroups.Add(fg);  
      fg.Create();  
      // Change this path if needed.
      DataFile file = new DataFile(
         fg,
         "memOptFile",
         @"C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\MSSQLmemOptFileName");  
      file.Create();  
  
      // Create a durable memory-optimized table with primary key, nonclustered index and nonclustered hash index.
      // Define the table as memory optimized and set the durability.
      Table table = new Table(db, "memOptTable");  
      table.IsMemoryOptimized = true;  
      table.Durability = DurabilityType.SchemaAndData;  
  
      // Create columns.
      Column col1 = new Column(table, "col1", DataType.Int);  
      col1.Nullable = false;  
      table.Columns.Add(col1);  
      Column col2 = new Column(table, "col2", DataType.Float);  
      col2.Nullable = false;  
      table.Columns.Add(col2);  
      Column col3 = new Column(table, "col3", DataType.Decimal(2, 10));  
      col3.Nullable = false;  
      table.Columns.Add(col3);  
  
      // Create indexes.
      Index pk = new Index(table, "PK_memOptTable");  
      pk.IndexType = IndexType.NonClusteredIndex;  
      pk.IndexKeyType = IndexKeyType.DriPrimaryKey;  
      pk.IndexedColumns.Add(new IndexedColumn(pk, col1.Name));  
      table.Indexes.Add(pk);  
  
      Index ixNonClustered = new Index(table, "ix_nonClustered");  
      ixNonClustered.IndexType = IndexType.NonClusteredIndex;  
      ixNonClustered.IndexKeyType = IndexKeyType.None;  
      ixNonClustered.IndexedColumns.Add(
         new IndexedColumn(ixNonClustered, col2.Name));  
      table.Indexes.Add(ixNonClustered);  
  
      Index ixNonClusteredHash = new Index(table, "ix_nonClustered_Hash");  
      ixNonClusteredHash.IndexType = IndexType.NonClusteredHashIndex;  
      ixNonClusteredHash.IndexKeyType = IndexKeyType.None;  
      ixNonClusteredHash.BucketCount = 1024;  
      ixNonClusteredHash.IndexedColumns.Add(
         new IndexedColumn(ixNonClusteredHash, col3.Name));  
      table.Indexes.Add(ixNonClusteredHash);  
  
      table.Create();  
  
      // Create a user-defined memory-optimized table type.
      UserDefinedTableType uDTT = new UserDefinedTableType(db, "memOptUDTT");  
      uDTT.IsMemoryOptimized = true;  
  
      // Add columns.
      Column udTTCol1 = new Column(uDTT, "udtCol1", DataType.Int);  
      udTTCol1.Nullable = false;  
      uDTT.Columns.Add(udTTCol1);  
      Column udTTCol2 = new Column(uDTT, "udtCol2", DataType.Float);  
      udTTCol2.Nullable = false;  
      uDTT.Columns.Add(udTTCol2);  
      Column udTTCol3 = new Column(uDTT, "udtCol3", DataType.Decimal(2, 10));  
      udTTCol3.Nullable = false;  
      uDTT.Columns.Add(udTTCol3);  
  
      // Add index.
      Index ix = new Index(uDTT, "IX_UDT");  
      ix.IndexType = IndexType.NonClusteredHashIndex;  
      ix.BucketCount = 1024;  
      ix.IndexKeyType = IndexKeyType.DriPrimaryKey;  
      ix.IndexedColumns.Add(new IndexedColumn(ix, udTTCol1.Name));  
      uDTT.Indexes.Add(ix);  
  
      uDTT.Create();  
  
      // Create a natively compiled stored procedure.
      StoredProcedure sProc = new StoredProcedure(db, "nCSProc");  
      sProc.TextMode = false;  
      sProc.TextBody = "--Type body here";  
      sProc.IsNativelyCompiled = true;  
      sProc.IsSchemaBound = true;  
      sProc.ExecutionContext = ExecutionContext.Owner;  
      sProc.Create();  
   }  
}  
```  
  
## <a name="see-also"></a>См. также:  

[Поддержка SQL Server для In-Memory OLTP](sql-server-support-for-in-memory-oltp.md)

