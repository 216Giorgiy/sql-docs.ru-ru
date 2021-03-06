---
title: Создание или изменение диалоговое окно «связи» (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createrelationship.f1
helpviewer_keywords:
- Create Relationship dialog box
ms.assetid: da3c7074-623e-4ddf-a707-d3276a47cf1c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: abcfea8c23806de0e784b8784064d77195ad5cf1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197684"
---
# <a name="create-or-edit-relationship-dialog-box-analysis-services---multidimensional-data"></a>диалоговое окно "Создание/Изменение связи" (службы Analysis Services — многомерные данные)
  Используйте диалоговое окно **Создание связи/изменение связи** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для определения или редактирования связи в представлении источника данных. Диалоговое окно **Создание связи/изменение связи** можно вызвать следующими способами:  
  
-   Нажмите кнопку **Создать связь** на панели **Панель инструментов** диалогового окна **Конструктор представлений источников данных**.  
  
-   Щелкните правой кнопкой мыши таблицу на панели **Таблицы** или **Диаграмма** **конструктора представлений источника данных** и выберите пункт **Создать связь**.  
  
-   Щелкните правой кнопкой мыши связь на панели **Диаграмма** **конструктора представлений источника данных** и выберите пункт **Изменить связь**.  
  
> [!NOTE]  
>  В **конструкторе представления источников данных** можно создать связи, не существующие в базовом источнике данных, и удалить связи, созданные **конструктором представления источников данных** из существующих связей внешних ключей в базовом источнике данных.  
  
## <a name="options"></a>Параметры  
 **Исходная таблица (внешний ключ)**  
 Выберите таблицу или именованный запрос, содержащий ссылку на один или несколько столбцов в целевой таблице.  
  
 **Целевая таблица (первичный ключ)**  
 Выберите таблицу, содержащую один или несколько столбцов, на которые имеются ссылки из исходной таблицы. Для самосоединений укажите таблицу, выбранную в параметре **Исходная таблица (внешний ключ)**.  
  
 **Исходные столбцы**  
 Выберите столбцы, которые ссылаются на столбцы в целевой таблице.  
  
 **Целевые столбцы**  
 Выберите столбцы, на которые ссылаются столбцы исходной таблицы.  
  
 **обратный**  
 Щелкните для изменения направления связи.  
  
 **Описание**  
 Введите необязательное описание связи.  
  
## <a name="see-also"></a>См. также  
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Конструктор представлений источников данных &#40;службы Analysis Services — многомерные данные&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
