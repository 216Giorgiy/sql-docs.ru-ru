---
title: CONSTRAINT_TABLE_USAGE (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-information-schema-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CONSTRAINT_TABLE_USAGE_TSQL
- CONSTRAINT_TABLE_USAGE
dev_langs:
- TSQL
helpviewer_keywords:
- CONSTRAINT_TABLE_USAGE view
- INFORMATION_SCHEMA.CONSTRAINT_TABLE_USAGE view
ms.assetid: 5770b696-6c04-4d5c-a8db-9eb92022fa42
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d4b1c05a7d30e6671995f34f621668a61d16c310
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="constrainttableusage-transact-sql"></a>CONSTRAINT_TABLE_USAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает по строке для каждой из таблиц текущей базы данных, в которых определено ограничение. Это представление информационной схемы возвращает сведения об объектах, на которые у текущего пользователя есть разрешения.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA. *** view_name*.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**ЗНАЧЕНИЯМ TABLE_CATALOG**|**nvarchar (**128**)**|Квалификатор таблицы.|  
|**TABLE_SCHEMA**|**nvarchar (**128**)**|Имя схемы, содержащей таблицу.<br /><br /> **\*\* Важные \* \***  не используйте представления INFORMATION_SCHEMA, чтобы определить схему объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**ИМЯ_ТАБЛИЦЫ**|**sysname**|Имя таблицы.|  
|**CONSTRAINT_CATALOG**|**nvarchar (**128**)**|Квалификатор ограничения.|  
|**CONSTRAINT_SCHEMA**|**nvarchar (**128**)**|Имя схемы, содержащей ограничение.<br /><br /> **\*\* Важные \* \***  не используйте представления INFORMATION_SCHEMA, чтобы определить схему объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**CONSTRAINT_NAME**|**sysname**|Имя ограничения.|  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.CHECK_CONSTRAINTS &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)   
 [sys.key_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [sys.foreign_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-foreign-keys-transact-sql.md)  
  
  
