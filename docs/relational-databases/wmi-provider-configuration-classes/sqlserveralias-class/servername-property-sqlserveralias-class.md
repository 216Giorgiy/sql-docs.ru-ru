---
title: Свойство ServerName (класс SqlServerAlias) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- ServerName Property (SqlServerAlias Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ServerName property
ms.assetid: 58c82b19-b548-42fa-9c5a-059b606da097
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5319f26db7b54fa6bb5bcae73068c7f11e17362d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47768382"
---
# <a name="servername-property-sqlserveralias-class"></a>Свойство ServerName (класс SqlServerAlias)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает имя экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , заданного псевдонимом соединения сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ServerName [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlServerAlias](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) , представляющий псевдоним [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Строковое значение, определяющее имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на который ссылается псевдоним соединения сервера.  
  
## <a name="remarks"></a>Примечания  
  
