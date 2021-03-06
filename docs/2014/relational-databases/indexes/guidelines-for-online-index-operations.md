---
title: Рекомендации по операциям с индексами | Документация Майкрософт
ms.custom: ''
ms.date: 11/11/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- clustered indexes, online operations
- online index operations
- indexes [SQL Server], online operations
- disk space [SQL Server], indexes
- nonclustered indexes [SQL Server], online operations
- transaction logs [SQL Server], indexes
ms.assetid: d82942e0-4a86-4b34-a65f-9f143ebe85ce
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e2f7a25a4a6a4bb6b8f153a8b04b47aeb542265c
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53356207"
---
# <a name="guidelines-for-online-index-operations"></a>Руководящие принципы для операций с индексами
  При выполнении операций с индексами в сети придерживайтесь следующих правил.  
  
-   Кластеризованные индексы должны создаваться, перестраиваться или удаляться автономный режим при базовая таблица содержит следующие типы данных больших объектов (LOB): `image`, **ntext**, и `text`.  
  
-   Индексы локальных временных таблиц не могут создаваться, перестраиваться и удаляться в режиме в сети. Это ограничение не относится к индексам глобальных временных таблиц.  
  
> [!NOTE]  
>  Операции с индексами в режиме "в сети" доступны не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 В следующей таблице перечислены операции с индексами, которые могут быть выполнены в режиме в сети и индексы, которые исключаются из этих операций. Кроме того, в ней указаны дополнительные ограничения.  
  
|Операция с индексами в сети|Исключенные индексы|Прочие ограничения|  
|----------------------------|----------------------|------------------------|  
|ALTER INDEX REBUILD|Отключенный кластеризованный индекс или отключенное индексированное представление<br /><br /> XML-индекс <br /><br />Индекс columnstore<br /><br /> Индекс локальной временной таблицы|Указание ключевого слова ALL может привести к ошибке выполнения операции, если таблица содержит исключенный индекс.<br /><br /> На перестроение отключенных индексов налагаются дополнительные ограничения. Дополнительные сведения см. в статье [Отключение индексов и ограничений](disable-indexes-and-constraints.md).|  
|CREATE INDEX|XML-индекс<br /><br /> Исходные уникальные кластеризованные индексы представлений.<br /><br /> Индекс локальной временной таблицы||  
|CREATE INDEX WITH DROP_EXISTING|Отключенный кластеризованный индекс или отключенное индексированное представление<br /><br /> Индекс локальной временной таблицы<br /><br /> XML-индекс||  
|DROP INDEX|Отключенный индекс<br /><br /> XML-индекс<br /><br /> Некластеризованный индекс<br /><br /> Индекс локальной временной таблицы|В одной инструкции не может быть указано несколько индексов.|  
|ALTER TABLE ADD CONSTRAINT (PRIMARY KEY или ограничение UNIQUE)|Индекс локальной временной таблицы<br /><br /> Кластеризованный индекс|Допускается только одно вложенное предложение за раз. Например: нельзя добавлять и удалять ограничения PRIMARY KEY и UNIQUE в одной и той же инструкции ALTER TABLE.|  
||||  
  
 Базовая таблица не может быть изменена, усечена или удалена, пока не завершилась операция с индексами в сети.  
  
 Настройка параметра ONLINE (ON или OFF), указанная при создании или удалении кластеризованного индекса, относится ко всем перестраиваемым некластеризованным индексам. Например: если кластеризованный индекс построен в режиме в сети с помощью инструкции CREATE INDEX WITH DROP_EXISTING, ONLINE=ON, все связанные с ним некластеризованные индексы также повторно создаются в режиме в сети.  
  
 При создании или перестроении в сети индекса UNIQUE построитель индексов и выполняющаяся одновременно пользовательская транзакция могут попытаться добавить одно и то же значение ключа, нарушая его уникальность. Если строка, введенная пользователем, вставляется в новый индекс прежде, чем исходная строка из таблицы-источника перемещается в новый индекс, операция с индексами вне сети завершится ошибкой.  
  
 С небольшой вероятностью операция с индексами в сети может вызвать взаимоблокировку при работе с базой данных, вызванную работой пользователя или приложения. В этих редких случаях компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] определит жертвой взаимоблокировки активность пользователя или приложения.  
  
 Можно выполнять одновременные фоновые DLL-операции индекса одной таблицы или представления только при создании нескольких некластеризованных индексов либо при реорганизации некластеризованных индексов. Все остальные попытки выполнения операций с индексами в сети завершаются ошибкой. Например: нельзя в режиме в сети создавать новый индекс во время перестроения существующего индекса для этой же таблицы.  
  
 Операцию в сети нельзя выполнить, если индекс содержит столбец с типом больших объектов, и операции в сети в той же транзакции предшествует операция обновления. Для решения этой проблемы проводите операцию в сети либо вне такой транзакции, либо в транзакции, но перед операциями обновления.  
  
