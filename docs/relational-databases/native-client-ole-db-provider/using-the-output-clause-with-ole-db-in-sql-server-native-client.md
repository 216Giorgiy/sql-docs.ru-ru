---
title: "Использование предложения OUTPUT с OLE DB в собственном клиенте SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-provider
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 53deeb99-c088-4fde-844b-b2d91d6de1eb
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ba8b9ae67733b2a86bc682ae8c3e518284934f71
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="using-the-output-clause-with-ole-db-in-sql-server-native-client"></a>Использование предложения OUTPUT с OLE DB в собственном клиенте SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Если используется предложение OUTPUT в инструкции INSERT, UPDATE, DELETE или MERGE количество затронутых строк недоступен. Приложение необходимо подсчитать число строк в наборе строк, возвращаемых предложением OUTPUT.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложения поставщика OLE DB для SQL Server Native Client](../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  