---
title: Установка и удаление компонента источника OData | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 34a71ed768c49436a4dba4ecf225bdd009132866
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385263"
---
# <a name="install-and-uninstall-odata-source-component"></a>Установка и удаление компонента источника OData
  В этом разделе приведены инструкции по установке или удалению компонента источника OData на компьютере.  
  
## <a name="installation"></a>Установка  
 Для компонента источника OData на компьютере должны быть установлены следующие компоненты.  
  
-   SQL Server Data Tools (для проектирования пакетов)  
  
-   Службы SQL Server Integration Services (для запуска пакетов вне Visual Studio)  
  
 Чтобы установить компонент источника OData, загрузите [пакет дополнительных компонентов SQL Server 2014](https://go.microsoft.com/fwlink/p/?LinkId=391999) и запустите один из следующих MSI-файлов.  
  
-   ODataSourceForSQLServer2014-amd64.msi для 64-разрядных платформ  
  
-   ODataSourceForSQLServer2014-x86.msi для 32-разрядных платформ  
  
> [!IMPORTANT]  
>  64-разрядный установщик устанавливает 32-разрядную и 64-разрядную версии компонента источника OData. Если используется 32-разрядная ОС, необходимо запускать 32-разрядный установщик.  
  
## <a name="uninstallation"></a>Удаление  
 Компонент источника OData можно удалить в меню **Программы и компоненты** . Найдите элемент **Компонент источника OData Microsoft SQL Server SSIS (x64)** и нажмите кнопку **Удалить**.  
  
  
