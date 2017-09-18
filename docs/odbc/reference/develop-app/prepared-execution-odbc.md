---
title: "Выполнение ODBC подготовленной | Документы Microsoft"
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
- prepared execution [ODBC]
- SQL statements [ODBC], prepared execution
- SQL statements [ODBC], executing
ms.assetid: f08c8a98-31ee-48b2-9dbf-6f31c2166dbb
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d6b2437d1958e2583dabb75c0a4c26a2ed472975
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="prepared-execution-odbc"></a>Подготовленное выполнение ODBC
Подготовленное выполнение является эффективным способом выполнение инструкции несколько раз. Инструкция первой компиляции, или *подготовлен,* в плане доступа. План доступа — то выполняются один или более раз через некоторое время. Дополнительные сведения о планах доступа см. в разделе [обработки инструкции SQL](../../../odbc/reference/processing-a-sql-statement.md).  
  
 Подготовленное выполнение часто используется вертикальная и пользовательских приложений для многократного выполнения параметризованных инструкции SQL. Например следующий код подготавливает инструкцию для обновления цен различных частей. Затем выполняется инструкция несколько раз с различными значениями параметров при каждом.  
  
```  
SQLREAL       Price;  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd = 0, PriceInd = 0;  
  
// Prepare a statement to update salaries in the Employees table.  
SQLPrepare(hstmt, "UPDATE Parts SET Price = ? WHERE PartID = ?", SQL_NTS);  
  
// Bind Price to the parameter for the Price column and PartID to  
// the parameter for the PartID column.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,  
                  &PartID, 0, &PartIDInd);  
  
// Repeatedly execute the statement.  
while (GetPrice(&PartID, &Price)) {  
   SQLExecute(hstmt);  
}  
```  
  
 Подготовленное выполнение быстрее, чем прямое выполнение инструкций выполняется более одного раза, в первую очередь потому, что инструкция компилируется только один раз; инструкции, выполняемые прямо, компилируются при каждом выполнении. Подготовленное выполнение также предоставляют сокращение объема сетевого трафика, так как драйвер может отправлять идентификатор плана доступа к источнику данных при каждом инструкция выполняется, а не целую инструкцию SQL, если идентификаторы план доступа поддерживает источника данных.  
  
 Приложение может получить метаданные для результирующего набора после подготовки инструкции и перед его выполнением. Однако возвращать метаданные для подготовленных, невыполненных инструкций расходуется для некоторых драйверов и следует избегать, взаимодействующие приложения, если это возможно. Дополнительные сведения см. в разделе [результирующий набор метаданных](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 Не следует использовать подготовленное выполнение для инструкций, исполняемых один раз. Для таких инструкций это немного медленнее, чем прямое выполнение, поскольку для нее требуется дополнительный вызов функции ODBC.  
  
> [!IMPORTANT]  
>  Фиксация или откат транзакции, либо путем явного вызова **SQLEndTran** или по работе в режиме автоматической фиксации, вызывает некоторые источники данных для удаления планов доступ для всех инструкций в соединении. Дополнительные сведения см. в разделе Параметры SQL_CURSOR_COMMIT_BEHAVIOR и SQL_CURSOR_ROLLBACK_BEHAVIOR в [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание функции.  
  
 Подготовка и выполнение инструкции, приложение:  
  
1.  Вызовы **SQLPrepare** , передавая ей строку, содержащую инструкцию SQL.  
  
2.  Задает значения всех параметров. Фактически можно задать параметры, до или после подготовки инструкции. Дополнительные сведения см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md)далее в этом разделе.  
  
3.  Вызовы **SQLExecute** и выполняет дополнительную обработку, необходимую, таких как извлечение данных.  
  
4.  Повторяет шаги 2 и 3, при необходимости.  
  
5.  Когда **SQLPrepare** вызывается драйвер:  
  
    -   Изменяет инструкцию SQL для использования источника данных грамматику SQL без синтаксический анализ инструкции. Сюда входят, заменив escape-последовательности, рассматриваемые в [Escape-последовательности ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md). Приложение может получить измененные формы инструкции SQL, вызвав **SQLNativeSql**. Если значение атрибута инструкции SQL_ATTR_NOSCAN escape-последовательности не заменяются.  
  
    -   Отправляет инструкцию в источнике данных для подготовки.  
  
    -   Сохраняет возвращаемый доступа идентификатор плана для последующего выполнения (если успешно подготовки) или возвращает все ошибки (если не удалось выполнить подготовку). Ошибки — это синтаксические ошибки, такие как SQLSTATE 42000 (синтаксическая ошибка или нарушение доступа) и семантические ошибки, такие как SQLSTATE 42S02 (базовая таблица или представление не найдены).  
  
        > [!NOTE]  
        >  Некоторые драйверы не возвращать ошибки на этом этапе, но вместо возврата их при выполнении инструкции или при вызове функций каталога. Таким образом **SQLPrepare** может оказаться успешно выполнено, когда на самом деле завершилось ошибкой.  
  
6.  Когда **SQLExecute** вызывается драйвер:  
  
    -   Получает текущие значения параметров и преобразует их при необходимости. Дополнительные сведения см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md)далее в этом разделе.  
  
    -   Отправляет идентификатор плана доступа и значения параметров, преобразованных в источник данных.  
  
    -   Возвращает все ошибки. Это обычно ошибки во время выполнения как SQLSTATE 24000 (недопустимое состояние курсора). Тем не менее некоторые драйверы возвращает синтаксические и семантические ошибки на этом этапе.  
  
 Если источник данных не поддерживает подготовку, драйвер должен выполнить его формированию. Например, драйвер может ничего не делать при **SQLPrepare** вызывается и затем выполнить прямое выполнение инструкции при **SQLExecute** вызывается.  
  
 Если источник данных поддерживает проверку без выполнения синтаксиса, драйвер может отправить инструкции для проверки при **SQLPrepare** вызывается и отправить инструкции для выполнения при **SQLExecute** — вызывается.  
  
 Если драйвер не может эмулировать подготовке инструкции, он содержит инструкцию при **SQLPrepare** вызывается и передает его для выполнения при **SQLExecute** вызывается.  
  
 Так как подготовка эмулированной инструкции не является идеальным, **SQLExecute** может возвращать ошибки, возвращенные обычно **SQLPrepare**.