---
title: "DLL-библиотеки перевода | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- translation DLLs [ODBC]
ms.assetid: 38975059-b346-410f-bb27-326f3f7bbf39
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 06e496e3999904a019f481374598a9a774729ab3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="translation-dlls"></a>Преобразование библиотеки DLL
Приложения и источника данных часто хранятся в различных наборов символов. ODBC предоставляет общий механизм, который позволяет драйверу преобразовать данные из одной кодировки в другую. Он состоит из библиотеки DLL, которая реализует функции преобразования **трансляции SQLDriverToDataSource** и **SQLDataSourceToDriver**, которые вызываются драйвером для преобразования всех данных, передаваемых между источника данных и драйвер. Эта библиотека DLL могут быть записаны разработчиком приложения, разработчик драйвера или третьей стороны.  
  
 Перевод DLL для конкретного источника данных может быть указано в сведениях о системе для этого источника данных; Дополнительные сведения см. в разделе [подразделов спецификации источника данных](../../../odbc/reference/install/data-source-specification-subkeys.md). Его также можно установить во время выполнения с помощью атрибутов соединения SQL_ATTR_TRANSLATE_DLL и SQL_ATTR_TRANSLATE_OPTION.  
  
 Параметр миграции является значение, которое может интерпретировать только определенной перевод DLL. Например если перевод DLL преобразовывает разные кодовые страницы, параметр дать номера кодовых страниц, используемых приложением, а источник данных. Нет необходимости для перевода DLL необходимо использовать параметр перевода.  
  
 После перевода указаны библиотеки DLL драйвер загружается и вызывается для преобразования всех данных, передаваемых между приложением и источником данных. Сюда входят все инструкции SQL и символьные строки, отправляемых в источнике данных и все результаты символа, символа метаданные, такие как имена столбцов и сообщения об ошибках, получаемые из источника данных. Данные подключения не преобразуются, поскольку преобразование библиотека DLL загружается только после подключения приложения к источнику данных.