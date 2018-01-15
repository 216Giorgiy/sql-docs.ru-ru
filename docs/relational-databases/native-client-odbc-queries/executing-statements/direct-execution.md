---
title: "Прямое выполнение | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
caps.latest.revision: "38"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 28f1d355627fc6b54feb3357f77ce14a2dd014c7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="direct-execution"></a>Прямое выполнение
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Прямое выполнение — это наиболее распространенный способ выполнения инструкции. Приложение создает символьную строку, содержащую [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкции и передает его для выполнения с помощью **SQLExecDirect** функции. Когда инструкция достигает сервера, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] компилирует ее в план выполнения и немедленно запускает план.  
  
 Прямое выполнение обычно используется приложениями, которые создают и выполняют инструкции во время выполнения, и является наиболее эффективным методом для инструкций, которые будут выполняться одновременно. Недостатком многих баз данных является то, что SQL-инструкция должна анализироваться и компилироваться при каждом выполнении, что увеличивает нагрузку при неоднократном использовании данной процедуры.  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] значительно повышена производительность прямого выполнения часто выполняемых инструкций в многопользовательских средах, а использование SQLExecDirect с маркерами параметров для часто используемых инструкций SQL может приблизить их эффективность к эффективности выполнения после подготовки.  
  
 При подключении к экземпляру компонента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует драйвер ODBC собственного клиента [sp_executesql](../../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md) для передачи инструкции SQL или пакета, указанного на **SQLExecDirect**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]содержит логику, чтобы быстро определить, если инструкции SQL или выполнении пакета с **sp_executesql** соответствует инструкцию или пакет, созданный план выполнения, который уже существует в памяти. В случае совпадения [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] повторно использует существующий план, а не компилирует новый. Это означает, что часто выполняемые инструкции SQL, выполненных с **SQLExecDirect** в системе с большим количеством пользователей получают пользу от многих преимуществ повторное использование плана, которые ранее были доступны с хранимыми процедурами в более ранних версиях только[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Данное преимущество работает только в случае одновременного выполнения одной инструкции или пакета SQL несколькими пользователями. Следуйте этим соглашениям по написанию кода для повышения вероятности того, что инструкции SQL, выполняемые различными клиентами, будут достаточно похожи, чтобы повторно использовать планы выполнения.  
  
-   Не включайте константы данных в инструкции SQL. Вместо этого используйте маркеры параметров, привязанные к переменным программы. Дополнительные сведения см. в разделе [использование параметров инструкции](../../../relational-databases/native-client-odbc-queries/using-statement-parameters.md).  
  
-   Используйте полные имена объектов. Планы выполнения не будут использоваться повторно при неполных именах объектов.  
  
-   Соединения приложения по возможности должны использовать стандартный набор параметров соединений и инструкций. Планы выполнения, созданные для соединения с одним набором параметров (например ANSI_NULLS), не используются для соединения, имеющего другой набор параметров. Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имеют одинаковые установки по умолчанию для этих параметров.  
  
 Если все инструкции, выполняемые с **SQLExecDirect** кодируются с помощью этих соглашений [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно повторно использовать планы выполнения, при возможности будет.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение инструкции &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  