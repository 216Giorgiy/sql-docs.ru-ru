---
title: Использование транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d585a757b0f76390739d9a01a8436fd624d1efb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208964"
---
# <a name="using-transactions"></a>Использование транзакций
  В управляющих объектах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SMO) обработка транзакций выполняется через соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Объект ссылается <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Server> объекта при установлении соединения. Такие методы, как <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> и <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A>, принадлежат свойству объекта <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>.  
  
## <a name="see-also"></a>См. также  
 [Создание приложений SMO](creating-smo-programs.md)  
  
  
