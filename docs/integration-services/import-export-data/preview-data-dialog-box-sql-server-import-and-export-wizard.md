---
title: Диалоговое окно "Просмотр данных" (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 02/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.previewdata.f1
ms.assetid: 423ac26a-ba02-4fdf-88b4-07995fe4a97e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 385ff11ddd79430f122a5390b45af77d8fba9205
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58272440"
---
# <a name="preview-data-dialog-box-sql-server-import-and-export-wizard"></a>Диалоговое окно «Просмотр данных» (мастер импорта и экспорта SQL Server)
  После указания данных, которые необходимо скопировать, можно нажать кнопку **Просмотр** , чтобы открыть диалоговое окно **Просмотр данных** . На этой странице можно просмотреть до 200 строк образца данных из источника данных. Таким образом вы убедитесь, что мастер будет копировать именно необходимые данные.
  
## <a name="screen-shot-of-the-preview-data-page"></a>Снимок экрана: страница "Просмотр данных" 
 На следующем снимке экрана показано диалоговое окно **Просмотр данных** мастера.  
 
![Страница "Просмотр данных" в мастере импорта и экспорта](../../integration-services/import-export-data/media/preview-data.png "Страница \"Просмотр данных\" в мастере импорта и экспорта")  
  
## <a name="preview-sample-data"></a>Просмотр образца данных  
 **Source**  
Отображает запрос, используемый мастером для загрузки данных из источника данных.

Если вы выбрали таблицу для копирования, в поле **Источник** отображается запрос `SELECT * FROM <table>` вместо имени таблицы. 
  
 **Сетка образца данных**  
 Отображает до 200 строк образца данных, возвращаемых запросом из источника данных.  


## <a name="thats-not-right-i-want-to-change-something"></a>Изменение параметров
После просмотра данных может потребоваться изменить параметры, выбранные на предыдущих страницах мастера. Для этого нажмите кнопку **ОК**, чтобы вернуться на страницу **Выбор исходных таблиц и представлений**, и нажмите кнопку **Назад**, чтобы вернуться к предыдущим страницам, где можно изменить выбранные параметры.

## <a name="whats-next"></a>Дальнейшие действия  
 После просмотра данных, которые требуется скопировать, и нажатия кнопки **ОК**диалоговое окно **Просмотр данных** вернет вас на страницу **Выбор исходных таблиц и представлений** или на страницу **Настройка назначения "Неструктурированный файл"** . Дополнительные сведения см. в разделах [Выбор исходных таблиц и представлений](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md) или [Настройка назначения "Неструктурированный файл"](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md).  
 
 ## <a name="see-also"></a>См. также раздел
[Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)
