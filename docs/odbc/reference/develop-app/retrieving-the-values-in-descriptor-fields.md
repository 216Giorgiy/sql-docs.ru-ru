---
title: Получение значения в поля дескриптора | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 37efd70ccd8fa0ad5c6d4bb573eb1c158a3ec35b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Получение значения в поля дескриптора
Приложение может вызвать **SQLGetDescField** получить одно поле записи дескриптора. **SQLGetDescField** дает приложению доступ для поля дескриптора, определенные в ODBC с также поля, определяемые драйвером.  
  
 **SQLGetDescRec** можно вызвать для получения значения нескольких полей дескриптора, которые определяют тип данных и хранилища данных столбца или параметра.
