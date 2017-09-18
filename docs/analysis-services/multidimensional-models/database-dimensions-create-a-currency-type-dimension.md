---
title: "Создание измерения типа Currency | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dimensions [Analysis Services], currency
- currency [Analysis Services]
- converting currency
- currency dimensions [Analysis Services]
ms.assetid: b1f037d1-ce47-4e47-a1c2-5ec9e781cff6
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9763fad72a0c1ba346e777719a9594801db35f6e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="database-dimensions---create-a-currency-type-dimension"></a>Измерения базы данных — Создание измерения типа Currency
  В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]измерение типа валюты является измерением, атрибуты которого представляют собой список валют для целей финансовой отчетности.  
  
 Измерение валюты позволяет добавлять возможности конвертации валюты в куб в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Чтобы добавить в куб конвертацию валюты, воспользуйтесь мастером бизнес-аналитики для определения команды скрипта многомерного выражения, которая конвертирует меры валюты в значения, соответствующие локали клиентского приложения. Для создания скрипта многомерных выражений мастеру бизнес-аналитики необходимы следующие данные:  
  
-   Измерение валюты, которое представляет собой исходные валюты. (Данное измерение представляет собой исходное измерение валюты.)  
  
-   Группа мер, которая представляет собой используемые валютные курсы.  
  
 На основании этих данных мастер бизнес-аналитики разработает проект конвертации валюты, определяющий подходящее измерение целевой валюты (измерение валюты, которое представляет собой целевые валюты). В зависимости от числа конвертаций валюты, необходимых для выбранного решения бизнес-аналитики, мастер бизнес-аналитики может задать несколько измерений целевой валюты. Дополнительные сведения об определении конвертаций валюты см. в разделе [Конвертация валюты (службы Analysis Services)](../../analysis-services/currency-conversions-analysis-services.md).  
  
 Чтобы определить измерение как измерение валюты, установите для свойства **Type** измерения значение **Currency**.  
  
## <a name="dimension-structure"></a>Структура измерения  
 В измерении валюты содержится, по крайней мере, ключевой атрибут, определяющий отдельные валюты в таблице измерения для измерения валюты. Значение ключевого атрибута отличается как в исходных, так и в целевых измерениях валюты:  
  
-   Чтобы определить атрибут как ключевой атрибут исходного измерения валюты, установите для свойства **Type** атрибута значение **CurrencySource**.  
  
-   Чтобы определить атрибут как целевое измерение валюты, установите для свойства **Type** атрибута значение **CurrencyDestination**.  
  
 В целях отчетности как исходное, так и целевое измерение валюты может содержать следующие необязательные атрибуты:  
  
-   Атрибут названия валюты.  
  
     Чтобы определить атрибут как атрибут названия валюты, установите для свойства **Type** атрибута значение **CurrencyName**.  
  
-   Атрибут источника валюты.  
  
     Чтобы определить атрибут как атрибут источника валюты, установите для свойства **Type** атрибута значение **CurrencySource**.  
  
-   Код валюты, принятый Международной организацией по стандартизации (ISO).  
  
     Чтобы определить атрибут как атрибут кода валюты ISO, установите для свойства **Type** атрибута значение **CurrencyIsoCode**.  
  
 Дополнительные сведения о типах атрибутов см. в разделе [Настройка типов атрибутов](../../analysis-services/multidimensional-models/attribute-properties-configure-attribute-types.md).  
  
## <a name="defining-account-intelligence-with-the-business-intelligence-wizard"></a>Определение логики операций со счетами с помощью мастера бизнес-аналитики  
 После определения измерения счетов и его добавления в куб можно, воспользовавшись мастером бизнес-аналитики, добавить функционал логики операций со счетами, например идентифицирующие типы учетной записи и типы сопоставления, к измерению. Дополнительные сведения см. в разделе [Добавление логики операций со счетами к измерению](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и иерархии атрибутов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Справка F1 мастера бизнес-аналитики](http://msdn.microsoft.com/library/155ac80c-63ae-47aa-9e86-9396e3d920eb)   
 [Типы измерений](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  