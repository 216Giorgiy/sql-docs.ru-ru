---
title: Архитектура пользовательских элементов отчета | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a053eb55547da9030eebe9036667cca2e14606f1
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60153762"
---
# <a name="custom-report-item-architecture"></a>Архитектура пользовательских элементов отчета
  Пользовательский элемент отчета является расширением языка определения отчетов (RDL), позволяющим разработчикам добавлять функции, изначально не поддерживаемые в RDL, или расширять функциональные возможности существующих элементов управления. Существует два основных компонента пользовательского элемента отчета: компонент времени выполнения и компонент времени разработки. Эти компоненты реализованы как сборки платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] и могут быть записаны на любом соответствующем CLS языке.  
  
## <a name="the-run-time-component"></a>Компонент времени выполнения  
 Компонент времени выполнения для пользовательского элемента отчета вызывается обработчиком отчетов во время выполнения. Компонент времени выполнения принимает данные, переданные обработчиком отчетов во время выполнения, обрабатывает эти данные и возвращает изображение, содержащее отображаемый пользовательский элемент отчета.  
  
 ![Пользовательский элемент отчета (компонент времени выполнения)](../../../2014/reporting-services/media/customreportitemrun-timecomponentarchitecture.gif "Пользовательский элемент отчета (компонент времени выполнения)")  
  
## <a name="the-design-time-component"></a>Компонент времени разработки  
 Компонент времени разработки позволяет определять пользовательский элемент отчета и управлять этим элементом в интерфейсе конструктора отчетов в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Компонент времени разработки состоит из нескольких вложенных элементов управления, которые контролируют внешний вид и свойства пользовательского элемента отчета в среде проектирования.  
  
 ![Пользовательский элемент отчета (компонент времени разработки)](../../../2014/reporting-services/media/customreportitemdesign-timecomponentarchitecture.gif "Пользовательский элемент отчета (компонент времени разработки)")  
  
## <a name="see-also"></a>См. также:  
 [Создание компонента времени выполнения пользовательского элемента отчета](../custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Создание компонента времени разработки пользовательского элемента отчета](../custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Как развернуть пользовательский элемент отчета](../custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
