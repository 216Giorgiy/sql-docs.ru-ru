---
title: Планирование трассировок | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], events
- traces [SQL Server]
- traces [SQL Server], stopping
- events [SQL Server], filters
- scheduling traces [SQL Server]
- traces [SQL Server], scheduling
- stopping traces
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 32d292d18a240554165f2850664faf93ae2a855f
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51669343"
---
# <a name="schedule-traces"></a>Планирование трассировок
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]предусмотрены два способа планирования трассировок. Возможные действия:  
  
-   задать время прекращения трассировки;  
  
-   использовать агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для планирования трассировки.  
  
## <a name="specifying-a-stop-time"></a>Задание времени прекращения  
 Время прекращения трассировки можно указать в том случае, если используются хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] или приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Время прекращения указывается после того, как произведено начальное конфигурирование трассировки.  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a>Планирование трассировки с помощью агента SQL Server  
 Наилучшим способом планирования трассировок является использование агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для запуска трассировки с последующим указанием времени ее прекращения хранимой процедурой [!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_trace_setstatus**или приложением [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 **Установка фильтра времени прекращения трассировки**  
  
 [Фильтровать события по времени окончания (приложение SQL Server Profiler)](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [Хранимая процедура sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Задачи автоматизированного администрирования (агент SQL Server)](https://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)  
  
  
