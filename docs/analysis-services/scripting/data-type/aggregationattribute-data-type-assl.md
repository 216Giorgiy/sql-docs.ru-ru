---
title: "Тип данных AggregationAttribute (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AggregationAttribute Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationAttribute
helpviewer_keywords:
- AggregationAttribute data type
ms.assetid: 636827c7-938d-4b7d-9827-46da3bc60d9a
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c4e7ac84001e3b113f8a351d464b0bec35fe5272
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="aggregationattribute-data-type-assl"></a>Тип данных AggregationAttribute (ASSL)
  Определяет тип-примитив, представляющий взаимосвязь между [статистической обработки](../../../analysis-services/scripting/objects/aggregation-element-assl.md) элемента и атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationAttribute>  
   <AttributeID>...</AttributeID>  
      <Annotations>...</Annotations>  
</AggregationAttribute>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md), [заметок](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
|Производные элементы|[Атрибут](../../../analysis-services/scripting/objects/attribute-element-assl.md) ([атрибуты](../../../analysis-services/scripting/collections/attributes-element-assl.md) коллекцию [AggregationDimension](../../../analysis-services/scripting/data-type/aggregationdimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 Соответствующим классом в модели объектов AMO является <xref:Microsoft.AnalysisServices.AggregationAttribute>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Aggregation &#40; ASSL &#41;](../../../analysis-services/scripting/objects/aggregation-element-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  