---
title: "Установка обновлений для обслуживания SQL Server 2016 | Документы Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/31/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c0e1316d3444a08aaf114de18d1b7d9f5450aa9f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server-servicing-updates"></a>Установка обновлений для обслуживания SQL Server
  В этом разделе описывается установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В разделе рассматриваются следующие вопросы.  
  
-   Установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при установке нового экземпляра  
  
-   Установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] после установки экземпляра.  
  
 Пользователям рекомендуется своевременно оценивать и устанавливать последние обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы обеспечить наличие последних обновлений безопасности для систем.  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-during-a-new-installation"></a>Установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при установке нового экземпляра  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объединяет последние обновления продукта с установкой основного продукта, чтобы он и применимые обновления устанавливались одновременно. Функция обновления продукта может искать подходящие обновления в следующих источниках.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update  
  
-   Службы Windows Server Update Services (WSUS)  
  
-   Локальная папка  
  
-   Сетевая папка  
  
 Когда программа установки обнаруживает последние версии соответствующих обновлений, эти обновления загружаются и интегрируются в текущую процедуру установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Функция обновления продукта может включить в установку пакет обновления, накопительное обновление или и то и другое.  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-after-it-has-already-been-installed"></a>Установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] после установки экземпляра  
 В установленном экземпляре [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]рекомендуется установить последние обновления безопасности и критические обновления, в том числе выпуски для общего распространения (GDR), пакеты обновления (SP) и накопительные пакеты обновления (CU). Дополнительные сведения см. в [объявлении о добавочной модели обслуживания SQL Server за март 2016 года](http://blogs.msdn.microsoft.com/sqlreleaseservices/announcing-updates-to-the-sql-server-incremental-servicing-model-ism/). 
  
 Обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступны через центр обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MU), службу обновления Windows (WSUS) и Центр загрузки Майкрософт. Обновления безопасности и критические обновления для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступны в центре обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Чтобы увидеть эти обновления, необходимо дать согласие на использование MU в приложении центра обновления Windows на панели управления.  
  
 После получения обновления через центр обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)] все компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обновляются до последней версии в автоматическом режиме. Если необходима дополнительная гибкость в процессе установки или отсутствует доступ к Интернету или службам WSUS, то нужно получить обновления из центра загрузки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Установка SQL Server 2016 с помощью мастера установки (программа установки)](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)   
 [Добавление компонентов в экземпляр SQL Server 2016 (программа установки)](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)   
 [Исправление неудавшейся установки SQL Server 2016](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)  
  
  
