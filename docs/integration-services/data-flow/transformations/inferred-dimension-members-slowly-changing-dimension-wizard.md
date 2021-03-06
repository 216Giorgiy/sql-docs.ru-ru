---
title: Выводимые элементы измерения (мастер медленно изменяющихся измерений) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5821b5e8e0db6054ea7f1e3d89f3e11c314c0a15
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58282178"
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a>Выводимые элементы измерения (мастер медленно изменяющихся измерений)
  Диалоговое окно **Выводимые элементы измерения** используется для задания параметров их вывода. Выводимые элементы существуют в случае, когда таблица фактов ссылается на еще не загруженные элементы таблицы измерения. При загрузке данных для выводимого элемента можно просто обновить существующую запись, а не создавать ее заново.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Включить поддержку выводимых элементов измерения**  
 В случае включения выводимых элементов, необходимо выбрать один из двух следующих параметров.  
  
 **Все столбцы с типом изменения имеют значение NULL**  
 Позволяет указать, вводить ли значения NULL во все столбцы с типом изменения в новой записи выводимых элементов.  
  
 **Использовать логический столбец для указания принадлежности текущей записи к выводимым элементам**  
 Позволяет задать, использовать ли существующий логический столбец для указания, является ли текущая запись выводимым элементом.  
  
 **Признак выводимого элемента**  
 Если выбрано использовать логический столбец для указания выводимых элементов как описано выше, выберите столбец из списка.  
  
## <a name="see-also"></a>См. также:  
 [Настройка выходов при помощи мастера медленно изменяющихся измерений](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
