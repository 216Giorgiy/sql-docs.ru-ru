---
title: Использование конструктора запросов и представлений с международными данными (визуальные инструменты баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual Database Tools [SQL Server], international data
- queries [SQL Server], international data
- languages [SQL Server], Query and View Designer
- international considerations [SQL Server], Query and View Designer
- Criteria pane
- View Designer, international data
- Query Designer [SQL Server], international data
- localized information in Query and View Designer [SQL Server]
- global considerations [SQL Server], Query and View Designer
- SQL pane [Visual Database Tools]
- multiple language support [SQL Server], Query and View Designer
ms.assetid: 4b51c56f-f902-4e72-b919-e36127369b63
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c4776214176aca7990863491f68f06e934400e02
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315114"
---
# <a name="use-the-query-and-view-designer-with-international-data-visual-database-tools"></a>Использование конструктора запросов и представлений с международными данными (визуальные инструменты для баз данных)
  [Конструктор запросов и представлений](visual-database-tools.md) можно использовать с данными на любом языке и с любой версией операционной системы Windows. Ниже описаны различия, с которыми можно столкнуться при работе, и предоставлены сведения об управлении данными в международных приложениях.  
  
## <a name="localized-information-in-the-criteria-and-sql-panes"></a>Локализованные сведения на панелях критериев и «SQL»  
 Если для создания запроса использовать панель критериев, необходимо ввести данные в формате, соответствующем региональным настройкам Windows компьютера. Например, для поиска данных нужно ввести данные в столбец критериев с использованием любого привычного формата, за исключением следующих форматов.  
  
-   Длинные форматы даты не поддерживаются.  
  
-   Символы валют не должны вводиться на панели критериев.  
  
-   Символы валют не отображаются на панели результатов.  
  
    > [!NOTE]  
    >  На панели результатов можно самостоятельно ввести символ валюты, соответствующий региональным настройкам Windows на компьютере, однако символ будет удален и не отобразится на панели результатов.  
  
-   Унарный минус всегда появляется на левой стороне (например -1) независимо от параметров региональных настроек.  
  
 Наоборот, данные и ключевые слова на панели «SQL» должны всегда быть в формате ANSI (U.S.). Например, в процессе построения запроса конструктор запросов и представлений вставляет форму ANSI для всех ключевых слов SQL, таких как SELECT и FROM. При добавлении элементов к инструкции на панели «SQL» необходимо убедиться, что для элементов используется стандартная форма ANSI.  
  
 При введении на панель критериев данных с использованием местного формата конструктор запросов и представлений автоматически переводит их в формат ANSI на панель «SQL». Например, если региональные настройки установлены на стандартный немецкий, то на панели критериев можно вводить данные в следующем формате: «31.12.96». Однако дата появится на панели SQL в формате ANSI для даты-времени как `{ ts '1996-12-31 00:00:00' }.` Если вводить данные непосредственно на панели SQL, следует использовать формат ANSI.  
  
## <a name="sort-order"></a>Порядок сортировки  
 Порядок сортировки данных в запросе определяется базой данных. Параметры, которые указываются в диалоговом окне региональных настроек Windows, не влияют на порядок сортировки запросов. Однако в рамках любого конкретного запроса можно запросить возврат строк в определенном порядке.  
  
## <a name="using-double-byte-characters"></a>Использование двухбайтовых символов  
 Можно ввести символы двухбайтовой кодировки DBCS для констант и имен объектов базы данных, таких как имена или псевдонимы таблиц и представлений. Символы двухбайтовой кодировки DBCS также можно использовать для имен параметров и символов-маркеров параметров. Однако нельзя использовать символы двухбайтовой кодировки DBCS в элементах языка SQL, например в именах функций или ключевых словах SQL.  
  
## <a name="see-also"></a>См. также  
 [Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  