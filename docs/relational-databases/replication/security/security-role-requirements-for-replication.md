---
title: Требования к безопасности ролей для обслуживания репликации | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], roles
- roles [SQL Server], replication
ms.assetid: b324a80f-4319-4cb2-847b-1910c49d90e0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9eb96177e0db43ba8d1b6f9616b13f2e9692b898
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54131124"
---
# <a name="security-role-requirements-for-replication"></a>Security Role Requirements for Replication
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Репликация накладывает ограничения на специфические действия, которые пользователь может выполнить в зависимости от роли, соответствующей имени входа пользователя. Репликация предоставляет определенные разрешения предопределенной роли сервера **sysadmin** , предопределенной роли базы данных **db_owner** и именам входа в списке доступа к публикации (PAL).  
  
## <a name="security-role-requirements-for-replication-setup"></a>Требования к безопасности ролей для настройки репликации  
 В следующей таблице перечислены уровни проверки подлинности, необходимые для стандартных задач настройки репликации:  
  
|Задача настройки|Требования к членству в группах|  
|----------------|----------------------------|  
|Включение распространителя, издателя или подписчика.|Роль сервера**sysadmin** на издателе.|  
|Включение базы данных для репликации.|Роль сервера**sysadmin** на издателе.|  
|Создание публикации.|Роль**db_owner** базы данных для базы данных публикаций на издателе или роль сервера **sysadmin** на издателе.|  
|Просмотр свойств публикации.|Член списка PAL на издателе, роль **db_owner** базы данных в базе данных публикаций на издателе или роль сервера **sysadmin** на издателе.|  
|Создание подписки.|Роль**db_owner** базы данных для базы данных публикаций на издателе или роль сервера **sysadmin** на издателе.<br /><br /> Роль**db_owner** базы данных для базы данных подписок на подписчике или роль сервера **sysadmin** на подписчике.|  
|Настройка профилей агентов.|Роль сервера**sysadmin** на распространителе.|  
  
## <a name="security-role-requirements-for-replication-maintenance"></a>Требования к безопасности ролей для обслуживания репликации  
 В следующей таблице перечислены уровни проверки подлинности, необходимые для выполнения стандартных задач обслуживания репликаций:  
  
|Задача обслуживания|Требования к членству в группах|  
|----------------------|----------------------------|  
|Изменение или удаление распространителя, издателя или подписчика.|Роль сервера**sysadmin** на соответствующем сервере.|  
|Изменение или удаление публикации.|Роль**db_owner** базы данных для базы данных публикаций на издателе или роль сервера **sysadmin** на издателе.|  
|Изменение или удаление подписки на издателе.|Роль**db_owner** базы данных для базы данных публикаций на издателе или роль сервера **sysadmin** на издателе.|  
|Изменение или удаление подписки на подписчике.|Роль**db_owner** базы данных для базы данных подписок на подписчике или роль сервера **sysadmin** на подписчике.|  
|Пометка подписки для повторной инициализации.|Принудительная подписка: роль базы данных **db_owner** в базе данных публикаций на издателе или роль сервера **sysadmin** на издателе.<br /><br /> Подписка по запросу: роль базы данных **db_owner** в базе данных подписок на подписчике или роль сервера **sysadmin** на подписчике.|  
|Просмотр активности, ошибок и журнала репликации с помощью монитора репликации. Пользователь не может изменить профили агентов, расписания и т. д., если он не является членом роли сервера **sysadmin** .|Роль**replmonitor** базы данных в базе данных распространителя на распространителе или роль сервера **sysadmin** на распространителе.|  
|Обслуживание агентов репликации.|Роль**db_owner** базы данных в соответствующей базе данных или роль сервера **sysadmin** на соответствующем сервере.<br /><br /> Если агент создан пользователем в роли **sysadmin** , а учетная запись-посредник не указана для агента, агент запускается в контексте учетной записи агента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . В этом случае пользователь в роли **db_owner** не может изменить задание, связанное с агентом.|  
|Запуск или останов агента репликации.|Владелец задания агента или роль сервера **sysadmin** на соответствующем сервере.|  
  
## <a name="see-also"></a>См. также:  
 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Просмотр и изменение параметров безопасности репликации](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
