---
title: Программное управление ролями пакетов (служба SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4bcd4325e776e1b9d369f17f0f1aa456dadeb974
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58282938"
---
# <a name="managing-package-roles-programmatically-ssis-service"></a>Программное управление ролями пакетов (служба SSIS)
  При программной работе с пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может потребоваться определить, какие роли доступны для пакетов, либо определить или задать роли для индивидуального пакета. Класс <xref:Microsoft.SqlServer.Dts.Runtime.Application> из пространства имен <xref:Microsoft.SqlServer.Dts.Runtime> предоставляет разнообразные методы, выполняющие эти требования.  
  
 Роли применимы только для пакетов, хранящихся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb**. Дополнительные сведения о ролях пакетов см. в разделе [Роли служб Integration Services (службы SSIS)](../../integration-services/security/integration-services-roles-ssis-service.md).  
  
 Все методы, используемые в данном разделе, требуют наличия ссылки на сборку **Microsoft.SqlServer.ManagedDTS**. После добавления ссылки в новый проект импортируйте пространство имен <xref:Microsoft.SqlServer.Dts.Runtime> с помощью инструкции **using** или **Imports**.  
  
> [!IMPORTANT]  
>  Методы класса <xref:Microsoft.SqlServer.Dts.Runtime.Application> для работы с хранилищем пакетов служб SSIS поддерживают только имена «.», localhost и имя сервера для локального сервера. Нельзя использовать имя «(local)».  
  
## <a name="determining-which-roles-are-available"></a>Определение доступных ролей  
 Чтобы определить, какие роли доступны для пакетов, хранящихся на конкретном сервере, вызовите метод <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> класса <xref:Microsoft.SqlServer.Dts.Runtime.Application>.  
  
## <a name="determining-which-roles-are-assigned"></a>Определение назначенных ролей  
 Чтобы определить, какие роли уже назначены определенному пакету, вызовите метод <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A>. Чтобы назначить роли пакету, вызовите метод <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A>.  
  
## <a name="see-also"></a>См. также:  
 [Роли служб Integration Services (службы SSIS)](../../integration-services/security/integration-services-roles-ssis-service.md)  
  
  
