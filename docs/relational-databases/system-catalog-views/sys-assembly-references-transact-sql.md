---
title: sys.assembly_references (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- assembly_references
- sys.assembly_references_TSQL
- assembly_references_TSQL
- sys.assembly_references
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_references catalog view
ms.assetid: 50a5ed42-2d5b-4a11-a0d2-9a02241b078d
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a2a08a6c531ff91b12cbfae3a13b15c74484e2e0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sysassemblyreferences-transact-sql"></a>sys.assembly_references (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по строке для каждой пары сборок, где одна прямо ссылается на другую.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|Идентификатор сборки, которой принадлежит эта ссылка.|  
|**referenced_assembly_id**|**int**|Идентификатор сборки, на которую выполняется ссылка.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога сборки среды CLR &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ASSEMBLYPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
