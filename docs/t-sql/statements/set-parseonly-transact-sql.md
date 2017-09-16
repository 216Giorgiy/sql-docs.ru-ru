---
title: "SET PARSEONLY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARSEONLY_TSQL
- SET_PARSEONLY_TSQL
- PARSEONLY
- SET PARSEONLY
dev_langs:
- TSQL
helpviewer_keywords:
- parsing [SQL Server], SET PARSEONLY statement
- checking syntax
- PARSEONLY option
- syntax [SQL Server], verifying
- verifying syntax
- SET PARSEONLY statement
ms.assetid: 514ab042-c53e-4d96-be71-fb08fcc6ef3c
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2a117e81d9645edd9f24702ac01d8eeea3765726
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-parseonly-transact-sql"></a>SET PARSEONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Исследует синтаксис каждой инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и возвращает сообщения об ошибках без компиляции или выполнения инструкции.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET PARSEONLY { ON | OFF }  
```  
  
## <a name="remarks"></a>Замечания  
 Если для SET PARSEONLY установлено значение ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] только осуществляет синтаксический анализ инструкции. Если для SET PARSEONLY установлено значение OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компилирует и выполняет инструкцию.  
  
 Установка значения SET PARSEONLY осуществляется перед синтаксическим анализом, а не во время выполнения или запуска.  
  
 Не используйте PARSEONLY в хранимой процедуре или триггере. Инструкция SET PARSEONLY возвращает смещение, если параметру OFFSETS присвоено значение ON, и ошибки не возникают.  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [ЗНАЧЕНИЕ СМЕЩЕНИЯ &#40; Transact-SQL &#41;](../../t-sql/statements/set-offsets-transact-sql.md)  
  
  