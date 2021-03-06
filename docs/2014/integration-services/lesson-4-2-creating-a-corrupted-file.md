---
title: Этап 2. Создание поврежденного файла | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cd0b18dc-66c3-4d88-86ef-8e40cb660fae
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fa1bb23843447cc77276a34d5466d417f2a87a05
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58393352"
---
# <a name="step-2-creating-a-corrupted-file"></a>Этап 2. Создание поврежденного файла
  Для демонстрации настройки и обработки ошибок преобразования необходимо создать образец неструктурированного файла, который при обработке вызовет сбой в работе компонента.  
  
 В этой задаче предстоит скопировать существующий образец неструктурированного файла. Затем предстоит открыть его в приложении «Блокнот» и изменить столбец **CurrencyID** таким образом, чтобы при поиске совпадений во время преобразования произошел сбой. При обработке нового файла произойдет сбой в преобразовании «Уточняющий запрос» для CurrencyKey, что приведет к ошибке в работе всего пакета. После создания поврежденного образца файла предстоит выполнить пакет, чтобы просмотреть его поведение при сбое.  
  
### <a name="to-create-a-corrupted-sample-flat-file"></a>Создание поврежденного образца неструктурированного файла  
  
1.  В приложении «Блокнот» или другом текстовом редакторе откройте файл Currency_VEB.txt.  
  
     Образцы данных включаются в пакеты занятий по службам SSIS. Чтобы загрузить образцы данных и пакеты занятий выполните следующие действия.  
  
    1.  Перейдите к [образцам продуктов служб Integration Services](https://go.microsoft.com/fwlink/?LinkID=267527).  
  
    2.  Перейдите на вкладку **DOWNLOADS** .  
  
    3.  Щелкните файл SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
2.  Использование текстового редактора для поиска и замены, замените все вхождения `VEB` и замените их значением `BAD`.  
  
3.  Сохраните измененный файл в той же папке, что другие файлы образцов данных, `Currency_BAD.txt`.  
  
    > [!IMPORTANT]  
    >  Убедитесь, что `Currency_BAD.txt` сохраняется той же папке, что другие файлы образцов данных.  
  
4.  Закройте текстовый редактор.  
  
### <a name="to-verify-that-an-error-will-occur-during-run-time"></a>Проверка факта возникновения ошибки во время выполнения  
  
1.  В меню **Отладка** выберите команду **Начать отладку**.  
  
     При третьем проходе потока данных в преобразовании Lookup Currency Key будет предпринята попытка обработать файл Currency_BAD.txt, при этом произойдет ошибка преобразования. Ошибка преобразования вызовет отказ работы всего пакета.  
  
2.  В меню **Отладка** выберите команду **Остановить отладку**.  
  
3.  В области конструктора откройте вкладку **Результаты выполнения** .  
  
4.  Просмотрите журнал и убедитесь, что произошла следующая необработанная ошибка:  
  
     `[Lookup Currency Key[27]] Error: Row yielded no match during lookup.`  
  
    > [!NOTE]  
    >  Число 27 представляет собой идентификатор компонента. Это значение присваивается при создании потока данных, так что в пакете оно может отличаться от приведенного в учебнике.  
  
## <a name="next-steps"></a>Следующие шаги  
 [Шаг 3. Добавление перенаправления потока ошибок](lesson-4-3-adding-error-flow-redirection.md)  
  
  
