---
title: ROUND (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- rounding expressions
- ROUND function [SSIS]
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e6a3156fd30348f8bae8f3e66233ac1b0be99a66
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35400486"
---
# <a name="round-ssis-expression"></a>ROUND (выражение служб SSIS)
  Возвращает числовое выражение, округленное до указанной длины или точности. Параметр длины должен иметь целочисленное значение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Является выражением допустимого числового типа. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 *длина*  
 Является целочисленным выражением. Это точность, до которой должно быть округлено значение *numeric_expression* .  
  
## <a name="result-types"></a>Типы результата  
 Того же типа, что и *numeric*_*expression.*  
  
## <a name="remarks"></a>Remarks  
 Аргумент *length* должен иметь положительное целочисленное значение либо ноль.  
  
 ROUND возвращает результат NULL, если аргумент имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Эти примеры округляют числовые величины до трех знаков. Первый возвращенный результат — 137.1570, второй — 137.1580.  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
