---
title: Скрытие элементов условных обозначений на диаграмме (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0d0f83504e3fe0a5686868316a728276626c0e37
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56296572"
---
# <a name="chart-legend---hide-items-report-builder"></a>Условные обозначения диаграммы — скрытие элементов (построитель отчетов)
По умолчанию все ряды, добавленные в отчете с разбиением на страницы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] к диаграмме, отличной от фигурной, будут добавлены как элементы в условные обозначения. Для круговых, воронкообразных и пирамидальных диаграмм добавление любого ряда к диаграмме вызовет добавление индивидуальных точек данных к условным обозначениям.  
  
 Любой элемент условных обозначений можно спрятать. Спрятанный в условных обозначениях элемент по-прежнему будет виден на диаграмме. Это полезно в ситуациях, когда для добавленного к диаграмме ряда не нужно выводить дополнительную информацию. Например, если к диаграмме добавлен вычисляемый ряд (допустим, скользящее среднее), можно спрятать его запись в условных обозначениях, чтобы дополнительная информация выводилась только для первоначальных рядов.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-hide-an-item-from-display-in-the-legend"></a>Переключение видимости элемента условных обозначений  
  
1.  Щелкните правой кнопкой мыши ряд, который нужно скрыть, и выберите пункт **Свойства ряда**.  
  
2.  Выберите **Условные обозначения**. Выберите **Не показывать этот ряд в условных обозначениях** .  
  
    > [!NOTE]  
    >  Нельзя спрятать ряд только для одной группы. Если поле добавлено в область **Группа рядов** , будут скрыты все ряды, принадлежащие этой группе.  
  
## <a name="see-also"></a>См. также:  
 [Форматирование условных обозначений на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
 [Форматирование точек данных на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Изменение текста элемента условных обозначений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/chart-legend-change-item-text-report-builder.md)   
 [Добавление скользящего среднего в диаграмму (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)   
 [Диалоговое окно "Свойства условных обозначений" — "Общие" (построитель отчетов и службы SSRS)](https://msdn.microsoft.com/library/db718f8f-f185-422f-871c-96f0749e5893)  
  
  
