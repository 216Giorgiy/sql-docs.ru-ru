---
title: Ограничения безопасности для SQL Server в Linux | Документация Майкрософт
description: В этой статье описывается SQL Server на Linux ограничения.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 9c58592568ca841df270190970fb76fefe43d96d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711722"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Ограничения безопасности для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server в Linux в настоящее время имеет следующие ограничения:

* Предоставляется политику паролей standard. Параметр MUST_CHANGE имеет единственный доступный параметр можно настроить таким образом.  
* Расширенное управление ключами не поддерживается. 
* Использование ключей, хранящихся в хранилище ключей Azure не поддерживается.
* SQL Server создает свой собственный самозаверяющий сертификат для шифрования подключений. SQL Server можно настроить для использования предоставленной сертификата для TLS пользователем. 

Дополнительные сведения о функциях безопасности, доступных в SQL Server, см. в разделе [центр обеспечения безопасности для ядра СУБД SQL Server и базы данных SQL Azure](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Следующие шаги

Общие задачи безопасности, см. в разделе [приступить к работе с помощью функций безопасности SQL Server на Linux](sql-server-linux-security-get-started.md). Для сценария, изменить TCP номер_порта, каталоги по SQL Server и настроить флагов трассировки или параметры сортировки, см. в разделе [Настройка SQL Server в Linux с помощью mssql-conf](sql-server-linux-configure-mssql-conf.md).
