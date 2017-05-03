---
title: "Получение суммарных или статистических значений для всех строк в таблице | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- summarizing query results
- aggregate functions [SQL Server], summarizing query results
ms.assetid: f5af876e-f937-4110-ba09-07999c35a699
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 734063422cddceb9ac5fb3b1b44b0d64d07f7d6b
ms.lasthandoff: 04/11/2017

---
# <a name="summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools"></a>Получение суммарных или статистических значений для всех строк в таблице (визуальные инструменты для баз данных)
## <a name="aggregate-function"></a>Агрегатная функция
Агрегатные функции позволяют вычислять сумму всех значений, содержащихся в таблице. Например, можно создать запрос наподобие того, что приведен ниже, для отображения общей стоимости всех книг, содержащихся в таблице `titles` :  
  
```  
SELECT SUM(price)  
FROM titles  
```  
  
Создайте несколько агрегатов в одном запросе, используя агрегатные функции для одного или нескольких столбцов. Например, можно создать запрос, вычисляющий общую сумму по столбцу `price` и среднеарифметическое значение столбца `discount` .  
  
В отдельном запросе для одного и того же столбца можно определять несколько статистических операций (подведение общей суммы, подсчет, усреднение). Например, следующий запрос определяет среднеарифметическое значение и общую сумму столбца `price` в таблице `titles` :  
  
```  
SELECT AVG(price), SUM(price)  
FROM titles  
```  
  
Если добавить условия поиска, можно вычислять статистические значения на основе подмножества строк, удовлетворяющих заданному условию.  

**Примечание.** Можно также подсчитать, сколько всего в таблице содержится строк, или строк, удовлетворяющих определенному условию. Дополнительные сведения см. в разделе [Подсчет строк в таблице (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/count-rows-in-a-table-visual-database-tools.md).  
  
  
Если в запросе указано статистическое выражение, то для всех строк в таблице отображается только само это статистическое значение. Например, при подсчете итогового значения столбца `price` в таблице `titles` названия, имена издателей и другие столбцы не отображаются.  
 
 **!** При создании подытогов (например групп) можно выводить значения столбцов для каждой группы. Дополнительные сведения см. в разделе [Группирование строк в результатах запроса (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/group-rows-in-query-results-visual-database-tools.md).  

## <a name="aggregate-values-for-all-rows"></a>Статистическая обработка значений по всем строкам  
  
1.  Убедитесь, что таблица, в которой необходимо вычислить статистическую величину, присутствует на панели диаграмм  
  
2.  Щелкните правой кнопкой мыши фон панели диаграммы, а затем в контекстном меню выберите пункт **Группировать** . [Конструктор запросов и представлений](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) добавляет столбец **Группировать** в сетку на панели критериев.  
  
3.  Добавьте на панель критериев столбец, по которому необходимо вычислить статистическую величину. Убедитесь, что столбец помечен для вывода.  
  
    Конструктор запросов и представлений автоматически назначает суммируемому столбцу псевдоним, который можно заменить более понятным. Дополнительные сведения см. в разделе [Создание псевдонимов столбцов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-column-aliases-visual-database-tools.md).  
  
4.  В столбце сетки **Группировать** выберите нужную агрегатную функцию, например **Sum**, **Avg**, **Min**, **Max**, **Count**. Если необходимо вычислить статистические значения только для уникальных строк результирующего набора, выберите агрегатную функцию с параметром DISTINCT, например **Min Distinct**. Не выбирайте параметры **Группировать**, **Выражение**или **Где**, так как они не применяются при статистической обработке всех строк.  
  
    Конструктор запросов и представлений заменяет указанной агрегатной функцией имя столбца в инструкции, представленной на [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md) . Например, инструкция SQL может иметь такой вид:  
  
    ```  
    SELECT SUM(price)  
    FROM titles  
    ```  
  
5.  Если необходимо создать в запросе несколько статистических выражений, повторите шаги 3 и 4.  
  
    Если в список выводов запроса или в список сортировки добавляется другой столбец, конструктор запросов и представлений автоматически заполняет термин **Группировать** в столбце сетки **Группировать** . Выберите соответствующую агрегатную функцию.  
  
6.  Если необходимо, добавьте условия поиска для задания подмножества строк, для которых вычисляется сумма.  
  
При выполнении запроса на панели результатов отображаются указанные статистические выражения.  
  
> [!NOTE]  
> Конструктор запросов и представлений обслуживает агрегатные функции в инструкции, отображаемой на панели SQL до тех пор, пока режим «Группировать по» явно не будет выключен. Поэтому при изменении типа запроса или изменении состава таблиц и возвращающих табличное значение объектов, присутствующих на панелях диаграмм, конечный запрос может содержать недопустимые агрегатные функции.  
  
## <a name="see-also"></a>См. также:  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
  
