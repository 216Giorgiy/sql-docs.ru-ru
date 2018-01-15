---
title: "managed_backup.fn_get_current_xevent_settings (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_get_current_xevent_settings
- smart_admin.fn_get_current_xevent_settings_TSQL
- fn_get_current_xevent_settings_TSQL
- smart_admin.fn_get_current_xevent_settings
dev_langs: TSQL
helpviewer_keywords:
- smart_admin.fn_get_current_xevent_settings
- fn_get_current_xevent_settings
ms.assetid: 95d3adaa-bb9d-4833-b8b4-3d9fd4f9c82a
caps.latest.revision: "11"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cd569f74e53d5b556f7ec8a4c1f3c02b7d574742
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="managedbackupfngetcurrentxeventsettings-transact-sql"></a>managed_backup.fn_get_current_xevent_settings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку для каждого типа расширенного события, поддерживаемого Smart Admin.  
  
 Эта функция используется для возврата или просмотра текущих параметров расширенных событий в целях определения настраиваемых типов событий и текущих конфигураций.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
smart_admin.fn_get_current_xevent_settings ()   
```  
  
##  <a name="Arguments"></a> Аргументы  
 Эта функция не имеет аргументов.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
 Каналы администрирования, аналитики и операционные каналы расширенных событий необходимы, включены по умолчанию и не могут быть изменены.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|Event_name|NVARCHAR(128)|Тип расширенного события|  
|is_configurable|NVARCHAR(128)|Это свойство имеет значение **True** , если событие можно настроить, в противном случае его значение **False**.|  
|is_enabled|NVARCHAR(128)|Устанавливается в значение True, если событие включено, и False, если выключено. Для включения событий отладки используйте хранимую процедуру smart_admin.sp_set_parameter.|  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется **ВЫБЕРИТЕ** разрешений на функцию.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все расширенные события с их текущим состоянием.  
  
```  
SELECT *   
FROM smart_admin.fn_get_current_xevent_settings ()  
  
```  
  
  