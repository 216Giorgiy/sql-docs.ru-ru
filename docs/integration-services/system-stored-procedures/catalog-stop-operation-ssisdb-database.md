---
title: catalog.stop_operation (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 97fd9d22-03dd-4eda-8f6c-ba8b67acec68
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: afcaf6f62c697c50dbf40bfaa822c1a685af745e
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58272717"
---
# <a name="catalogstopoperation-ssisdb-database"></a>catalog.stop_operation (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Останавливает проверку или экземпляр выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.stop_operation [ @operation_id = ] operation_id  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @operation_id = ] *operation_id*  
 Уникальный идентификатор проверки или экземпляра выполнения. Параметр *operation_id* имеет тип **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на проверку или экземпляр выполнения.  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пользователь не имеет соответствующих разрешений  
  
-   Недопустимый идентификатор операции  
  
-   Операция уже остановлена  
  
## <a name="remarks"></a>Remarks  
 Только один пользователь за раз должен останавливать операцию в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Если несколько пользователей попытаются остановить операцию, хранимая процедура возвратит код успешного завершения при первой попытке (значение `0`), но последующие попытки будут приводить к ошибкам.  
  
  
