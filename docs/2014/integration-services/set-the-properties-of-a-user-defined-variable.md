---
title: Установка свойств определяемой пользователем переменной | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- modifying variables
- variables [Integration Services], properties
ms.assetid: f98ddbec-f668-4dba-a768-44ac3ae0536f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4aaac5f66e8c01364419d8d2d9d5e853bf929ef7
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385532"
---
# <a name="set-the-properties-of-a-user-defined-variable"></a>Установка свойств определяемой пользователем переменной
  Чтобы задать свойства определяемой пользователем переменной в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], можно использовать один из следующих способов.  
  
-   Окно «Переменные».  
  
-   Окно «Свойства». **Свойства** окне указаны свойства для настройки переменных, которые недоступны в **переменных** окна: Description, EvaluateAsExpression, Expression, ReadOnly, ValueType и IncludeInDebugDump.  
  
> [!NOTE]  
>  Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предоставляют также набор системных переменных, свойства которых нельзя обновить, за исключением свойства RaiseChangedEvent.  
  
 **Задание выражений в переменных**  
  
 При использовании окна **Свойства** для задания выражений на определяемой пользователем переменной:  
  
-   Значение переменной можно задать с помощью свойства Value или Expression. По умолчанию присваивается свойство EvaluateAsExpression `False` и значение переменной задается значение свойства. Чтобы использовать выражения для задания значения, необходимо сначала установить свойство EvaluateAsExpression в `True`, а затем указать выражение в свойстве Expression. Свойство Value автоматически устанавливается в значение результата выражения.  
  
-   Свойство ValueType содержит тип данных значения свойства Value. Если свойство Value задается с помощью выражения, свойство ValueType автоматически обновляется типом данных, совместимым с результатом вычисления выражения. Например, если значение содержит 0, а свойство ValueType содержит **Int32** и затем свойству Expression присваивается GETDATE(), значение содержит текущую дату и время, и свойство ValueType устанавливается в `DateTime`.  
  
-   Окно **Свойства** для переменной предоставляет доступ к диалоговому окну **Построитель выражений** . Это средство можно использовать для построения, проверки и вычисления выражений. Дополнительные сведения см. в разделах [Построитель выражений](expressions/expression-builder.md) и [Выражения служб Integration Services (SSIS)](expressions/integration-services-ssis-expressions.md).  
  
 При использовании окна **Переменные** для задания выражений на определяемой пользователем переменной:  
  
-   Чтобы использовать выражения для задания значения переменной, сначала убедитесь, что тип данных переменной совместим с результатом вычисления выражения, а затем указать выражение в `Expression` столбец **переменных** окна. Свойство EvaluateAsExpression в **свойства** окно автоматически присваивается `True`.  
  
-   При присваивании выражения переменной рядом с переменной отображается специальный маркер значка. Этот специальный маркер значка отображается также рядом с диспетчерами соединений и задачами, для которых заданы выражения.  
  
-   Окно **Переменные** для переменной предоставляет доступ к диалоговому окну **Построитель выражений** . Это средство можно использовать для построения, проверки и вычисления выражений. Дополнительные сведения см. в разделах [Построитель выражений](expressions/expression-builder.md) и [Выражения служб Integration Services (SSIS)](expressions/integration-services-ssis-expressions.md).  
  
 В обоих **переменных** и **свойства** окна, если переменной назначено выражение и `EvaluateAsExpression` присваивается `True`, невозможно изменить тип данных переменной.  
  
 **Установка свойств имя и пространство имен**  
  
 Первым символом в значениях свойств `Name` и `Namespace` согласно стандарту Юникод 2.0 должна быть буква или символ подчеркивания (_). Далее могут следовать буквы или цифры по определению стандарта Юникод 2.0 или символ подчеркивания (\_).  
  
## <a name="using-the-variables-window-to-set-properties"></a>Использование окна «Переменные» для задания значений свойств  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-variables-window"></a>Задание свойств переменной с помощью окна «Переменные»  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  В окне обозревателя решений щелкните пакет правой кнопкой мыши для его открытия.  
  
3.  В меню **Службы SSIS** щелкните **Переменные**.  
  
     При необходимости окно **Переменные** можно открыть, назначив команде View.Variables нужное сочетание клавиш на странице **Клавиатура** диалогового окна **Параметры** .  
  
4.  При желании в окне **Переменные** выберите **Параметры сетки**, а затем выберите столбцы для отображения в окне **Переменные** и выберите фильтры для списка переменных.  
  
5.  Выберите переменную в списке, а затем обновите значения в `Name`, **тип данных**, `Value`, `Namespace`, **создать событие изменения**, **описание,** и `Expression` столбцов.  
  
6.  Выберите переменную из списка, а затем нажмите **Переместить переменную** для изменения области.  
  
7.  Чтобы сохранить измененный пакет, в меню **Файл** выберите команду **Сохранить выбранные элементы**.  
  
## <a name="using-the-properties-window-to-set-properties"></a>Использование окна «Свойства» для задания значений свойств  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-properties-window"></a>Задание свойств переменной с помощью окна «Свойства»  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  В окне обозревателя решений щелкните пакет правой кнопкой мыши для его открытия.  
  
3.  В меню **Просмотр** выберите пункт **Окно свойств**.  
  
4.  В конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] перейдите на вкладку **Обозреватель пакетов** и разверните узел пакета.  
  
5.  Чтобы изменить переменные в области пакета, разверните узел «Переменные» или разворачивайте узлы «Обработчики событий» или «Исполняемые объекты», пока не обнаружите узел «Переменные» с переменной, которую необходимо изменить.  
  
6.  Щелкните переменную, свойства которой необходимо изменить.  
  
7.  В окне **Свойства** обновите свойства переменной для чтения/записи. Для переменных, определяемых пользователем, некоторые свойства отображаются только для чтения.  
  
     Дополнительные сведения о свойствах см. в разделе [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).  
  
8.  Чтобы сохранить измененный пакет, в меню **Файл** выберите команду **Сохранить выбранные элементы**.  
  
## <a name="see-also"></a>См. также  
 [Переменные в службах Integration Services (SSIS)](integration-services-ssis-variables.md)   
 [Использование переменных в пакетах](../../2014/integration-services/use-variables-in-packages.md)   
 [Добавление, удаление и изменение области определяемой пользователем переменной в пакете](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
