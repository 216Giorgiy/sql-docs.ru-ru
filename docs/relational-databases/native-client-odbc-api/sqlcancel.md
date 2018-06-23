---
title: SQLCancel | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fb89ce802ff713127e570fbf9f7cc4b19e872606
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35702655"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) раздел о том, что в ODBC 2.x, если приложение вызывает **SQLCancel** Если обработка не выполняется в операторе **SQLCancel** действует так же, как  **SQLFreeStmt** с **SQL_CLOSE** параметр; это поведение определяется только для полноты и приложения должны вызывать метод **SQLFreeStmt** или  **SQLCloseCursor** закрытия курсора. Но даже если ваш [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственное клиентское приложение задает версию ODBC API 3.5.x или более поздней версии, **SQLCancel** функция будет использовать поведение ODBC 2.x.  
  
## <a name="see-also"></a>См. также  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
