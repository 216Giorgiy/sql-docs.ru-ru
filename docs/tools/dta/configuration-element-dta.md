---
title: Элемент Configuration (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Configuration element
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9a0e0bbcc65dd3b9cb1d6fd53f3d296f995f0527
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51291320"
---
# <a name="configuration-element-dta"></a>Элемент Configuration (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Задает определенную пользователем конфигурацию, состоящую из существующих и гипотетических структур физического проектирования и позволяющую помощнику по настройке ядра СУБД производить анализ при настройке рабочей нагрузки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## <a name="element-attributes"></a>Атрибуты элемента  
  
|Атрибут конфигурации|Описание|  
|-----------------------------|-----------------|  
|**SpecificationMode**|Необязательный параметр. Указывает, должен ли помощник по настройке ядра СУБД анализировать указанную конфигурацию как связь с текущей существующей конфигурацией либо как совершенно новую, отдельную конфигурацию. Используйте тип данных **string** для указания этого атрибута при помощи следующих допустимых значений:<br /><br /> **Relative**:<br />                  Вычисляет указанную конфигурацию как связь с существующей конфигурацией структур физического проектирования (индексы, индексированные представления, секционирование) в настраиваемой базе данных. Пример:<br /><br /> `<Configuration SpecificationMode="Relative">`<br /><br /> **Absolute**:<br />                  Вычисляет указанную конфигурацию как самостоятельную. Если указано «Absolute», помощник по настройке ядра СУБД не учитывает существующую конфигурацию. Пример:<br /><br /> `<Configuration SpecificationMode="Absolute">`|  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необязательный параметр. Может использоваться один раз для каждого элемента **DTAInput** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DTAInput (DTA)](../../tools/dta/dtainput-element-dta.md)|  
|**Дочерние элементы**|[Элемент Server описания конфигурации (DTA)](../../tools/dta/server-element-for-configuration-dta.md)|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
