---
title: "SQLBindParameter (драйвер Excel) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel driver [ODBC], SQLBindParameter
- SQLBindParameter function [ODBC], Excel Driver
ms.assetid: 40489bc5-3e2a-425e-892d-e0dc037f4d7a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 013f19579815dfcac2fcfe78cbbe41919bff9c15
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlbindparameter-excel-driver"></a>SQLBindParameter (драйвер Excel)
> [!NOTE]  
>  В этом разделе сведения драйвера Excel. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 При использовании драйвера Microsoft Excel при выполнении инструкции INSERT, в котором используется параметр, чтобы вставить значение NULL в столбец SQL_CHAR будет возвращено значение SQL_SUCCESS_WITH_INFO с кодом SQLSTATE 01004, «Усеченный данных».
