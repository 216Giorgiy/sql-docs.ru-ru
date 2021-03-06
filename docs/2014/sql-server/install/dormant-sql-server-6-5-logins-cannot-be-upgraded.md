---
title: Невозможно обновить неактивные имена входа SQL Server 6.5 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0381e04ae1df53e5502c49eb17d0823fcf611e89
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582182"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a>Невозможно обновить неактивные имена входа SQL Server 6.5
  Советник по переходу обнаружил имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], пароль которого нельзя напрямую обновить до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Чтобы активировать имя входа, необходимо сбросить его пароль. Можно изменить пароль с помощью инструкции ALTER LOGIN.  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 Новый пароль будет проверен на соответствие политике сложности паролей системы, если проверка политики не отключена. Рекомендуется использовать сложные пароли и не отключать политику проверки. Параметр MUST_CHANGE принуждает пользователя выбрать новый пароль. Это не обязательно, но рекомендуется.  
  
 Можно определить неактивные имена входа с помощью следующего запроса:  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
