---
title: Последняя функция (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- last function [XQuery]
- fn:last function
ms.assetid: dc92086e-3b01-4b0b-9f54-3bbf306cf7ae
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7220b0fe10f88ec9ba78d31a8507d12eba7aafff
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51674073"
---
# <a name="context-functions---last-xquery"></a>Функции контекста — last (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает количество элементов в обрабатываемой в данный момент последовательности. Точнее, эта функция возвращает целочисленный индекс последнего элемента в последовательности. Значение индекса первого элемента в последовательности — 1.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:last() as xs:integer  
```  
  
## <a name="remarks"></a>Примечания  
 В SQL Server **fn: last()** может использоваться только в контексте контекстно зависимого предиката. Точнее, ее использование возможно только внутри квадратных скобок (`[ ]`).  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** -столбец базы данных AdventureWorks.  
  
### <a name="a-using-the-last-xquery-function-to-retrieve-the-last-two-manufacturing-steps"></a>A. Использование функции last() языка XQuery для получения последних двух этапов производства  
 Следующий запрос получает последние два этапа производства для определенной модели продукта. Значение, количество этапов производства, возвращенный **last()** функция используется в этом запросе для получения последних двух этапов производства.  
  
```  
SELECT ProductModelID, Instructions.query('   
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  <LastTwoManuSteps>  
   <Last-1Step>   
     { (/AWMI:root/AWMI:Location)[1]/AWMI:step[(last()-1)]/text() }  
   </Last-1Step>  
   <LastStep>   
     { (/AWMI:root/AWMI:Location)[1]/AWMI:step[last()]/text() }  
   </LastStep>  
  </LastTwoManuSteps>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 В предыдущем запросе **last()** работать в /`/AWMI:root//AWMI:Location)[1]/AWMI:step[last()]` возвращает количество этапов производства. Это значение используется для получения последнего этапа производства на участке цеха.  
  
 Результат:  
  
```  
ProductModelID Result    
-------------- -------------------------------------  
7      <LastTwoManuSteps>  
         <Last-1Step>  
            When finished, inspect the forms for defects per   
            Inspection Specification .  
         </Last-1Step>  
         <LastStep>Remove the frames from the tool and place them   
            in the Completed or Rejected bin as appropriate.  
         </LastStep>  
       </LastTwoManuSteps>  
```  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
