---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aee9b29650e1ec8bf684a38d14f1fb2fa267652f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47738292"
---
# <a name="localdberrortoomanysharedinstances"></a>LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|287|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Общих экземпляров слишком много, и создать уникальное имя пользовательского экземпляра не удается. Отключите совместный доступ к некоторым из существующих общих экземпляров.|  
  
## <a name="explanation"></a>Объяснение  
 Общих экземпляров слишком много, и создать уникальное имя пользовательского экземпляра не удается.  
  
## <a name="user-action"></a>Действие пользователя  
 Отключите совместный доступ к одному или нескольким общим экземплярам среды выполнения локальной базы данных и повторите попытку.  
  
  
