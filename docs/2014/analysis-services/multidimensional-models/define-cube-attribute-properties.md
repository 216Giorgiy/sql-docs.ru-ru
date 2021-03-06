---
title: Определение свойств атрибутов куба | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], defining
ms.assetid: 579ca818-f33d-4060-906d-c8bfee93bf99
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2e84c49055a1fdb5b11487ab17af19762f86686c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48146007"
---
# <a name="define-cube-attribute-properties"></a>Определение свойств атрибутов куба
  Свойства атрибутов куба позволяют указать уникальные настройки для атрибутов измерений в кубе на основании того же измерения базы данных. В следующей таблице приводится описание свойств атрибутов куба.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`AggregationUsage`|Определяет, каким образом мастер статистических схем будет создавать агрегаты для атрибута. Это свойство может иметь следующие значения:<br /><br /> `Default`: По умолчанию. Мастер статистических схем применяет роль по умолчанию на основании типа атрибута (Full для ключей, Unrestricted для остальных).<br /><br /> `None`: Ни один агрегат для куба должен включать этот атрибут.<br /><br /> `Unrestricted`: Никакие ограничения, помещаются на мастер статистических схем.<br /><br /> `Full`: Каждый агрегат для куба должен включать этот атрибут.|  
|`AttributeHierarchyEnabled`|Указывает, включена ли иерархия атрибута в этом измерении куба. Это позволяет отключать иерархии атрибута в определенных кубах или ролях измерения. Эта установка не имеет действия, если отключена базовая иерархия атрибута. Значение по умолчанию — `True`.|  
|`OptimizedState`|Указывает, оптимизирована ли иерархия атрибутов в этом измерении куба. Это позволяет оптимизировать иерархии атрибута в определенных кубах или ролях измерения. Эта установка не имеет действия, если базовая иерархия атрибута не оптимизирована. Это свойство может иметь следующие значения:<br /><br /> `FullyOptimized`: По умолчанию. Экземпляр создает индексы иерархии для улучшения производительности запросов. Это значение по умолчанию.<br /><br /> `NotOptimized`: Экземпляр не создает дополнительных индексов.|  
|`AttributeHierarchyVisible`|Указывает, видима ли иерархия атрибута в этом измерении куба. Это позволяет иерархии атрибутов быть видимой в определенных кубах или ролях измерения. Эта установка не имеет действия, если основная иерархия атрибутов не видима. Значение по умолчанию — `True`.|  
|`AttributeID`|Содержит уникальный идентификатор атрибута.|  
  
## <a name="see-also"></a>См. также  
 [Определение свойств измерения куба](define-cube-dimension-properties.md)   
 [Определение свойств иерархии куба](define-cube-hierarchy-properties.md)  
  
  
