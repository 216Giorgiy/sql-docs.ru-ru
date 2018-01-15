---
title: "Метод IBCPSession::BCPControl (OLE DB) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IBCPSession::BCPControl (OLE DB)
apitype: COM
helpviewer_keywords: BCPControl method
ms.assetid: d58f3fe1-45e3-4e46-8e9c-000971829d99
caps.latest.revision: "50"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 72969fb998915015b59e47c602df075921f46a0e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="ibcpsessionbcpcontrol-ole-db"></a>Метод IBCPSession::BCPControl (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Задает параметры для операции массового копирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT BCPControl(   
      int eOption,  
      void *iValue);  
```  
  
## <a name="remarks"></a>Замечания  
 Метод **BCPControl** задает различные параметры управления для операций массового копирования, в том числе количество ошибок, допустимых перед отменой массового копирования, номера первой и последней строк, копируемых из файла данных, и размер пакетов.  
  
 Этот метод также применяется, чтобы указать на использование инструкции SELECT при массовом копировании данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Можно присвоить аргументу **eOption** значение BCP_OPTION_HINTS, а аргументу **iValue** указатель на строку знаков в Юникоде, содержащую инструкцию SELECT.  
  
 Возможные значения параметра *eOption* .  
  
|Параметр|Описание|  
|------------|-----------------|  
|BCP_OPTION_ABORT|Останавливает текущую операцию массового копирования. Можно вызвать метод **BCPControl** с аргументом *eOption* , имеющим значение BCP_OPTION_ABORT, из другого потока, чтобы остановить текущую операцию массового копирования. Аргумент *iValue* не учитывается.|  
|BCP_OPTION_BATCH|Количество строк на пакет. Значение по умолчанию равно 0. Оно обозначает все строки в таблице при извлечении данных или все строки в файле пользовательских данных при копировании данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При значении меньше 1 параметр BCP_OPTION_BATCH принимает значение по умолчанию.|  
|BCP_OPTION_DELAYREADFMT|Логическое значение. Если задано значение true, приведет к [IBCPSession::BCPReadFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md) для чтения во время выполнения. Если false (по умолчанию), IBCPSession::BCPReadFmt будет немедленно считать файл форматирования. Если возникнет ошибка последовательности **BCP_OPTION_DELAYREADFMT** имеет значение true, при вызове метода IBCPSession::BCPColumns или IBCPSession::BCPColFmt.<br /><br /> Ошибка последовательности также возникает при вызове метода `IBCPSession::BCPControl(BCPDELAYREADFMT, (void *)FALSE))` после вызова метода `IBCPSession::BCPControl(BCPDELAYREADFMT, (void *)TRUE)` и IBCPSession::BCPWriteFmt.<br /><br /> Дополнительные сведения см. в разделе [обнаружение метаданных](../../relational-databases/native-client/features/metadata-discovery.md).|  
|BCP_OPTION_FILECP|Аргумент *iValue* содержит номер кодовой страницы для файла данных. Можно указать номер кодовой страницы, такой как 1252 или 850, или одно из следующих значений.<br /><br /> BCP_FILECP_ACP: данные в файле находятся в кодовой странице Microsoft Windows® клиента.<br /><br /> BCP_FILECP_OEMCP: данные в файле находятся в кодовой странице изготовителя оборудования (OEM) клиента (по умолчанию).<br /><br /> BCP_FILECP_RAW: данные в файле находятся в кодовой странице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|BCP_OPTION_FILEFMT|Номер версии для формата файла данных. Может иметь значение 80 ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]), 90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]), 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), 110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) или 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]). 120 используется по умолчанию. Это может оказаться полезным при экспорте или импорте данных в форматах, которые поддерживались прежними версиями сервера.  Например, полученный для импорта данных из текстового столбца на [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] сервера в **varchar(max)** столбца в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии, следует указать значение 80. Аналогично Если указать 80 при экспорте данных из **varchar(max)** столбец, он будет сохранен так же, как сохраняются текстовые столбцы в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] форматирование и могут быть импортированы в текстовый столбец [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] сервера.|  
|BCP_OPTION_FIRST|Первая строка данных копируемого файла или таблицы. Значение по умолчанию равно 1. Если задать для этого параметра значение меньше 1, то будет установлено значение по умолчанию.|  
|BCP_OPTION_FIRSTEX|В операциях bcp out задает первую строку таблицы базы данных для копирования в файл данных.<br /><br /> В операциях bcp in задает первую строку файла данных для копирования в таблицу базы данных.<br /><br /> Параметр *iValue* должен представлять адрес 64-разрядного целого числа со знаком, содержащего значение. Максимальное значение, которое можно передать в BCPFIRSTEX, составляет 2^63-1.|  
|BCP_OPTION_FMTXML|Используется, чтобы указать, что созданный файл форматирования должен быть в формате XML. Отключен по умолчанию, и по умолчанию файлы форматирования сохраняются как текстовые файлы. XML-файл форматирования обеспечивает более высокую гибкость, но связан с некоторыми дополнительными ограничениями. Например, нельзя указать для поля одновременно префикс и признак конца, что было возможно в старых файлах форматирования.<br /><br /> Примечание: Только являются XML-файлы форматирования поддерживаются, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средства устанавливаются вместе с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.|  
|BCP_OPTION_HINTS|Аргумент *iValue* содержит указатель на расширенный символ. Адресуемая строка задает подсказки для обработки массового копирования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)], которая возвращает результирующий набор. Если указана инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)], которая возвращает более одного результирующего набора, все результирующие наборы после первого не учитываются.|  
|BCP_OPTION_KEEPIDENTITY|Когда *iValue* аргумент имеет значение TRUE, этот параметр указывает, что методы массового копирования вставляют значения данных, предоставленные для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбцов, определенных с ограничением identity. Входной файл должен содержать значения для столбцов идентификаторов. Если эти значения не заданы, то для вставляемых строк создаются новые значения идентификаторов. Данные в файле, предназначенные для столбцов идентификаторов, не учитываются.|  
|BCP_OPTION_KEEPNULLS|Указывает, будут ли пустые значения данных в файле преобразовываться в значения NULL в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда *iValue* аргумент имеет значение TRUE, пустые значения будут преобразованы в значение NULL в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы. По умолчанию пустые значения преобразовываются в значения по умолчанию для столбца в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если значение по умолчанию существует.|  
|BCP_OPTION_LAST|Последняя копируемая строка. По умолчанию копируются все строки. При значении менее 1 этот параметр сбрасывается в значение по умолчанию.|  
|BCP_OPTION_LASTEX|В операциях bcp out задает последнюю строку таблицы базы данных для копирования в файл данных.<br /><br /> В операциях bcp in задает последнюю строку файла данных для копирования в таблицу базы данных.<br /><br /> Параметр *iValue* должен представлять адрес 64-разрядного целого числа со знаком, содержащего значение. Максимальное значение, передаваемое в BCPLASTEX, составляет 2^63-1.|  
|BCP_OPTION_MAXERRS|Число ошибок, при достижении которого операция массового копирования завершается неудачей. Значение по умолчанию равно 10. При значении менее 1 этот параметр сбрасывается в значение по умолчанию. В операции массового копирования допускается не более 65 535 ошибок. Если выполнить попытку установить этот параметр в значение, превышающее 65 535, будет установлено значение 65 535.|  
|BCP_OPTION_ROWCOUNT|Возвращает число строк, на которые распространяется действие текущей (или последней) операции bcp.|  
|BCP_OPTION_TEXTFILE|Файл данных является не двоичным, а текстовым файлом. BCP обнаруживает, представлен ли текстовый файл в формате Юникод или нет, проверяя отметку байтов Юникод в первых двух байтах файла данных.|  
|BCP_OPTION_UNICODEFILE|Если установлено значение TRUE, этот параметр указывает, что входной файл представлен в формате Юникода.|  
  
## <a name="arguments"></a>Аргументы  
 *eOption*[in]  
 Задает один из параметров, перечисленных в таблице выше.  
  
 *iValue*[in]  
 Значение для указанного аргумента *eOption*. Аргумент *iValue* является целым значением, приведенным к указателю void, чтобы обеспечить расширение в будущем до 64-разрядных значений.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_FAIL  
 Ошибка поставщика; Дополнительные сведения, используйте [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) интерфейса.  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например [IBCPSession::BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) перед вызовом этой функции не был вызван метод.  
  
 E_OUTOFMEMORY  
 Недостаточно памяти.  
  
## <a name="see-also"></a>См. также:  
 [IBCPSession &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Выполнение операций массового копирования](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  