---
title: "SQLProcedures | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
caps.latest.revision: "35"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 17ced2d525f863a6a24b1f4a7234cdd1312d7201
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="sqlprocedures"></a>SQLProcedures
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Все хранимые процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращают какое-либо значение. **SQLProcedures** сообщает значение SQL_PT_FUNCTION результирующего набора procedure_type.  
  
 **SQLProcedures** возвращает SQL_SUCCESS независимо от наличия значения существуют для *CatalogName, SchemaName* или *ProcName* параметров. Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 **SQLProcedures** может быть выполнена для статического серверного курсора. Попытка выполнить **SQLProcedures** для обновляемого (динамического или набора ключей) курсора будет возвращено значение SQL_SUCCESS_WITH_INFO, указывающее на то, что тип курсора был изменен.  
  
 **SQLProcedures** возвращает сведения обо всех процедурах, имена которых соответствуют *ProcName* и могут быть выполнены текущим пользователем или для которого текущий пользователь имеет разрешение VIEW DEFINITION.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLProcedures](http://go.microsoft.com/fwlink/?LinkId=59364)   
 [Сведения о реализации API-интерфейса ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
