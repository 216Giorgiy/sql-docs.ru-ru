---
title: Имена участника-службы (SPN) в клиентских соединениях (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: e212010e-a5b6-4ad1-a3c0-575327d3ffd3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ae38f4258c965a3b4aedf18ed6261134bd00ac6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108684"
---
# <a name="service-principal-names-spns-in-client-connections-ole-db"></a>Имена участника-службы в клиентских соединениях (OLE DB)
  В этом разделе описываются свойства OLE DB и функции элементов, поддерживающие имена участника-службы (SPN) в клиентских приложениях. Дополнительные сведения о имена участников-служб в клиентских приложениях, см. в разделе [имени участника-службы &#40;имени участника-службы&#41; поддержка в клиентских соединениях](../features/service-principal-name-spn-support-in-client-connections.md). Пример, см. в разделе [встроенную проверку подлинности Kerberos &#40;OLE DB&#41;](../../native-client-ole-db-how-to/integrated-kerberos-authentication-ole-db.md).  
  
## <a name="provider-initialization-string-keywords"></a>Ключевые слова строки инициализации поставщика  
 Следующие ключевые слова строки инициализации поставщика поддерживают имена участников-служб в приложениях OLE DB. В следующей таблице значения в столбце ключевых слов используются строкой поставщика, в котором IDBInitialize::Initialize. Значения в столбце описания используются в строках инициализации при подключении с использованием ADO или IDataInitialize::GetDataSource.  
  
|Ключевое слово|Описание|Значение|  
|-------------|-----------------|-----------|  
|ServerSPN|Имя участника-службы сервера|Имя участника-службы для сервера. Значением по умолчанию является пустая строка, и в этом случае собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, создаваемое поставщиком.|  
|FailoverPartnerSPN|Имя участника-службы партнера по обеспечению отработки отказа|Имя участника-службы для партнера по обеспечению отработки отказа. Значением по умолчанию является пустая строка, и в этом случае собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, создаваемое поставщиком.|  
  
## <a name="data-source-initialization-properties"></a>Свойства инициализации источника данных  
 Следующие свойства набора свойств `DBPROPSET_SQLSERVERDBINIT` позволяют приложениям указывать имена участников-служб.  
  
|Имя|Тип|Использование|  
|----------|----------|-----------|  
|SSPROP_INIT_SERVERSPN|VT_BSTR, чтение и запись|Задает имя участника-службы для сервера. Значением по умолчанию является пустая строка, и в этом случае собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, создаваемое поставщиком.|  
|SSPROP_INIT_FAILOVERPARTNERSPN|VT_BSTR, чтение и запись|Указывает имя участника-службы для партнера по обеспечению отработки отказа. Значением по умолчанию является пустая строка, и в этом случае собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, создаваемое поставщиком.|  
  
## <a name="data-source-properties"></a>Свойства источника данных  
 Следующие свойства набора свойств `DBPROPSET_SQLSERVERDATASOURCEINFO` позволяют приложениям распознавать метод проверки подлинности.  
  
|Имя|Тип|Использование|  
|----------|----------|-----------|  
|SSPROP_INTEGRATEDAUTHENTICATIONMETHOD|VT_BSTR, только для чтения|Возвращает метод проверки подлинности, используемый для соединения. Приложению возвращается значение, которое Windows возвращает собственному клиенту [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Возможные следующие значения.<br /><br /> -«NTLM», который возвращается при открытии соединения с использованием проверки подлинности NTLM.<br />-«Kerberos», который возвращается при открытии соединения с использованием проверки подлинности Kerberos.<br /><br /> Если при открытом соединении нельзя определить метод проверки подлинности, то возвращается значение VT_EMPTY.<br /><br /> Это свойство доступно для чтения только в том случае, если инициализирован источник данных. При попытке считывания свойства до инициализации источника данных, IDBProperties::GetProperies возвращает DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURRED, соответствующим образом и будет установлено значение DBPROPSTATUS_NOTSUPPORTED DBPROPSET_PROPERTIESINERROR для этого свойства. Это поведение соответствует основной спецификации OLE DB.|  
|SSPROP_MUTUALLYAUTHENICATED|VT_BOOL, только для чтения|Если при соединении серверов была выполнена взаимная проверка подлинности, возвращает значение VARIANT_TRUE. В противном случае возвращает VARIANT_FALSE.<br /><br /> Это свойство доступно для чтения только в том случае, если инициализирован источник данных. При попытке считывания свойства до инициализации источника данных IDBProperties::GetProperies возвращает DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURRED, соответствующим образом и будет установлено значение DBPROPSTATUS_NOTSUPPORTED DBPROPSET_ PROPERTIESINERROR для этого свойства. Это поведение соответствует основной спецификации OLE DB.<br /><br /> Если этот атрибут запрашивается соединением, не использующим проверку подлинности Windows, возвращается значение VARIANT_FALSE.|  
  
## <a name="ole-db-api-support-for-spns"></a>Поддержка OLE DB API для имен участников-служб  
 В следующей таблице описываются функции-члены OLE DB, поддерживающие имена участников-служб в клиентских соединениях.  
  
|Функция-член|Описание|  
|---------------------|-----------------|  
|IDataInitialize::GetDataSource|*pwszInitializationString* может содержать новые ключевые слова `ServerSPN` и `FailoverPartnerSPN`.|  
|IDataInitialize::GetInitializationString|Если свойства SSPROP_INIT_SERVERSPN и ssprop_init_failoverpartnerspn не имеют значения по умолчанию, они будут включены в строку инициализации с помощью *ppwszInitString* виде ключевых слов для `ServerSPN` и `FailoverPartnerSPN`. В противном случае эти ключевые слова не будут включены в строку инициализации.|  
|IDBInitialize::Initialize|Если запрос включается путем установки свойства DBPROP_INIT_PROMPT в свойствах инициализации источника данных, будет отображаться диалоговое окно входа OLE DB. Это позволяет ввести имена участников-служб как для основного сервера, так и для его партнера по обеспечению отработки отказа.<br /><br /> Строка поставщика в свойстве DPPROP_INIT_PROVIDERSTRING, если установлена, будет распознавать новые ключевые слова `ServerSPN` и `FailoverPartnerSPN` и использовать их значения, в том случае, если он имеется, для инициализации свойств SSPROP_INIT_SERVER_SPN и SSPROP_INIT_FAILOVER_PARTNER_SPN.<br /><br /> Чтобы установить свойства SSPROP_INIT_SERVER_SPN и SSPROP_INIT_FAILOVER_PARTNER_SPN до вызова IDBInitialize::Initialize может вызываться IDBProperties::SetProperties. Это является альтернативой использованию строки поставщика.<br /><br /> Если свойство устанавливается в нескольких местах, заданное программно значение имеет приоритет над значением, указанным в строке поставщика. Значение, заданное в строке инициализации, имеет приоритет над значением, заданным в диалоговом окне входа.<br /><br /> Если одно ключевое слово появляется в строке поставщика несколько раз, приоритет имеет первое значение.|  
|IDBProperties::GetProperties|IDBProperties::GetProperties может вызываться для получения значения нового свойства инициализации источника данных SSPROP_INIT_SERVERSPN и SSPROP_INIT_FAILOVERPARTNERSPN, а новых свойств источника данных SSPROP_AUTHENTICATIONMETHOD и SSPROP_ MUTUALLYAUTHENTICATED.|  
|IdbProperties::GetPropertyInfo|IdbProperties::GetPropertyInfo будет включать новые свойства инициализации источника данных SSPROP_INIT_SERVERSPN и SSPROP_INIT_FAILOVERPARTNERSPN или новые свойства источника данных SSPROP_AUTHENTICATION_METHOD и SSPROP_MUTUALLYAUTHENTICATED.|  
|IDBProperties::SetProperties|Чтобы задать значения для нового источника данных свойства инициализации SSPROP_INITSERVERSPN и ssprop_init_failoverpartnerspn не может вызываться IDBProperties::SetProperties.<br /><br /> Эти свойства можно задать в любое время, но если источник данных уже открыт, будет возвращена следующая ошибка: DB_E_ERRORSOCCURRED, «Многошаговая операция OLE DB сформировала ошибки. Проверьте каждое значение состояния OLE DB (если возможно). Работа не была выполнена».|  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client &#40;OLE DB&#41;](sql-server-native-client-ole-db.md)  
  
  
