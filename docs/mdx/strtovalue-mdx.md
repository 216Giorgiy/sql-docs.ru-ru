---
title: StrToValue (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c327dc55420cc89f5e76b6fae7822fad3a4e95f4
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52524347"
---
# <a name="strtovalue-mdx"></a>StrToValue (многомерные выражения)


  Возвращает числовое значение, заданное строкой в формате Многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StrToValue(MDX_Expression [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Аргументы  
 *MDX_Expression*  
 Допустимое строковое выражение, разрешающееся (напрямую или косвенно) в одну ячейку.  
  
## <a name="remarks"></a>Примечания  
 **StrToValue** функция возвращает числовое значение, заданное Многомерным выражением. **StrToValue** функция обычно используется вместе с определяемыми пользователем функциями для передачи Многомерного выражения из внешней функции обратно в инструкцию многомерных Выражений, которое может быть разрешено в одну ячейку.  
  
-   При использовании флага CONSTRAINED многомерное выражение должно содержать только скалярное значение. Флаг CONSTRAINED позволяет снизить вероятность атак через указанную строку. Если указано многомерное выражение, которое не разрешается до скалярной величины, то выдается следующая ошибка: «Нарушены ограничения, наложенные флагом CONSTRAINED в функции STRTOVALUE».  
  
-   Без флага CONSTRAINED можно использовать многомерные выражения любой сложности, если они разрешаются в допустимое многомерной выражение, возвращающее одну ячейку.  
  
> [!NOTE]  
>  Возвращение результата многомерного выражения в виде числового значения полезно использовать, если значение хранится в текстовом виде и требуется выполнить арифметические операции над возвращаемыми значениями.  
  
## <a name="example"></a>Пример  
 В следующем примере используется **StrToValue** функция возвращается вес каждого велосипеда.  
  
```  
WITH MEMBER Measures.x AS   
StrToValue   
   ([Product].[Product].CurrentMember.Properties ('Weight')  
   ,CONSTRAINED  
   )  
SELECT Measures.x ON 0  
,[Product].[Product].[Product].Members ON 1  
FROM [Adventure Works]  
WHERE [Product].[Product Categories].[Bikes]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
