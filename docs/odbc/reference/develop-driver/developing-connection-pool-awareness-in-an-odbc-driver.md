---
title: "Разработка драйвера ODBC, поддерживающие пула соединений | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c63d5cae-24fc-4fee-89a9-ad0367cddc3e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7b7b550bd24788f30926aaee5ae42a8de79a59c9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="developing-connection-pool-awareness-in-an-odbc-driver"></a>Разработка драйвера ODBC, поддерживающие пула соединений
В этом разделе приведены подробные сведения о разработке драйвер ODBC, который содержит сведения о драйвере следует служб пулов подключений.  
  
## <a name="enabling-driver-aware-connection-pooling"></a>Включение пулов соединений с учетом драйвера  
 Драйвер должен реализовывать интерфейс поставщика службы ODBC (SPI) следующие функции:  
  
-   SQLSetConnectAttrForDbcInfo  
  
-   SQLSetConnectInfo  
  
-   SQLSetDriverConnectInfo  
  
-   SQLGetPoolID  
  
-   SQLRateConnection  
  
-   SQLPoolConnect  
  
-   SQLCleanupConnectionPoolID  
  
 В разделе [Справочник интерфейса поставщика службы ODBC (SPI)](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md) для получения дополнительной информации.  
  
 Драйвер также должен реализовывать следующие существующие функции так, чтобы включить пул учетом драйвера:  
  
