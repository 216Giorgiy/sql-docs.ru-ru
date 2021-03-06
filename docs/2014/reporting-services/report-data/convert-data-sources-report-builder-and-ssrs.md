---
title: Преобразование источника данных из внедренного в общий (построитель отчетов и службы SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
- data sources [Reporting Services], shared
ms.assetid: 0e099c7e-8c03-43eb-9ea3-76e52d9ebbe3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: aa7cc2560e5f22d6da60c3784361ad50f85bfbef
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59952140"
---
# <a name="convert-a-data-source-from-embedded-to-shared-report-builder-and-ssrs"></a>Преобразование источника данных из внедренного в общий (построитель отчетов и службы SSRS)
  Каждый источник данных в области данных отчета является внедренным и привязанным к определенному отчету либо общим. В построителе отчетов общий источник данных указывает на опубликованный общий источник данных на сервере отчетов или сайте SharePoint. В конструкторе отчетов общий источник данных указывает на общий источник данных в папке **Общие источники данных** в обозревателе решений.  
  
 Дополнительные сведения о различиях между внедренными и общими источниками данных см. в разделе [Внедренные и общие подключения к данным или источники данных (построитель отчетов и службы SSRS)](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).  
  
 Дополнительные сведения о создании общего источника данных см. в разделе [Создание внедренного или общего источника данных (службы SSRS)](../create-an-embedded-or-shared-data-source-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-designer"></a>конструктор отчетов  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a>Преобразование источника данных из внедренного в общий  
  
-   В области данных отчета щелкните правой кнопкой мыши источник данных и выберите команду **Преобразовать в общий источник данных**.  
  
    > [!NOTE]  
    >  Если область данных отчета не отображается, в меню **Вид** выберите пункт **Данные отчета**. Если панель открывается как плавающее окно, его можно пристыковать. Дополнительные сведения см. в разделе [Закрепление области данных отчета в конструкторе отчетов (службы SSRS)](../tools/dock-the-report-data-pane-in-report-designer-ssrs.md).  
  
     В области данных отчета значок источника данных сменится значком общего источника данных. В обозревателе решений общий источник данных появится с тем же именем в папке **Общий источник данных** .  
  
### <a name="to-convert-a-data-source-from-shared-to-embedded"></a>Преобразование источника данных из общего во внедренный  
  
-   В области данных отчета щелкните правой кнопкой мыши источник данных, откройте диалоговое окно **Свойства источника данных** и выберите параметр **Внедренное соединение**. Введите необходимые данные.  
  
     В области данных отчета значок источника данных сменится значком общего источника данных.  
  
## <a name="report-builder"></a>построитель отчетов  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a>Преобразование источника данных из внедренного в общий  
  
-   В области данных отчета щелкните правой кнопкой мыши источник данных, чтобы открыть диалоговое окно **Свойства источника данных** , и выберите параметр **Внедренное соединение**. Введите необходимые данные.  
  
     В области данных отчета значок источника данных сменится значком общего источника данных.  
  
#### <a name="to-convert-a-data-source-from-shared-to-embedded"></a>Преобразование источника данных из общего во внедренный  
  
-   В области данных отчета щелкните правой кнопкой мыши источник данных, откройте диалоговое окно **Свойства источника данных** и выберите параметр **Внедренное соединение**. Введите необходимые данные.  
  
     В области данных отчета значок источника данных сменится значком общего источника данных.  
  
## <a name="see-also"></a>См. также  
 [Управление источниками данных отчета](manage-report-data-sources.md)   
 [Подключения данных, Источники данных и Строки подключения в службе Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
