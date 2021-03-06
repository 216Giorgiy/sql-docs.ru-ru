---
title: Разработка пользовательского регистратора | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SSIS packages, log providers
- custom log providers [Integration Services]
- SQL Server Integration Services packages, log providers
- log providers [Integration Services]
- packages [Integration Services], logs
- Integration Services packages, log providers
ms.assetid: 3f715b95-7074-4f5c-8ae2-246998052e78
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 25531ce8e4a405b1e52a0f1f8d81fb536087cff7
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58389282"
---
# <a name="developing-a-custom-log-provider"></a>Разработка пользовательского регистратора
  В службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] имеются различные возможности по ведению журналов, которые позволяют отслеживать события, возникающие во время выполнения пакетов. Службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] включают целый ряд регистраторов, используя которые можно создавать и сохранять журналы в различных форматах, например XML, текстовом, базы данных или в виде журнала событий Windows. Если предоставляемые регистраторы и форматы выходных данных не вполне отвечают вашим требованиям, вы можете создать пользовательский регистратор.  
  
 Чтобы создать пользовательский регистратор, необходимо создать класс, унаследованный от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>, применить к этому новому классу атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> и переопределить важные методы и свойства базового класса, включая свойство <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> и метод <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>.  
  
## <a name="in-this-section"></a>в этом разделе  
 Этот раздел описывает создание, настройку и программирование пользовательского регистратора.  
  
 [Создание пользовательского регистратора](creating-a-custom-log-provider.md)  
 Описывает создание классов для проекта пользовательского регистратора.  
  
 [Создание кода пользовательского регистратора](coding-a-custom-log-provider.md)  
 Описывает реализацию пользовательского регистратора путем перекрытия методов и свойств базового класса.  
  
 [Разработка пользовательского интерфейса для пользовательского регистратора](developing-a-user-interface-for-a-custom-log-provider.md)  
 Пользовательские интерфейсы для пользовательских регистраторов не поддерживаются службами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
## <a name="related-topics"></a>См. также  
  
### <a name="information-common-to-all-custom-objects"></a>Общие сведения для всех пользовательских объектов  
 Сведения, общие для всех типов пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательских объектов для служб Integration Services](../developing-custom-objects-for-integration-services.md)  
 Описывает основные шаги по реализации всех типов пользовательских объектов для служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Сохранение пользовательских объектов](../persisting-custom-objects.md)  
 Описывает пользовательский механизм сохраняемости, при необходимости приводя пояснения.  
  
 [Сборка, развертывание и отладка пользовательских объектов](../building-deploying-and-debugging-custom-objects.md)  
 Описывает методы построения, подписывания, развертывания и отладки пользовательских объектов.  
  
### <a name="information-about-other-custom-objects"></a>Сведения о других пользовательских объектах  
 Сведения о других типах пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательской задачи](../task/developing-a-custom-task.md)  
 Описывает программирование пользовательских задач.  
  
 [Разработка пользовательского диспетчера соединений](../connection-manager/developing-a-custom-connection-manager.md)  
 Описывает вопросы программирования пользовательских диспетчеров соединений.  
  
 [Разработка пользовательского перечислителя по каждому элементу](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Описывает вопросы программирования пользовательских перечислителей.  
  
 [Разработка пользовательского компонента потока данных](../data-flow/developing-a-custom-data-flow-component.md)  
 Описывает вопросы программирования пользовательских источников, преобразований и назначений потока данных.  
  
![Значок служб Integration Services (маленький)](../../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