|Функция|Дополнительные возможности|  
|--------------|-------------------------|  
|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)<br /><br /> [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)<br /><br /> [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|Поддерживает новый тип дескриптора: SQL_HANDLE_DBC_INFO_TOKEN (см. описание ниже).|  
|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|Поддерживает новый атрибут соединения только для набора: SQL_ATTR_DBC_INFO_TOKEN для сброса соединения (см. описание ниже).|  
  
> [!NOTE]  
>  Устаревшие функции, такие как **SQLError** и **SQLSetConnectOption** не поддерживается для использования пулов соединений с учетом драйвера.  
  
## <a name="the-pool-id"></a>Идентификатор пула  
 Идентификатор пула является идентификатор драйвера указатель длины для представления определенной группы подключений, которые могут быть взаимозаменяемыми. При заданном наборе сведений о соединении, драйвер должны иметь возможность быстро вывести соответствующий идентификатор пула.  
  
 Например идентификатор пула следует кодировать данные имя и учетные данные сервера. Однако имя базы данных не требуется, так как драйвер может иметь возможность повторно использовать соединение, а затем измените базу данных в меньше времени, чем создание нового подключения.  
  
 Драйвер должен определить набор ключевые атрибуты, составляющие идентификатор пула. Значение этих ключевых атрибутов могут поступать из атрибуты соединения, строку соединения и источника данных. Если имеются конфликты в этих источниках, существующей, определяемой драйвером политики разрешения можно использовать для обеспечения обратной совместимости.  
  
 Диспетчер драйверов будет использовать другой пул для другой пул идентификаторов. Все соединения, в том же пуле используются для повторного использования. Диспетчер драйверов никогда не будут повторно использовать подключение с использованием идентификатора другого пула.  
  
 Поэтому драйверы следует назначить Идентификатором уникальный пул для каждой группы соединений с тем же значением, в их определенных ключевых атрибутов. Если драйвер использует тот же идентификатор пула для двух подключений с различными значениями в их ключевых атрибутов, диспетчер драйверов по-прежнему поместить их в том же пуле (диспетчера драйверов ничего не знает о ключевых атрибутов драйвера). Это означает, что драйвер будет необходимо сообщить в диспетчер драйверов, соединение с другим набором ключевых атрибутов можно использовать только внутри [SQLRateConnection функция](../../../odbc/reference/syntax/sqlrateconnection-function.md). Это может привести к снижению производительности, и это не рекомендуется.  
  
 Диспетчер драйверов не будут повторно использовать соединение, выделенных из другой среды драйвера, даже если вся информация о соединении совпадает. Диспетчер драйверов используйте другой пул для другую среду, даже в том случае, если соединение имеет тот же идентификатор пула. Таким образом идентификатор пула является локальной в своей среде драйвера.  
  
 Функция для получения идентификатора пула в драйвере — [SQLGetPoolID функция](../../../odbc/reference/syntax/sqlgetpoolid-function.md).  
  
## <a name="the-connection-rating"></a>Оценка подключения  
 По сравнению с установкой нового соединения, можно получить более высокую производительность, сбросив некоторые сведения о соединении (например, база данных) в составе пула соединений. Таким образом вы не можете имя базы данных в наборе ключевых атрибутов. В противном случае может иметь отдельный пул для каждой базы данных, который не может быть хорошим в приложениях среднего уровня, где клиенты использовать различные различные строки подключения.  
  
 Каждый раз, когда вы повторно использовать подключения с некоторые несоответствия атрибут, необходимо переустановить непарные атрибуты, основанные на запрос нового приложения, таким образом, возвращенное подключение идентичен запросу приложения (см. обсуждение атрибута SQL_ATTR _DBC_INFO_TOKEN в [SQLSetConnectAttr, функция](http://go.microsoft.com/fwlink/?LinkId=59368)). Тем не менее Сброс этих атрибутов может привести к снижению производительности. Например сброс базы данных требует вызова по сети к серверу. Таким образом повторно использовать соединения, который полностью соответствует, если он доступен.  
  
 Функция оценки в драйвере можно оценить существующее соединение с нового запроса на подключение. Например можно определить драйвер оценка функции:  
  
-   Если существующее подключение полностью совпадает с запросом.  
  
-   Если есть только некоторые незначащие несоответствия, такие как время ожидания подключения, не требующие обмена данными с сервером для сброса.  
  
-   Если существуют некоторые несоответствия атрибуты, которые требуется связь с сервером для сброса, но по-прежнему приведет к появлению лучшую производительность, чем при установке нового подключения.  
  
-   Несоответствие произошло ли атрибута, что занимает очень много времени сбросить (разработчик драйвера может потребоваться дополнительный этот атрибут в набор ключевых атрибутов, который используется для создания идентификатора пула).  
  
 Оценка от 0 до 100 — возможно, где 0 означает. не используйте и 100% означает вполне соответствует. [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md) — это функция для оценки соединения.  
  
## <a name="new-odbc-handle---sqlhandledbcinfotoken"></a>Новый дескриптор ODBC - SQL_HANDLE_DBC_INFO_TOKEN  
 Чтобы обеспечить поддержку пулов соединений с учетом драйвера, этот драйвер должен сведения о соединении для вычисления идентификатор пула. Этот драйвер должен также сведения о соединении для сравнения новых запросов на подключение с помощью соединения в пуле.  Каждый раз, когда может быть повторно использован без соединения в пуле, драйвер должен установить новое соединение, что требует сведений о соединении.  
  
 Так как сведения о соединении могут поступать из нескольких источников (строка подключения, атрибуты соединения и источника данных), драйвер может потребоваться выполнить синтаксический анализ строки соединения и разрешить конфликт между эти источники в каждом из приведенного выше вызова функции.  
  
 Таким образом, вводится новый дескриптор ODBC: SQL_HANDLE_DBC_INFO_TOKEN. С SQL_HANDLE_DBC_INFO_TOKEN драйвер не требуется обработать строку подключения и разрешение конфликтов в сведения о соединении более одного раза. Так как это структуры данных, драйвер может хранить данные, такие как сведения о соединении или пула идентификатор.  
  
 Этот маркер используется только как интерфейс между диспетчером драйверов и драйверов. Приложение не может выделить этот дескриптор напрямую.  
  
 Дескриптор родительского этого дескриптора относится к типу SQL_HANDLE_ENV, это означает, что драйвер может получить сведения о среде из дескриптора HENV во время разрешения сведения для соединения.  
  
 Каждый раз, когда он получает новый запрос на соединение, диспетчер драйверов выделит дескриптор типа SQL_HANDLE_DBC_INFO_TOKEN для хранения сведения о соединении, после того, подтверждает, что драйвер поддерживает осведомленности пула соединений. После завершения использования дескриптора (но до возвращения некоторые возвращают коды от SQL_STILL_EXECUTING из [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) или [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), диспетчер драйверов, чтобы освободить дескриптор. Таким образом дескриптор создается после вызова метода SQLAllocHandle и уничтожается после вызова метода SQLFreeHandle. Диспетчер драйверов гарантирует дескриптор будет освобождена до снятия его связанный HENV (когда [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) или [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) возвращает сообщение об ошибке).  
  
 Драйвер следует изменить для приема новый дескриптор типа SQL_HANDLE_DBC_INFO_TOKEN следующие функции:  
  
1.  [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
2.  [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
3.  [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
4.  [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
 Диспетчер драйверов гарантирует, что несколько потоков не будет использовать один и тот же дескриптор SQL_HANDLE_DBC_INFO_TOKEN одновременно. Таким образом модель синхронизации этого дескриптора может быть очень простым в драйвере. Диспетчер драйверов не будет блокировки среды до выделения и освобождения SQL_HANDLE_DBC_INFO_TOKEN.  
  
 Диспетчер драйверов **SQLAllocHandle** и **SQLFreeHandle** не принимает этот новый тип дескриптора.  
  
 SQL_HANDLE_DBC_INFO_TOKEN могут содержать конфиденциальную информацию, например учетные данные. Таким образом, драйвер должен безопасно очистить буфер памяти (с помощью [SecureZeroMemory](http://msdn.microsoft.com/library/windows/desktop/aa366877\(v=vs.85\).aspx)), содержащий конфиденциальную информацию, перед тем как освободить этот дескриптор с **SQLFreeHandle**. При закрытии дескриптора среды приложения все пулы связанное соединение будет закрыто.  
  
## <a name="driver-manager-connection-pool-rating-algorithm"></a>Оценка алгоритм пула соединений диспетчер драйверов  
 В этом разделе рассматриваются алгоритма оценки для организации пулов соединений диспетчера драйверов. Разработчики могут реализовывать один и тот же алгоритм для обеспечения обратной совместимости. Этот алгоритм нельзя лучшее из них. Следует уточнить это алгоритм на основе реализации (в противном случае, нет причин для реализации этой возможности).  
  
 Диспетчер драйверов вернет целый оценка от 0 до 100 для каждого подключения из пула. 0 означает соединение не может быть повторно и 100 показывает, соответствует прекрасно. Предположим, запрос на соединение называется hRequest и hCandidate называется существующее подключение из пула. Если один из следующих условий равно false, соединение пула hCandidate нельзя использовать повторно для hRequest (диспетчера драйверов назначит оценка от 0).  
  
-   hCandidate и hRequest поступать из API ЮНИКОДА (например, SQLDriverConnectW) или API ANSI (например, SQLDriverConnectA). (Драйверы ЮНИКОДА можно поведение различных ANSI API и Юникод API (см. атрибут соединения SQL_ATTR_ANSI_APP)).  
  
-   hCandidate и hRequest создаются с одной и той же функции; SQLDriverConnect или SQLConnect.  
  
-   Строка подключения, используемая для открытия hCandidate должно совпадать с hRequest, при использовании SQLDriverConnect.  
  
-   Имя сервера (или DSN), имя пользователя и пароль, используемый для открытия hCandidate должны быть одинаковыми, используемую для открытия hRequest при использовании SQLConnect.  
  
-   Идентификатор безопасности (SID) текущего потока должен совпадать с SID используется для открытия hCandidate.  
  
-   Для драйвера затратна прикрепить, а также исключить соединение из оно (см. в обсуждении SQL_DTC_TRANSITION_COST в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), повторное использование *hRequest* не должен требовать дополнительных зачисление или unenlistment.  
  
 В следующей таблице показаны назначение оценки для различных сценариев.  
  
|Сравнение атрибутов соединения между соединения и запроса|Не было / unenlistment|Требуется дополнительное присоединение / Unenlistment|  
|---------------------------------------------------------------------------------------|-----------------------------------|----------------------------------------------|  
|Другой каталог (SQL_ATTR_CURRENT_CATALOG)|60|50|  
|Некоторые атрибуты соединения различаются, а каталог совпадает с|90|70|  
|Все атрибуты соединения полностью соответствует|100|80|  
  
## <a name="sequence-diagram"></a>Диаграмма последовательностей  
 Эта схема последовательностей показывает базовый механизм регулирования количества запросов, описанные в этом разделе. Отображаются только использование [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) , но [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) случай аналогичен.  
  
 ![Схема последовательностей](../../../odbc/reference/develop-driver/media/odbc_seq_dia.gif "odbc_seq_dia")  
  
## <a name="state-diagram"></a>Диаграмма состояния  
 Это Схема состояний показывает сведения маркера объект подключения, описанные в этом разделе. На диаграмме показаны только [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) , но [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) случай аналогичен. Поскольку диспетчер драйверов может потребоваться для обработки ошибок в любое время, можно вызвать диспетчер драйверов [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md) для любого штата.  
  
 ![Диаграмма состояния](../../../odbc/reference/develop-driver/media/odbc_state_diagram.gif "odbc_state_diagram")  
  
## <a name="see-also"></a>См. также:  
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Справочник по интерфейсу службы доступа (SPI) ODBC](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)