---
title: Дескриптор переходов | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- state transitions [ODBC], descriptor
- transitioning states [ODBC], descriptor
- descriptor transitions [ODBC]
ms.assetid: 0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32799b8a7b78672e33da24bfac45aab1d764bb0b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907699"
---
# <a name="descriptor-transitions"></a>Дескриптор переходов
Дескрипторы ODBC имеет три состояния.  
  
|Состояние|Описание|  
|-----------|-----------------|  
|D0|Незанятое дескриптора|  
|D1i|Неявно выделенного дескриптора.|  
|D1e|Явно выделенного дескриптора.|  
  
 В следующих таблицах показано, как каждая функция ODBC влияет на состояние дескриптора.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|D1i [1]|--|--|  
|D1e [2]|--|--|  
  
 [1] в этой строке показаны переходы при *HandleType* был значение SQL_HANDLE_STMT.  
  
 [2] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_DESC.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|(СИСТЕМЫ)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(СИСТЕМЫ) [2]|(HY017)|D0|  
  
 [1] в этой строке показаны переходы при *HandleType* был значение SQL_HANDLE_STMT.  
  
 [2] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_DESC.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>Функция SQLGetDescField и SQLGetDescRec  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|(СИСТЕМЫ)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField и SQLSetDescRec  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|(СИСТЕМЫ) [1]|--|--|  
  
 [1] в этой строке показаны переходы при *DescriptorHandle* было Отменить, APD или IPD, дескриптор или (для **SQLSetDescField**) при *DescriptorHandle* был дескриптор IRD и *FieldIdentifier* SQL_DESC_ARRAY_STATUS_PTR или SQL_DESC_ROWS_PROCESSED_PTR.  
  
## <a name="all-other-odbc-functions"></a>Все остальные функции ODBC  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|--|--|--|
