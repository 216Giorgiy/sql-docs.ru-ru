---
title: Символ процента (символы-шаблоны совпадения) (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 12/06/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '%'
- '%_TSQL'
- wildcard
dev_langs:
- TSQL
helpviewer_keywords:
- conditions [SQL Server], wildcards
- '% (wildcard - character(s) to match)'
- matching conditions [SQL Server]
- wildcard characters [SQL Server]
- characters [SQL Server], wildcard
ms.assetid: d4cbc1a9-37e1-4101-97fb-e6ac30c1223e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 11d70a61f3e6fca60ffbbdd45fa1d3ab5d2d5e39
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773302"
---
# <a name="percent-character-wildcard---characters-to-match-transact-sql"></a>Символ процента (Cимволы-шаблоны совпадения) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Совпадает с любой строкой из нуля или более символов. Этот символ-шаблон может быть использован как префикс или суффикс.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает все имена людей в таблице `Person` базы данных `AdventureWorks2012`, которые начинаются с `Dan`.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE 'Dan%';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [LIKE (Transact-SQL)](../../t-sql/language-elements/like-transact-sql.md)   
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
 [[ ] (подстановочный знак — символы для сопоставления)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
  [&#91;^&#93; (подстановочный знак — символы не для сопоставления)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
 [_ (подстановочный знак — совпадение одного символа)](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
    
  
