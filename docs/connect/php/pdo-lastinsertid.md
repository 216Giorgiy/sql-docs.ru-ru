---
title: "PDO::lastInsertId | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c617b53-a74b-4d5b-b76b-3ec7f1b8e8de
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 00a3f4499c4fa0dee832fb8838d8a1239ed7ff49
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="pdolastinsertid"></a>PDO::lastInsertId
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Возвращает идентификатор для строки, которая самой последней вставлена в таблицу базы данных. Таблица должна содержать столбец IDENTITY NOT NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
string PDO::lastInsertId ([ $name ] );  
```  
  
#### <a name="parameters"></a>Параметры  
$*name*: необязательная строка, позволяющая указать таблицу.  
  
## <a name="return-value"></a>Возвращаемое значение  
Строка идентификатора для строки, добавленной самой последней. Пустая строка, если вызов метода завершается ошибкой.  
  
## <a name="remarks"></a>Замечания  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
   $database = "test";  
   $server = "(local)";  
   $conn = new PDO( "sqlsrv:server=$server; Database = $database", "", "");  
  
   $conn->exec("use Test");  
  
   $ret = $conn->exec("INSERT INTO Table1 VALUES( '19' )");  
   $ret = $conn->exec("INSERT INTO ScrollTest VALUES( 1, '19' )");  
  
   $lastRow = $conn->lastInsertId('Table1');  
   echo $lastRow . "\n";  
  
   // defaults to ScrollTest  
   $lastRow = $conn->lastInsertId();  
   echo $lastRow . "\n";  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