## <a name="disk-space-considerations"></a>Рекомендации по месту на диске  
 В общем случае требования к свободному месту на диске при работе с индексами и в режиме в сети и в режиме вне сети одинаковы. Исключением является дополнительное место, необходимое для временного сопоставления индекса. Этот временный индекс применяется в операциях с индексами в сети при создании, перестроении или удалении кластеризованных индексов. Удаление кластеризованного индекса в режиме в сети требует столько же места, сколько и его создание в режиме в сети. Дополнительные сведения см. в статье [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).  
  
## <a name="performance-considerations"></a>Вопросы производительности  
 Хотя операции с индексами в сети допускают одновременную работу пользователей, в этом случае они выполняются тем дольше, чем интенсивнее происходит обновление данных. Обычно операции с индексами в сети выполняются медленнее, чем аналогичные операции вне сети, независимо от текущей интенсивности обновления данных.  
  
 Поскольку и исходная, и целевая структуры обслуживаются во время выполнения операции с индексами в сети, увеличивается потребление ресурсов при вставке, обновлении и удалении, и это увеличение может доходить до двукратного. Это может привести к снижению производительности и повышению нагрузки на систему, особенно ресурсов ЦП. Операции с индексами в сети полностью записываются в журнал.  
  
 Несмотря на то, что рекомендуется выполнять операции с индексами в сети, необходимо предварительно оценить среду и определенные требования. Возможно, оптимальным решением может оказаться переключение в режим вне сети. При этом на время выполнения операции пользователи будут иметь ограниченный доступ к данным, но она быстрее закончится и в итоге займет меньше ресурсов.  
  
 На многопроцессорных компьютерах, где установлен [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], индексные инструкции могут использовать больше процессоров для выполнения операций просмотра и сортировки, связанных с индексной инструкцией, как это делают другие запросы. Можно использовать параметр индекса MAXDOP с целью управления максимальным количеством процессоров, используемых для операции с индексами в сети. В этом случае можно распределить потребляемые операцией с индексом ресурсы таким образом, чтобы не пострадали одновременно работающие пользователи. Дополнительные сведения см. в статье [Настройка параллельных операций с индексами](configure-parallel-index-operations.md). Дополнительные сведения о выпусках SQL Server, поддерживающих параллельные операции с индексами см. в разделе [функции, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Поскольку на финальной фазе удерживаются блокировки S-lock и Sch-M, будьте внимательны при выполнении операций с индексами в сети внутри явно объявленных пользовательских транзакций (например: в блоке BEGIN TRANSACTION...COMMIT), поскольку в этом случае блокировка будет удерживаться до окончания транзакции, мешая одновременной работе пользователей.  
  
 Перестроение индекса в сети может привести к увеличению фрагментации, когда оно выполняется с параметрами `MAX DOP > 1` и `ALLOW_PAGE_LOCKS = OFF` . Дополнительные сведения см. в разделе [как это работает: Перестроение индекса в сети — может привести к увеличению фрагментации](https://blogs.msdn.com/b/psssql/archive/2012/09/05/how-it-works-online-index-rebuild-can-cause-increased-fragmentation.aspx).  
  
## <a name="transaction-log-considerations"></a>Вопросы, касающиеся журнала транзакций  
 Масштабные операции с индексами, выполняемые в режиме в сети или вне сети, могут привести к формированию больших объемов данных, которые вызовут переполнение журнала транзакций. Для гарантии возможности отката операций с индексами журнал транзакций не может быть усечен до завершения операции с индексом, однако может быть выполнено его резервное копирование. Иными словами, журнал транзакций должен иметь достаточно места для сохранения и транзакции операции с индексом и текущих пользовательских транзакций на весь период выполнения операции с индексом. Дополнительные сведения см. в статье [Transaction Log Disk Space for Index Operations](transaction-log-disk-space-for-index-operations.md).  
  
## <a name="related-content"></a>См. также  
 [Об операциях с индексами в сети](how-online-index-operations-work.md)  
  
 [Выполнение операции с индексами в сети](perform-index-operations-online.md)  
  
 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)  
  
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)  
  
  
