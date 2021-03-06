---
title: Использование заметок в пакетах | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- self-documenting packages
- adding annotations
- annotations [Integration Services]
ms.assetid: 48c8ed9a-b10d-490c-9ba7-4b77aa44e3dd
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3c4d9cc0f6d3487a1eae6118c2df64527d97160f
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58282018"
---
# <a name="use-annotations-in-packages"></a>Использование заметок в пакетах
  Конструктор служб [!INCLUDE[ssIS](../includes/ssis-md.md)] предоставляет заметки, которые можно использовать для обеспечения самодокументируемости пакетов, упрощения их понимания и поддержки. Заметки вы можете добавлять в области конструктора потока управления, потока данных и обработчика событий конструктора [!INCLUDE[ssIS](../includes/ssis-md.md)] . Заметки могут содержать разные типы текста; они полезны при добавлении меток, примечаний и других описательных сведений в пакет. Создание заметок возможно только во время проектирования. Например, они не записываются в журналы.  
  
 При нажатии клавиши ВВОД текст переносится на следующую строку. Размер поля заметки автоматически увеличивается по мере добавления дополнительных строк текста. Заметки пакета сохраняются в виде обычного текста в разделе CDATA файла пакета.  
  
 Дополнительные сведения об изменении формата файла пакета см. в разделе [Формат пакетов служб SSIS](https://msdn.microsoft.com/library/cfe0e5dc-5be3-4222-b721-fe83665edd94).  
  
 При сохранении пакета конструктор служб [!INCLUDE[ssIS](../includes/ssis-md.md)] сохраняет включенные в пакет заметки.  
  
## <a name="add-an-annotation-to-a-package"></a>Добавление заметки к пакету  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий пакет, к которому нужно добавить заметку.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  В конструкторе [!INCLUDE[ssIS](../includes/ssis-md.md)] щелкните правой кнопкой мыши в любом месте области конструктора на вкладке **Поток управления**, **Поток данных**или **Обработчик событий** , затем выберите пункт **Добавить заметку**. В области конструктора вкладки появится блок текста.  
  
4.  Добавление текста.  
  
    > [!NOTE]  
    >  Если текст не введен, то блок будет удален при первом щелчке вне блока.  
  
5.  Чтобы изменить размер или формат текста заметки, щелкните правой кнопкой мыши заметку и выберите пункт **Установить шрифт текста заметки**.  
  
6.  Чтобы добавить дополнительную строку текста, нажмите клавишу ВВОД.  
  
     Размер поля заметки автоматически увеличивается по мере добавления дополнительных строк текста.  
  
7.  Чтобы добавить заметку к группе, щелкните правой кнопкой мыши заметку и выберите пункт **Группа**.  
  
8.  Чтобы сохранить обновленный пакет, в меню **Файл** выберите команду **Сохранить все**.  
