---
title: Базы данных (табличное) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 16a233fb-f83b-4ca1-acb5-6186eca0a62c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 377b85c22d1c6da9f5296d6ad57a86028e022785
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60156510"
---
# <a name="database-representationtabular"></a>Представление базы данных (табличное)
  В табличном режиме база данных является контейнером для всех объектов табличной модели.  
  
## <a name="database-representation"></a>Представление базы данных  
 База данных — это место, где размещаются все объекты, образующие табличную модель. В базе данных разработчик находит такие объекты, как соединения, таблицы, роли и т. д.  
  
### <a name="database-in-amo"></a>База данных в объектах AMO  
 Если для управления табличным шаблоном базы данных табличной модели используются объекты AMO, то объект <xref:Microsoft.AnalysisServices.Database> из AMO соответствует логическому объекту базы данных в табличной модели по схеме «один к одному».  
  
> [!NOTE]  
>  Чтобы получить доступ к объекту базы данных, пользователь объектов AMO должен получить доступ к объекту сервера и установить с ним соединение.  
  
### <a name="database-in-adomdnet"></a>База данных в ADOMD.Net  
 Если ADOMD используется для просмотра табличного шаблона базы данных и отправки запросов к ней, то соединение с определенной базой данных устанавливается посредством объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 К определенной базе данных можно подключиться напрямую с помощью следующего фрагмента кода:  
  
```csharp  
using ADOMD = Microsoft.AnalysisServices.AdomdClient;  
...  
   ADOMD.AdomdConnection currrentCnx = new ADOMD.AdomdConnection("Data Source=<<server\instance>>;Catalog=<<database>>");  
   currrentCnx.Open();  
...  
  
```  
  
 Кроме того, через существующий объект соединения (если оно не закрыто) можно изменить текущую базу данных на другую, как показано в следующем фрагменте кода:  
  
```csharp  
currentCnx.ChangeDatabase("myOtherDatabase");  
  
```  
  
## <a name="database-in-amo"></a>База данных в объектах AMO  
 При использовании объектов AMO для управления объектом базы данных начните с объекта <xref:Microsoft.AnalysisServices.Server>. Затем найдите свою базу данных в коллекции баз данных или создайте новую базу данных, добавив ее в коллекцию.  
  
 В следующем фрагменте кода показано, как подключиться к серверу и создать пустую базу данных, после проверки того, база данных не существует:  
  
```  
  
AMO.Server CurrentServer = new AMO.Server();  
try  
{  
    CurrentServer.Connect(currentServerName);  
}  
catch (Exception cnxException)  
{  
    MessageBox.Show(string.Format("Error while trying to connect to server: [{0}]\nError message: {1}", currentServerName, cnxException.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    return;  
}  
newDatabaseName = DatabaseName.Text;  
if (CurrentServer.Databases.Contains(newDatabaseName))  
{  
    return;  
}  
try  
{  
    AMO.Database newDatabase = CurrentServer.Databases.Add(newDatabaseName);  
  
    CurrentServer.Update();  
}  
catch (Exception createDBxc)  
{  
    MessageBox.Show(String.Format("Database [{0}] couldn't be created.\n{1}", newDatabaseName, createDBxc.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    newDatabaseAvailable = false;  
}  
  
```  
  
 Практические лучше понять, о том, как использовать объекты AMO для создания и обработки представлений базы данных, см. в статье исходный код в образце Tabular AMO 2012; в частности, проверьте в следующий файл: Database.cs. Образец кода приведен только для иллюстрации описываемых здесь логических концепций и не должен использоваться в рабочей среде.  
  
  
