---
title: "ALTER PROCEDURE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_PROCEDURE_TSQL
- ALTER_PROC_TSQL
- ALTER PROC
- ALTER PROCEDURE
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER PROCEDURE statement
- stored procedure modifications [SQL Server]
- modifying stored procedures
- stored procedures [SQL Server], modifying
ms.assetid: ed9b2f76-11ec-498d-a95e-75b490a75733
caps.latest.revision: 69
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3dc195d3f6ca908253ff5726c3f336435e7f2bd1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-procedure-transact-sql"></a>Инструкция ALTER PROCEDURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Изменяет ранее созданную процедуру с помощью инструкции CREATE PROCEDURE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database
  
ALTER { PROC | PROCEDURE } [schema_name.] procedure_name [ ; number ]   
    [ { @parameter [ type_schema_name. ] data_type }   
        [ VARYING ] [ = default ] [ OUT | OUTPUT ] [READONLY]  
    ] [ ,...n ]   
[ WITH <procedure_option> [ ,...n ] ]  
[ FOR REPLICATION ]   
AS { [ BEGIN ] sql_statement [;] [ ...n ] [ END ] }  
[;]  
  
<procedure_option> ::=   
    [ ENCRYPTION ]  
    [ RECOMPILE ]  
    [ EXECUTE AS Clause ]  
```  
  
```  
-- Syntax for SQL Server CLR Stored Procedure  
  
ALTER { PROC | PROCEDURE } [schema_name.] procedure_name [ ; number ]   
    [ { @parameter [ type_schema_name. ] data_type }   
        [ = default ] [ OUT | OUTPUT ] [READONLY]  
    ] [ ,...n ]   
[ WITH EXECUTE AS Clause ]  
AS { EXTERNAL NAME assembly_name.class_name.method_name }  
[;]  
```  
  
```tsql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER { PROC | PROCEDURE } [schema_name.] procedure_name  
    [ { @parameterdata_type } [= ] ] [ ,...n ]  
