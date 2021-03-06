---
title: Агент моментальных снимков | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.snapshotagent.f1
helpviewer_keywords:
- Snapshot Agent dialog box
ms.assetid: b715e621-2cd5-4a15-8f58-a341aa8ef5e4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a6efca71c246eaa08b237cd551c0cfae022463fc
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54123855"
---
# <a name="snapshot-agent"></a>агент моментальных снимков
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В диалоговом окне **Агент моментальных снимков** отображаются подробные сведения об агенте моментальных снимков, в том числе состояние, журнал, информационные сообщения и сообщения об ошибках.  
  
## <a name="options"></a>Параметры  
 Выберите в меню **Вид** , какие сеансы агента моментальных снимков нужно просматривать, затем выберите определенный сеанс в сетке с именем **Сеансы агента моментальных снимков**. Подробные сведения об этом сеансе отображаются в сетке, помеченной как **Действия в выбранном сеансе**. Если выбранный сеанс закончен с ошибкой, также выводится на экран текстовое поле, помеченное как **Описание ошибки или сообщение выбранного сеанса** .  
  
 **Вид**  
 Выберите сеансы агента моментальных снимков, которые нужно просмотреть.  
  
 **Состояние**  
 Состояние агента моментальных снимков. Возможные значения состояния показаны в следующем списке:  
  
-   Ошибка  
  
-   Попытка повторно выполнить неудачно завершившиеся команды  
  
-   Не выполняется  
  
-   Завершен  
  
 **Start Time**  
 Время начала сеанса.  
  
 **Время окончания**  
 Время окончания сеанса. Если агент не остановлен, это поле остается пустым.  
  
 **Длительность**  
 Общее время работы этого сеанса агента моментальных снимков. Если в данный момент агент работает, отображается время его работы, после завершения сеанса агента отображается общая длительность сеанса.  
  
 **Сообщение об ошибке**  
 Если сеанс завершился с ошибкой, в данном поле отображается последнее сообщение об ошибке, зарегистрированное агентом моментальных снимков. Если сеанс завершился без ошибки, это поле остается пустым.  
  
 **Сообщение действия**  
 Все информационные сообщения и сообщения об ошибках, зарегистрированные агентом моментальных снимков во время выбранного сеанса.  
  
 **Время действия**  
 Время, когда было выполнено действие, описанное в столбце **Сообщение действия** .  
  
 **Описание ошибки или сообщение выбранного сеанса**  
 Выводится, только если выбранный сеанс отображает значение **Ошибка** в столбце **Состояние** . Это текстовое поле отображает подробные данные об ошибке и о выполняемой во время возникновения ошибки команде. Также содержит ссылки на дополнительные данные, имеющие отношение к ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Запуск монитора репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Просмотр сведений и выполнение задач с помощью монитора репликации](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication.md)   
 [Replication Agents Overview](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
