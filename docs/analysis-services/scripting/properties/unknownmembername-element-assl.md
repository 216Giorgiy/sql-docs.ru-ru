---
title: "Элемент UnknownMemberName (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: UnknownMemberName Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: UnknownMemberName
helpviewer_keywords: UnknownMemberName element
ms.assetid: 54271336-ea9b-4270-ac3a-9658a5cff77b
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f8c0ef48c999e2a541c8e7d0177dde728c81478e
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="unknownmembername-element-assl"></a>Элемент UnknownMemberName (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит заголовок на языке по умолчанию измерения, для неизвестного элемента измерения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMemberName>...</UnknownMemberName>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|*Unknown*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значение элемента **UnknownMemberName** задает заголовок, используемый для неизвестного элемента. Идентификатором неизвестного элемента является *Dimension*.UnknownMember, где *Dimension* представляет собой уникальное имя измерения, которое не может быть изменено.  
  
 Элемент, соответствующий родителю параметра **UnknownMemberName** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
