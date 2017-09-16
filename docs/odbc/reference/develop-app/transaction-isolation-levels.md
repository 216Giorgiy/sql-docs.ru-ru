---
title: "Уровни изоляции транзакций | Документы Microsoft"
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
- dirty reads [ODBC]
- isolation levels [ODBC]
- nonrepeatable reads [ODBC]
- read uncommitted [ODBC]
- read committed [ODBC]
- serializable reads [ODBC]
- phantoms [ODBC]
- transaction isolation [ODBC]
- repeatable reads [ODBC]
- transactions [ODBC], isolation
ms.assetid: 0d638d55-ffd0-48fb-834b-406f466214d4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 13997d3c8d4bb3c4ea5ff47ec6e8d4c95b303d21
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="transaction-isolation-levels"></a>Уровни изоляции транзакций
*Уровни изоляции транзакций* — это мера степень изоляции для транзакций выполняется успешно. Уровни изоляции транзакций, в частности, определяются с наличие или отсутствие следующих явлений.  
  
-   **"Грязный" операций чтения** A *«грязное» чтение* возникает, когда транзакция считывает данные, которые еще не были зафиксированы. Например предположим, что транзакция 1 обновляет строку. Транзакция 2 считывает обновленная строка до фиксации транзакции 1 обновление. Если 1 отката транзакции изменения транзакции 2 будет считывать данные, которые считаются никогда не должен существовать.  
  
-   **Неповторяющееся чтение** A *неповторяющееся чтение* возникает, когда транзакция считывает ту же строку дважды, но возвращает разные данные каждый раз. Предположим, например, транзакция 1 считывает строку. Транзакция 2 обновляет или удаляет этой строки и фиксирует инструкции update или delete. Если транзакция 1 заново считывает строки, он извлекает значения разных строк или обнаруживает, что строка была удалена.  
  
-   **Фантомов** A *фантомных* строки, соответствующие условиям поиска, но не обнаружена изначально. Например предположим, что транзакция 1 считывает набор строк, удовлетворяющих условию некоторые условия поиска. Транзакция 2 создает новую строку (с помощью обновления или вставки), соответствующий условиям поиска для транзакции 1. Если транзакция 1 reexecutes инструкцию, которая считывает строки, она возвращает набор строк.  
  
 Уровни изоляции транзакций четыре (как определено SQL-92) определяются с точки зрения следующих явлений. В следующей таблице «X» помечает каждый явление, которое может произойти.  
  
|Уровень изоляции транзакции|«Грязные» чтения|Неповторяющееся чтение|Фантомов|  
|---------------------------------|-----------------|-------------------------|--------------|  
|Уровень изоляции read uncommitted|X|X|X|  
|Уровень изоляции read committed|--|X|X|  
|Уровень изоляции repeatable read|--|--|X|  
|Упорядочиваемый уровень изоляции|--|--|--|  
  
 В следующей таблице описаны довольно просто, что СУБД могут быть реализованы уровни изоляции транзакций.  
  
> [!IMPORTANT]  
>  Большинство СУБД использовать более сложные схемы, чем они для повышения параллелизма. Эти примеры предназначены только для демонстрационных целей. В частности, ODBC не определить как определенной СУБД изолирует транзакции друг от друга.  
  
|Уровень изоляции транзакции|Возможная реализация|  
|---------------------------|-----------------------------|  
|Уровень изоляции read uncommitted|Транзакции не изолированы друг от друга. Если СУБД это поддерживает другие уровни изоляции транзакций, он игнорирует любой механизм, который используется для реализации этих уровней. Чтобы они негативное влияние на другие транзакции, транзакциях, выполняемых на уровне изоляции Read Uncommitted, обычно доступные только для чтения.|  
|Уровень изоляции read committed|Транзакция ожидает, пока разблокируются записи заблокированные другими транзакциями строк; Это предотвращает чтение «грязных» данных.<br /><br /> Содержит транзакции, блокировки чтения (если только он считывает строку) или запись блокировки на текущей строке, чтобы предотвратить другими транзакциями, обновлять или удалять его (если он обновляет или удаляет строку). Транзакция освобождает блокировку считывания, когда он перемещается за пределы текущей строки. Она содержит записи блокировок до фиксации или отката.|  
|Уровень изоляции repeatable read|Транзакция ожидает, пока разблокируются записи заблокированные другими транзакциями строк; Это предотвращает чтение «грязных» данных.<br /><br /> Транзакция удерживает блокировку чтения всех строк, он возвращает блокировки приложения и записи для всех строк, он операций вставки, обновления или удаления. Например, если транзакция содержит инструкцию SQL **ВЫБЕРИТЕ \* заказы из**, блокировки транзакций, чтения строк, как приложение извлекает их. Если транзакция содержит инструкцию SQL **удалить из КОТОРЫХ состояние заказов = «CLOSED»**, запись блокировки транзакций строк как удаляет их.<br /><br /> Поскольку другие транзакции не может обновить или удалить эти строки, текущая транзакция позволяет избежать любой неповторяющееся чтение. Транзакция освобождает свои блокировки, при фиксации или отката.|  
|Упорядочиваемый уровень изоляции|Транзакция ожидает, пока разблокируются записи заблокированные другими транзакциями строк; Это предотвращает чтение «грязных» данных.<br /><br /> Транзакция удерживает блокировку чтения (если только он считывает строки) или блокировку записи (если оно могло обновить или удалить строки) диапазон строк влияет на. Например, если транзакция содержит инструкцию SQL **ВЫБЕРИТЕ \* заказы из**, диапазон — от всего таблицу Orders; транзакция чтения блокировки таблицы и не допускает никакие новые строки вставляются в его. Если транзакция содержит инструкцию SQL **удалить из КОТОРЫХ состояние заказов = «CLOSED»**, диапазон включает все строки с состоянием «ЗАКРЫТО»; записи блокировки транзакций все строки в заказах таблицы с состоянием «CLOSED» и не не Разрешить все строки вставлять или обновлять таким образом, что результирующей строке находится в состоянии «ЗАКРЫТО».<br /><br /> Поскольку другие транзакции нельзя обновить или удалить строки в диапазоне, текущая транзакция позволяет избежать любой неповторяющееся чтение. Так как другие транзакции не могут вставлять строки в диапазоне, текущая транзакция позволяет избежать любой фантомов. Транзакция освобождает свою блокировку при фиксации или отката.|  
  
 Это важно отметить, что уровень изоляции транзакции не влияет на транзакции возможность просматривать изменения; транзакции могут всегда видеть все изменения, которые они делают. Например, транзакция может состоять из двух **обновление** инструкций, в первом из которых вызывает оплату всех сотрудников на 10 процентов и второй из которых задает зарплате сотрудников через некоторые максимальное в этот период. Он завершается успешно как единую транзакцию, только потому, что второй **обновление** инструкции можно просмотреть результаты первого.