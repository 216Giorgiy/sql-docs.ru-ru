---
title: "Catalog.update_master_address (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e5e560d6011370b3d56ba13c86608d2be3d0dc6e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="catalogupdatemasteraddress-ssisdb-database"></a>Catalog.update_master_address (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Обновление [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] шкалы Out Master конечной точки.

## <a name="syntax"></a>Синтаксис

```tsql
update_master_address [@MasterAddress = ] masterAddress
```

## <a name="arguments"></a>Аргументы
[ @MasterAddress =] *masterAddress*  
Конечная точка шкалы Out Master. *MasterAddress* — **nvarchar**.  

 ## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  

## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
   
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
 
