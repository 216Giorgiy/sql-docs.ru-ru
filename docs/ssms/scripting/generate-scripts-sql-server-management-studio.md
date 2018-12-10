---
title: Формирование скриптов (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: mathoma
ms.topic: conceptual
ms.assetid: 9711c617-3c68-4e5a-aea3-befc64d51524
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 242e0e0c39ce381a492e1072dcb6934cf5f3e29f
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51643955"
---
# <a name="generate-scripts-sql-server-management-studio"></a>Формирование скриптов (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] предоставляет два механизма формирования скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] . Создать скрипты для нескольких объектов можно с помощью **мастера формирования и публикации скриптов**. Можно также создать скрипты для отдельных или нескольких объектов с помощью меню **Сформировать скрипт как** в **обозревателе объектов**.  

Подробный учебник по созданию скриптов для различных объектов с использованием SQL Server Management Studio (SSMS) см. в разделе [Учебник. Создание скриптов SSMS](https://docs.microsoft.com/sql/ssms/tutorials/scripting-ssms).

  
## <a name="before-you-begin"></a>Перед началом  
 Выберите механизм, который лучше всего соответствует имеющимся требованиям.  
  
###  <a name="GenPubScriptWiz"></a> Мастер формирования и публикации скриптов  
 С помощью **мастера формирования и публикации скриптов** можно создать скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] для нескольких объектов. Этот мастер создает скрипт для всех объектов базы данных или скрипт для подмножества выделенных объектов. Мастер позволяет настраивать различные параметры скрипта, такие как включение разрешений, параметры сортировки, ограничения и т. д. Инструкции по использованию мастера см. в разделе [Мастер формирования и публикации скриптов](../../relational-databases/scripting/generate-and-publish-scripts-wizard.md).  
  
###  <a name="OEScriptAsMenu"></a> Меню "Сформировать скрипт как" в обозревателе объектов  
 Меню **Сформировать скрипт как** в обозревателе объектов служит для создания скрипта для одного объекта, нескольких объектов или нескольких инструкций одного объекта. Можно выбрать один из нескольких типов скрипта, например для создания, изменения или удаления объекта. Сохранить скрипт можно в окне редактора запросов — в файл или в буфер обмена. Скрипт создается в формате Юникода.  
  
##  <a name="ScriptSingleObject"></a> Создание скрипта для одного объекта  
 **Создание скрипта для одного объекта**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, а затем разверните базу данных, содержащую объекты, для которых необходимо создать скрипт.  
  
3.  Разверните категорию объекта. Например, разверните узел **Таблицы** или узел **Представления** .  
  
4.  Щелкните объект правой кнопкой мыши, наведите указатель на пункт **Создать скрипт для \<тип объекта>**, например **Создать скрипт для таблицы**.  
  
5.  Укажите тип скрипта, например **Создать** или **Изменить**.  
  
6.  Выберите расположение для сохранения скрипта, например **Новое окно редактора запросов** или **Буфер обмена**.  

    ![Создание скриптов для таблиц](media/generate-scripts-sql-server-management-studio/scripttable.png)
  
  
 Для создания скрипта для нескольких объектов одной категории можно использовать панель **Подробности** обозревателя объектов.  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, а затем разверните базу данных, содержащую объекты, для которых необходимо создать скрипт.  
  
3.  Разверните узел категории типов объектов, для которых требуется создать скрипт, например узел **Таблицы** .  
  
4.  Откройте панель **Подробности обозревателя объектов** . Для этого нажмите клавишу **F7**или откройте меню **Вид** и выберите пункт **Подробности обозревателя объектов**.  
  
5.  Щелкните левой кнопкой один из объектов, который нужно включить в скрипт.  
  
6.  Удерживая клавишу CTRL, щелкните левой кнопкой второй объект, который необходимо включить в скрипт.  
  
7.  Щелкните правой кнопкой мыши один из выделенных объектов и выберите **Создать скрипт для \<тип объекта>**.  

    ![обозревателе объектов](media/generate-scripts-sql-server-management-studio/objectexplorerdetails.png)
  
  