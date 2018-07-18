---
title: Отчеты с дополнительной информацией страниц (диспетчер отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.modelproperties.drilthroughreports.f1
ms.assetid: e96cdeba-452b-45a8-9bcf-b75d76261e31
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 20c212e7829a04e1c6261a8818cebf7534d2529a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244354"
---
# <a name="clickthrough-reports-page-report-manager"></a>Страница «Отчеты с дополнительной информацией» (диспетчер отчетов)
  Отчет с дополнительной информацией отображает таблицу взаимосвязанных данных, если щелкнуть интерактивные данные, содержащиеся в отчете. Такие отчеты формируются сервером отчетов на основе сведений, содержащихся в модели, с помощью которой был создан этот отчет. Если использовать отчеты с дополнительной информацией, которые формирует сервер отчетов, неудобно, можно создать пользовательские отчеты, опубликовать их на сервере отчетов и сопоставить с интерактивными точками данных, определенными в модели. Пользовательские отчеты должны создаваться в построителе отчетов из одной и той же модели, а затем публиковаться на сервере отчетов. Для сопоставления пользовательских отчетов с элементами модели используется страница «Отчеты с дополнительной информацией» в диспетчере отчетов.  
  
 Страница «Отчеты с дополнительной информацией» обеспечивает способ сопоставления стандартных опубликованных отчетов построителя отчетов с конкретными сущностями, папками и элементами модели. Если сопоставить отчет с элементом модели, то пользователи, которые просматривают данный элемент, получат именно этот отчет вместо временного отчета, сформированного сервером отчетов.  
  
 Если предоставляется пользовательский отчет, в него необходимо включить версии отчета как для одного, так и для нескольких экземпляров. Путь к данным, по которому пользователь получает доступ к определенной сущности, определяет, какая версия отчета представлена пользователю во время выполнения — для одного или для нескольких экземпляров. Предсказать заранее, что та или иная версия отчета не понадобится, невозможно.  
  
 Пользовательские отчеты, которые можно сопоставить с сущностями, защищены с помощью иерархии папок на сервере отчетов. Если элемент модели сопоставлен с отчетом, но этот отчет недоступен для пользователя, который переходит к нему, пользователь получит временный отчет, сформированный сервером отчетов, а не нужный пользовательский отчет.  
  
 Хотя можно выбрать любой отчет, к которому имеется доступ, рекомендуется выбирать только те отчеты, которые созданы специально для настраиваемой модели.  
  
> [!NOTE]  
>  Отчеты с дополнительной информацией доступны не во всех выпусках [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Если используемый выпуск [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] неизвестен, обратитесь к администратору базы данных.  
  
## <a name="navigation"></a>Навигация  
 Чтобы перейти к этому местоположению в пользовательском интерфейсе, используйте следующую процедуру.  
  
###### <a name="to-open-the-clickthrough-reports-page"></a>Открытие страницы «Отчеты с дополнительной информацией»  
  
1.  Откройте диспетчер отчетов и перейдите к модели, для которой необходимо сопоставить отчеты с дополнительной информацией с сущностями в модели.  
  
2.  Подведите курсор к модели и щелкните стрелку раскрывающегося списка.  
  
3.  В раскрывающемся меню выберите **Управление**. Откроется страница свойств модели **Общие** .  
  
4.  Выберите вкладку **Дополнительная информация** .  
  
## <a name="options"></a>Параметры  
 **Иерархия элементов модели**  
 Отображает сущности, папки и элементы в пространстве имен модели, которым можно сопоставить пользовательский отчет.  
  
 **Отчет в одном экземпляре**  
 Определяет пользовательский отчет, который будет предоставлен пользователю, если ему понадобится представление данных от одного экземпляра. Нажмите кнопку обзора, чтобы выбрать нужный отчет.  
  
 **Отчет с несколькими экземплярами**  
 Определяет пользовательский отчет, который будет предоставлен пользователю, если ему понадобится представление данных от нескольких экземпляров. Нажмите кнопку обзора, чтобы выбрать нужный отчет.  
  
## <a name="see-also"></a>См. также  
 [Публикация отчетов](../../2014/reporting-services/publish-reports.md)  
  
  