---
title: Скрытие элементов условных обозначений на диаграмме (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 88c798ce1bd5f25b1a844894b8aa609a4c641e4c
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59968300"
---
# <a name="hide-legend-items-on-the-chart-report-builder-and-ssrs"></a>Скрытие элементов условных обозначений на диаграмме (построитель отчетов и службы SSRS)
  По умолчанию все ряды, добавленные к диаграмме, отличной от фигурной, будут добавлены как элементы в условные обозначения. Для круговых, воронкообразных и пирамидальных диаграмм добавление любого ряда к диаграмме вызовет добавление индивидуальных точек данных к условным обозначениям.  
  
 Любой элемент условных обозначений можно спрятать. Спрятанный в условных обозначениях элемент по-прежнему будет виден на диаграмме. Это полезно в ситуациях, когда для добавленного к диаграмме ряда не нужно выводить дополнительную информацию. Например, если к диаграмме добавлен вычисляемый ряд (допустим, скользящее среднее), можно спрятать его запись в условных обозначениях, чтобы дополнительная информация выводилась только для первоначальных рядов.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-an-item-from-display-in-the-legend"></a>Переключение видимости элемента условных обозначений  
  
1.  Щелкните правой кнопкой мыши ряд, который нужно скрыть, и выберите пункт **Свойства ряда**.  
  
2.  Выберите **Условные обозначения**. Выберите **Не показывать этот ряд в условных обозначениях** .  
  
    > [!NOTE]  
    >  Нельзя спрятать ряд только для одной группы. Если поле добавлено в область **Группа рядов** , будут скрыты все ряды, принадлежащие этой группе.  
  
## <a name="see-also"></a>См. также  
 [Форматирование условных обозначений на диаграмме (построитель отчетов и службы SSRS)](chart-legend-formatting-report-builder.md)   
 [Форматирование точек данных на диаграмме (построитель отчетов и службы SSRS)](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Изменение текста элемента условных обозначений (построитель отчетов и службы SSRS)](chart-legend-change-item-text-report-builder.md)   
 [Добавление скользящего среднего в диаграмму (построитель отчетов и службы SSRS)](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)   
 [Диалоговое окно "Свойства условных обозначений" — "Общие" (построитель отчетов и службы SSRS)](../legend-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
