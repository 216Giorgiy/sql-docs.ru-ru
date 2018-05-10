---
title: DATEFROMPARTS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATEFROMPARTS_TSQL
- DATEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATEFROMPARTS function
ms.assetid: 5b885376-87aa-41f1-9e18-04987aead250
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d74e96029a7f28e6547c74c34bc5de9e0b656d8d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="datefromparts-transact-sql"></a>DATEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Возвращает значение **date**, соответствующее указанному числу, месяцу и году.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATEFROMPARTS ( year, month, day )  
```  
  
## <a name="arguments"></a>Аргументы  
*year*  
Целочисленное выражение, задающее год.
  
*month*  
Целочисленное выражение от 1 до 12, задающее месяц.
  
*day*  
Целочисленное выражение, задающее день.
  
## <a name="return-types"></a>Типы возвращаемых данных
**date**
  
## <a name="remarks"></a>Remarks  
**DATEFROMPARTS** возвращает значение **date**, в котором часть даты установлена в указанные число, месяц и год, а часть времени установлена в значение по умолчанию. Если аргументы недопустимы, то возникает ошибка. Если требуемые аргументы имеют значение NULL, возвращается NULL.
  
Для серверов [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и выше данная функция может быть удаленной. Данная функция не может быть удаленной для серверов с версией ниже [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].
  
## <a name="examples"></a>Примеры  
В приведенном ниже примере показано использование функции **DATEFROMPARTS**.
  
```sql
SELECT DATEFROMPARTS ( 2010, 12, 31 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
----------------------------------  
2010-12-31  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также раздел
[date &#40;Transact-SQL&#41;](../../t-sql/data-types/date-transact-sql.md)
  
  

