---
title: Интеграция служб Reporting Services с помощью элементов управления ReportViewer | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- ReportViewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cbaa41c75297d62e84cfc808463214d19c4ff8fa
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60157030"
---
# <a name="integrating-reporting-services-using-the-reportviewer-controls"></a>Интеграция служб Reporting Services с помощью элементов управления ReportViewer
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] предоставляет два элемента управления ReportViewer для внедрения в приложения функциональности просмотра отчетов. К ним относятся версия для приложений на базе Windows Forms, а также версия для приложений Web Forms. Эти элементы управления предоставляют одинаковые функциональные возможности, однако каждый из них разработан с учетом особенностей соответствующей среды. Оба элемента управления обрабатывают отчеты, развернутые на сервере отчетов (режим удаленной обработки) или скопированные на компьютер, где еще не установлены службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (режим локальной обработки).  
  
 Элемент управления ReportViewer не включает встроенную поддержку динамической адаптации к разным устройствам с разным разрешением экрана.  
  
## <a name="remote-processing-mode"></a>Удаленный режим обработки  
 Режим удаленной обработки является предпочтительным методом просмотра отчетов, развернутых на сервере отчетов. Режим удаленной обработки предоставляет следующие преимущества.  
  
-   Удаленная обработка является оптимальным решением для выполнения отчетов, поскольку отчеты обрабатываются сервером отчетов.  
  
-   Таким образом, всю обработку выполняет сервер отчетов, поэтому запрос отчета может обрабатываться несколькими серверами отчетов в варианте с масштабированием по горизонтали или многопроцессорным сервером в варианте с масштабированием по вертикали.  
  
 Кроме того, эксплуатация отчетов в удаленном режиме позволяет воспользоваться полным набором функциональных возможностей сервера отчетов, в том числе всеми модулями подготовки к просмотру и обработки данных.  
  
> [!NOTE]  
>  Список модулей, доступных для элемента управления ReportViewer при работе в режиме удаленной обработки, зависит от выпуска служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], установленного на сервере отчетов.  
  
## <a name="local-processing-mode"></a>Локальной режим обработки  
 В режиме локальной обработки предусмотрен альтернативный метод просмотра и подготовки отчетов на тот случай, если службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не установлены. В отличие от удаленной обработки, в данном режиме элементу управления доступно лишь подмножество функциональных возможностей, предоставляемых сервером отчетов. В режиме локальной обработки обработка данных не выполняется элементом управления, а реализуется приложением, в котором размещается отчет. Но обработка отчета выполняется самим элементом управления. В режиме локальной обработки доступны только модули подготовки отчетов в форматах PDF, Excel, Word и в формате изображений.  
  
## <a name="see-also"></a>См. также  
 [Интеграция служб Reporting Services в приложения](../application-integration/integrating-reporting-services-into-applications.md)   
 [Создание отчетов служб SSRS с помощью Visual Studio (блог)](https://jwcooney.com/2015/01/07/ssrs-basics-set-up-visual-studio-to-write-a-new-ssrs-report/)  
  
  
