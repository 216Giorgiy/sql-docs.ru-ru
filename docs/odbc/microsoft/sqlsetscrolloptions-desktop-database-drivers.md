---
title: SQLSetScrollOptions (для настольных баз данных драйверы) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
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
- SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 716a29b89598ead97ae5268dcf850dd4c2c1a38d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (драйверы для настольных баз данных)
Прямой и статические курсоры поддерживаются для SQL_CONCUR_READ_ONLY.  
  
 Только управляемые набором ключей курсоры поддерживаются для *fConcurrency* аргумент SQL_CONCUR_LOCK.  
  
 *FConcurrency* аргумент SQL_CONCUR_ROWVER не поддерживается.  
  
 Динамические курсоры и смешанного курсоры не поддерживаются.
