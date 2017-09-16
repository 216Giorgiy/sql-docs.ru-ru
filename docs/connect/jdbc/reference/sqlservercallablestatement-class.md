---
title: "Класс SQLServerCallableStatement | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30710a63-c05d-47d9-9cf9-c087a1c76373
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 15c8a944d4130e496c051d163c4724fe6d87f74e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlservercallablestatement-class"></a>Класс SQLServerCallableStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Позволяет указать имя вызываемой хранимой процедуры с входными и выходными параметрами. Этот класс также дает возможность получить значение состояния возврата с помощью синтаксиса ? синтаксис = call( ?, ..).  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Реализует:** [ISQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
 **Расширяет:** [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final class SQLServerCallableStatement  
```  
  
## <a name="remarks"></a>Замечания  
 SQLServerCallableStatement позволяет указать имя хранимой процедуры для вызова, а также входные и выходные параметры. SQLServerCallableStatement также предоставляет возможность получить значение состояния возврата с `? = call( ?, ..)` синтаксиса.  
  
 Этот класс поддерживает развертывание в класс SQLServerCallableStatement, интерфейс ISQLServerCallableStatement, интерфейс java.sql.CallableStatement и классы и интерфейсы, поддерживаемые для развертывания классом SQLServerPreparedStatement. Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
 Если задано одно из SQLServerCallableStatement методы вызывается для типа, если этот тип конфликтует с типом, указанным в [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md), используется тип, заданный параметром метода set последней SQLServerCallableStatement. Однако это может вызвать ошибки несовместимости преобразования типов данных. Если метод set SQLServerCallableStatement не вызывается, типом, указанным в первый [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) используется вызов.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Версии 3.0 драйвера JDBC совместим с JDBC 4.0, согласно которой результирующего набора и счетчиков обновления происходит до извлечения параметров OUT. Если параметры OUT извлекаются до полной обработки результирующего набора и счетчиков обновлений, то любые, еще не обработанные результирующие наборы и счетчики обновлений будут утеряны.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  