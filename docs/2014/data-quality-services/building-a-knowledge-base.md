---
title: Построение базы знаний | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 51eff161-6ecd-4ee4-8187-1dd8ef4814bd
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 85dcae394c84a6af889dc6483e9989bc6dbe2ead
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014300"
---
# <a name="building-a-knowledge-base"></a>Построение базы знаний
  База знаний в службах [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) является репозиторием знаний о данных, помогающим понимать данные и поддерживать их целостность. База знаний состоит из доменов, каждый из которых представляет данные в поле данных. База знаний используется службами DQS для выполнения очистки данных и исключения из базы данных повторяющихся значений. Для подготовки базы знаний к очистке данных вы можете запустить на экземпляре данных компьютерный анализ и интерактивно управлять значениями в доменах. Службы DQS позволяют импортировать знания, создавать правила и связи, напрямую изменять значения данных и использовать базу данных по умолчанию.  
  
## <a name="in-this-section"></a>в этом разделе  
 Над базой знаний вы можете выполнить следующие действия:  
  
|||  
|-|-|  
|Создать новую базу знаний с нуля или на основе существующей базы знаний или файла данных DQS.|[Создание базы знаний](../../2014/data-quality-services/create-a-knowledge-base.md)|  
|Открыть существующую базу знаний для обнаружения знаний, управления доменами или добавления политики сопоставления.|[Открытие базы знаний](../../2014/data-quality-services/open-a-knowledge-base.md)|  
|Выполнять действия по управлению базой знаний, включая ее открытие, разблокировку, отмену работы, переименование, удаление и просмотр ее свойств.|[Управление базой знаний](../../2014/data-quality-services/manage-a-knowledge-base.md)|  
|Добавлять набор знаний в базу знаний с помощью обнаружения знаний; управления значениями в домене; добавления соответствующей политики; импорта набора знаний, доменов или значений; или с помощью базы знаний по умолчанию, DQS Data.|[Добавление знаний в базу знаний](../../2014/data-quality-services/adding-knowledge-to-a-knowledge-base.md)|  
|Анализировать образец данные по критериям качества данных.|[Обнаружение набора знаний](../../2014/data-quality-services/perform-knowledge-discovery.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Импорт знаний в базу знаний или экспорт из нее.|[Импорт и экспорт набора знаний](../../2014/data-quality-services/importing-and-exporting-knowledge.md)|  
|Создание отдельного домена и добавление набора знаний в этот домен.|[Управление доменом](../../2014/data-quality-services/managing-a-domain.md)|  
|Создание составного домена и добавление набора знаний в этот домен.|[Управление составным доменом](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
