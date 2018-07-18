---
title: Построитель выражений | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionbuilder.f1
helpviewer_keywords:
- Expression Builder dialog box
ms.assetid: 4717ce33-bd4e-44bc-81e0-002de075b4d1
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: be402c290ef355f93147b7aa66d8055c054f52ce
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151135"
---
# <a name="expression-builder"></a>Построитель выражений
  Диалоговое окно **Построитель выражений** используется для создания и редактирования выражения свойства или написания выражения, определяющего значение переменной, с помощью графического интерфейса, содержащего список переменных и встроенные ссылки на функции, приведения типов и операторы, включенные в язык выражений служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Выражение свойства представляет собой выражение, которое присваивается свойству. При вычислении выражения свойство динамически обновляется для использования результатов вычисления выражения. Аналогичным образом, выражение, которое используется в переменной, позволяет присваивать переменной результаты вычисления выражения в качестве нового значения.  
  
 Существует множество способов использования выражений:  
  
-   **Задачи** Обновление строки "Кому", в которую задача "Отправка почты" вставляет хранящийся в переменной адрес электронной почты, или обновление строки "Тема" с помощью объединения строки "Продажи за:" и текущей даты, возвращенной функцией GETDATE.  
  
-   **Переменные** Задание значения переменной, равного текущему месяцу, с помощью выражения, подобного `DATEPART("mm",GETDATE())`, или задание значения строки с помощью объединения строкового литерала и текущей даты с использованием такого выражения, как `"Today's date is " + (DT_WSTR,30)(GETDATE())`.  
  
-   **Диспетчеры соединений** Задание кодовой страницы диспетчера соединений с неструктурированными файлами с помощью переменной, содержащей другой идентификатор кодовой страницы, или указание количества строк в файле данных, которые должны быть пропущены, с помощью ввода положительного числа, такого как 3.  
  
 Дополнительные сведения о написании выражений и использовании выражений свойств см. в разделах [Использование выражений свойств в пакетах](use-property-expressions-in-packages.md) и [Выражения служб Integration Services (SSIS)](integration-services-ssis-expressions.md).  
  
## <a name="options"></a>Параметры  
  
|Термин|Определение|  
|----------|----------------|  
|**Переменные**|Откройте папку **Переменные** и перетащите переменные в окно **Выражение** .|  
|**Математические функции**<br /><br /> **Строковые функции**<br /><br /> **Функции даты/времени**<br /><br /> **Функции работы со значением NULL**<br /><br /> **Приведения типов**<br /><br /> **Операторы**|Откройте папки и перетащите функции, приведения типов и операторы в окно **Выражение** .|  
|**Выражение**|Отредактируйте или введите выражение.|  
|**Рассчитанное значение**|Список результатов вычислений выражения.|  
|**Вычислить значение выражения**|Чтобы просмотреть результаты вычислений выражения, выберите параметр **Вычислить значение выражения** .|  
  
## <a name="see-also"></a>См. также  
 [Страница «выражения»](expressions-page.md)   
 [Редактор выражений свойств](property-expressions-editor.md)   
 [Службы Integration Services &#40;SSIS&#41; переменных](../integration-services-ssis-variables.md)   
 [Системные переменные](../system-variables.md)  
  
  