AS { [ BEGIN ] sql_statement [ ; ] [ ,...n ] [ END ] }  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *schema_name*  
 Имя схемы, которой принадлежит процедура.  
  
 *procedure_name*  
 Имя процедуры, которую нужно изменить. Имена процедур должны соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md).  
  
 **;**  *номер*  
 Необязательный аргумент целочисленного типа, который применяется для объединения процедур с одинаковым именем и позволяет удалять их одновременно при помощи инструкции DROP PROCEDURE.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 **@***параметр*  
 Параметр в процедуре. Можно указать до 2 100 аргументов.  
  
 [ *type_schema_name***.** ] *data_type*  
 Тип данных аргумента и схема, которой он принадлежит.  
  
 Сведения об ограничениях типов данных см. в разделе [CREATE PROCEDURE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-procedure-transact-sql.md).  
  
 VARYING  
 Указывает результирующий набор, поддерживаемый в качестве выходного параметра. Этот параметр формируется динамически хранимой процедурой, и его содержимое может меняться. Область применения — только аргументы курсора. Этот параметр недопустим для процедур CLR.  
  
 *по умолчанию*  
 Значение по умолчанию для аргумента.  
  
 OUT | OUTPUT  
 Указывает, что параметр является выходным.  
  
 READONLY  
 Указывает, что параметр не может быть обновлен или изменен в тексте процедуры. Если тип параметра является возвращающим табличное значение типом, то должно быть указано ключевое слово READONLY.  
  
 RECOMPILE  
 Указывает, что компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не кэширует план этой процедуры и она перекомпилируется во время выполнения.  
  
 ENCRYPTION  
 **Применяется к**: SQL Server ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) и [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)].  
  
 Показывает, что компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] выполнит затемнение исходного текста инструкции ALTER PROCEDURE. Результат запутывания не виден непосредственно ни в одном представлении каталога [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пользователи, не имеющие доступа к системным таблицам или файлам баз данных, не смогут получить скрытый текст. Тем не менее, текст будет доступен привилегированным пользователям, которые либо смогут обращаться к системным таблицам через [порт выделенного административного Соединения](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md) или непосредственный доступ к файлам базы данных. Кроме того, пользователи, имеющие право на подключение отладчика к серверному процессу, могут получить исходный текст процедуры из памяти во время выполнения. Дополнительные сведения о доступе к системным метаданным см. в разделе [настроек видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
 Процедуры, созданные с помощью этого параметра невозможно публиковать как части [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] репликации.  
  
 Этот параметр не может быть указан в хранимой процедуре среды CLR.  
  
> [!NOTE]  
>  Во время обновления [!INCLUDE[ssDE](../../includes/ssde-md.md)] использует затемненные комментарии, которые хранятся в **sys.sql_modules** для повторного создания процедуры.  
  
 EXECUTE AS  
 Определяет контекст безопасности, в котором должна выполняться хранимая процедура при обращении к ней.  
  
 Дополнительные сведения см. в разделе [Предложение EXECUTE AS (Transact-SQL)](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
 FOR REPLICATION  

  
 Указывает, что хранимые процедуры, созданные для репликации, не могут выполняться на подписчике. Хранимая процедура, созданная с аргументом FOR REPLICATION, используется в качестве фильтра и выполняется только в процессе репликации. Параметры не могут быть объявлены, если указан параметр FOR REPLICATION. Этот параметр недопустим для процедур CLR. Параметр RECOMPILE не учитывается для процедур, созданных с параметром FOR REPLICATION.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 {[BEGIN] *sql_statement* [;] [ ...  *n*  ] [END]}  
 Одна или несколько инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)], составляющих текст процедуры. Инструкции можно заключить в необязательные ключевые слова BEGIN и END. Дополнительные сведения см. в разделах советы и рекомендации, общие замечания и ограничения в [CREATE PROCEDURE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-procedure-transact-sql.md).  
  
 ВНЕШНЕЕ имя *assembly_name***.** *class_name***.** *имя_метода*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает метод [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] хранимая процедура для ссылки на сборки среды CLR. *class_name* должен быть допустимым [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентификатором и существовать как класс в сборке. Если класс имеет имя, уточненное пространством имен используется точка (**.**) для разделения частей пространства имен, имя класса должно быть заключено в квадратные скобки (**[]**) или кавычки (**» «**). Указанный метод класса должен быть статическим.  
  
 По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не производит выполнение кода CLR. Можно создавать, изменять и удалять объекты базы данных, которые ссылаются на модули среды CLR; Однако нельзя выполнять эти ссылки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до включения [параметр clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md). Чтобы включить этот параметр, используйте [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
> [!NOTE]  
>  Процедуры CLR не поддерживаются в автономной базе данных.  
  
## <a name="general-remarks"></a>Общие замечания  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] нельзя преобразовать в хранимые процедуры CLR и наоборот.  
  
 Инструкция ALTER PROCEDURE не изменяет разрешения и не влияет на хранимые процедуры и триггеры. Тем не менее при изменении в хранимую процедуру включаются текущие значения для параметров сеанса QUOTED_IDENTIFIER и ANSI_NULLS. Если при создании хранимой процедуры использовались другие значения параметров, ее поведение может измениться.  
  
 Если предыдущее определение процедуры было создано с параметрами WITH ENCRYPTION или WITH RECOMPILE, эти параметры будут включены только в том случае, если они указаны в инструкции ALTER PROCEDURE.  
  
 Дополнительные сведения о хранимых процедурах см. в разделе [CREATE PROCEDURE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-procedure-transact-sql.md).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Требуется **ALTER** разрешение на процедуру или членство в **db_ddladmin** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается хранимая процедура `uspVendorAllInfo`. Эта хранимая процедура возвращает имена всех поставщиков, которые содержатся в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], товары, которые они производят, оценку кредитоспособности и доступность. После создания процедура изменяется и возвращает другой результирующий набор.  
  
```  
  
IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
    DROP PROCEDURE Purchasing.uspVendorAllInfo;  
GO  
CREATE PROCEDURE Purchasing.uspVendorAllInfo  
WITH EXECUTE AS CALLER  
AS  
    SET NOCOUNT ON;  
    SELECT v.Name AS Vendor, p.Name AS 'Product name',   
      v.CreditRating AS 'Rating',   
      v.ActiveFlag AS Availability  
    FROM Purchasing.Vendor v   
    INNER JOIN Purchasing.ProductVendor pv  
      ON v.BusinessEntityID = pv.BusinessEntityID   
    INNER JOIN Production.Product p  
      ON pv.ProductID = p.ProductID   
    ORDER BY v.Name ASC;  
GO  
  
```  
  
 В следующем примере изменяется хранимая процедура `uspVendorAllInfo`. Здесь удаляется предложение EXECUTE AS CALLER и изменяется текст процедуры, чтобы возвращать только поставщиков, предлагающих указанный товар. Содержимое результирующего набора определяется при помощи функций `LEFT` и `CASE` .  
  
```  
USE AdventureWorks2012;  
GO  
ALTER PROCEDURE Purchasing.uspVendorAllInfo  
    @Product varchar(25)   
AS  
    SET NOCOUNT ON;  
    SELECT LEFT(v.Name, 25) AS Vendor, LEFT(p.Name, 25) AS 'Product name',   
    'Rating' = CASE v.CreditRating   
        WHEN 1 THEN 'Superior'  
        WHEN 2 THEN 'Excellent'  
        WHEN 3 THEN 'Above average'  
        WHEN 4 THEN 'Average'  
        WHEN 5 THEN 'Below average'  
        ELSE 'No rating'  
        END  
    , Availability = CASE v.ActiveFlag  
        WHEN 1 THEN 'Yes'  
        ELSE 'No'  
        END  
    FROM Purchasing.Vendor AS v   
    INNER JOIN Purchasing.ProductVendor AS pv  
      ON v.BusinessEntityID = pv.BusinessEntityID   
    INNER JOIN Production.Product AS p   
      ON pv.ProductID = p.ProductID   
    WHERE p.Name LIKE @Product  
    ORDER BY v.Name ASC;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```   
 Vendor               Product name  Rating    Availability  
-------------------- ------------- -------   ------------  
Proseware, Inc.      LL Crankarm   Average   No  
Vision Cycles, Inc.  LL Crankarm   Superior  Yes  
(2 row(s) affected)`  
```  

## <a name="see-also"></a>См. также:  
 [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [DROP PROCEDURE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-procedure-transact-sql.md)   
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [ВЫПОЛНЕНИЕ AS &#40; Transact-SQL &#41;](../../t-sql/statements/execute-as-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Хранимые процедуры (компонент Database Engine)](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)   
 [sys.Procedures &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md)  
  
  
