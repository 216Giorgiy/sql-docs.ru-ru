---
title: AddCalculatedMembers (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ADDCALCULATEDMEMBERS
dev_langs:
- kbMDX
helpviewer_keywords:
- AddCalculatedMembers function
ms.assetid: c676cf70-7c24-46ea-b88c-d4a389a71d48
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: d944f0e4c3b97e85e2c1e606599b4573a9be7934
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="addcalculatedmembers-mdx"></a>AddCalculatedMembers (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор, созданный путем добавления вычисляемых элементов в указанный набор.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
AddCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Замечания  
 По умолчанию в языке многомерных выражений вычисляемые элементы исключаются при вычислении функций набора. **AddCalculatedMembers** функция просматривает выражение набора, указанного в *Set_Expression,* и включает вычисляемые одноуровневые элементы, содержащиеся в области данного выражения набора.  
  
> [!NOTE]  
>  Эту функцию можно использовать только для одномерных выражений наборов.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано использование этой функции.  
  
```  
-- This query returns the calculated members for the cube  
-- by retrieving all members, and then excluding non-calculated members.  
SELECT   
   AddCalculatedMembers(  
      {[Measures].Members}  
      )-[Measures].Members ON COLUMNS  
FROM [Adventure Works]   
```  
  
 В следующем примере возвращается `Measures.[Unit Price]` вместе со всеми вычисляемыми элементами в **меры** измерения, от **Adventure Works** куба.  
  
```  
SELECT  
   AddCalculatedMembers({Measures.[Unit Price]}) ON COLUMNS  
FROM   
   [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
