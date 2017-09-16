---
title: "FULLTEXTCATALOGPROPERTY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FULLTEXTCATALOGPROPERTY_TSQL
- FULLTEXTCATALOGPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- full-text catalogs [SQL Server], properties
- FULLTEXTCATALOGPROPERTY function
- status information [SQL Server], full-text catalogs
ms.assetid: f841dc79-2044-4863-aff0-56b8bb61f250
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 383eafdda02f402d1c398183bfedac6dde85d9ce
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="fulltextcatalogproperty-transact-sql"></a>FULLTEXTCATALOGPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о свойствах полнотекстовых каталогов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FULLTEXTCATALOGPROPERTY ('catalog_name' ,'property')  
```  
  
## <a name="arguments"></a>Аргументы  
  
> [!NOTE]  
>  Следующие свойства будут удалены в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **LogSize** и **PopulateStatus**. Избегайте использовать эти свойства в новых разработках и запланируйте изменение приложений, где они используются в настоящий момент.  
  
 *имя_каталога*  
 Выражение, содержащее имя полнотекстового каталога.  
  
 *Свойство*  
 Выражение, содержащее имя свойства полнотекстового каталога. В таблице перечислены свойства и описания возвращаемых сведений.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|**AccentSensitivity**|Настройка учета диакритических знаков:<br /><br /> 0 = без учета диакритических знаков;<br /><br /> 1 = с учетом диакритических знаков.|  
|**IndexSize**|Логический размер полнотекстового каталога в мегабайтах (МБ). Включает размер индексов семантических ключевых фраз и индексов подобия документов.<br /><br /> Дополнительные сведения см. в подразделе «Примечания» далее в этом разделе.|  
|**ItemCount**|Число проиндексированных элементов, включая все полнотекстовые индексы, индексы ключевых фраз и индексы подобия документов, содержащихся в каталоге|  
|**LogSize**|Поддерживается только для обеспечения обратной совместимости. Всегда возвращает значение 0.<br /><br /> Размер в байтах связанного набора журналов ошибок, связанных с полнотекстовым каталогом [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search Service.|  
|**MergeStatus**|Выполняется ли слияние в единый файл.<br /><br /> 0 = слияние в единый файл не выполняется;<br /><br /> 1 = слияние в единый файл выполняется.|  
|**PopulateCompletionAge**|Разница в секундах между завершением последнего заполнения полнотекстового индекса и 01/01/1990 00:00:00.<br /><br /> Обновляется только для полного и последовательного сканирования. Возвращает значение 0, если заполнение не выполнялось.|  
|**PopulateStatus**|0 = бездействие<br /><br /> 1 = идет полное заполнение<br /><br /> 2 = пауза<br /><br /> 3 = ограниченный режим<br /><br /> 4 = восстановление<br /><br /> 5 = выключение<br /><br /> 6 = идет добавочное заполнение<br /><br /> 7 = построение индекса<br /><br /> 8 = диск заполнен. приостановлено<br /><br /> 9 = отслеживание изменений.|  
|**UniqueKeyCount**|Количество уникальных ключей в полнотекстовом каталоге.|  
|**ImportStatus**|Выполняется ли в настоящее время импорт полнотекстового каталога.<br /><br /> 0 = импорт полнотекстового каталога не выполняется;<br /><br /> 1 = выполняется импорт полнотекстового каталога.|  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="exceptions"></a>Исключения  
 Возвращает значение NULL в случае ошибки или если участник не имеет разрешений для просмотра объекта.  
  
 В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые ему были предоставлены разрешения. Это означает, что встроенные функции, создающие метаданные, такие как FULLTEXTCATALOGPROPERTY, могут вернуть значение NULL в случае, если пользователь не имеет разрешений на объект. Дополнительные сведения см. в разделе [sp_help_fulltext_catalogs &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md).  
  
## <a name="remarks"></a>Замечания  
 FULLTEXTCATALOGPROPERTY ('*catalog_name*«,»**IndexSize**') анализирует только фрагменты с состоянием 4 или 6, указанным в [sys.fulltext_index_fragments](../../relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql.md). Данные фрагменты являются частью логического индекса. Таким образом **IndexSize** свойство возвращает только логический размер индекса. При слиянии индексов фактический размер индекса может в два раза превышать его логический размер. Чтобы найти фактический размер, который поглощается полнотекстового индекса во время слияния, используйте [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md) системной хранимой процедуры. При выполнении этой процедуры анализируются все фрагменты, связанные с полнотекстовым индексом. Если ограничить рост файла полнотекстового каталога и не оставить достаточно места для процесса слияния, заполнение полнотекстового каталога может завершиться ошибкой. В этом случае инструкция FULLTEXTCATALOGPROPERTY ('имя_каталога', 'IndexSize') возвращает значение 0, а сообщение об ошибке записывается в журнал полнотекстовых операций.  
  
 `Error: 30059, Severity: 16, State: 1. A fatal error occurred during a full-text population and caused the population to be cancelled. Population type is: FULL; database name is FTS_Test (id: 13); catalog name is t1_cat (id: 5); table name t1 (id: 2105058535). Fix the errors that are logged in the full-text crawl log. Then, resume the population. The basic Transact-SQL syntax for this is: ALTER FULLTEXT INDEX ON table_name RESUME POPULATION.`  
  
 Очень важно, чтобы приложение не проверяло в непрерывном цикле, проверка **PopulateStatus** свойство бездействия (показывая, что заполнение завершено), так как это отнимает время ЦП от базы данных и полнотекстовые Поиск процессов и причины время ожидания. Кроме того, это обычно лучший параметр для проверки соответствующего **PopulateStatus** свойства на уровне таблицы **TableFullTextPopulateStatus** в системной функции OBJECTPROPERTYEX. Это и другие полнотекстовые свойства в функции OBJECTPROPERTYEX предоставляют более подробные сведения о таблицах с полнотекстовым индексированием. Дополнительные сведения см. в разделе [OBJECTPROPERTYEX (Transact-SQL)](../../t-sql/functions/objectpropertyex-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает количество полнотекстовых индексированных элементов в полнотекстовом каталоге `Cat_Desc`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT fulltextcatalogproperty('Cat_Desc', 'ItemCount');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [FULLTEXTSERVICEPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_help_fulltext_catalogs &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md)  
  
  